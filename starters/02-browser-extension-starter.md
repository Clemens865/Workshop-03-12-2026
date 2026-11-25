# PRD — Starter 2: Browser extension with a CLI coding agent as the engine

## What this is
A harness, not a finished product. Once it works, you have a Chrome side panel that can ask a CLI coding agent to act on your behalf and write real files on your machine — on top of that you can build anything: a research assistant, a page summarizer, a scraping/automation tool, a game that reacts to whatever tab you're on. The point of this PRD is only the wiring.

## Goal
Prove that a Chrome side panel can send a prompt (plus optionally the current page's text) to a CLI coding agent running locally, via **Chrome Native Messaging** — the same mechanism Anthropic's own Claude in Chrome extension uses.

## Architecture
```
Side panel (extension page) ──connectNative()──► native host (Node, local) ──spawn──► claude -p …
                            ◄── length-prefixed JSON over stdin/stdout ──┘
```

## Scope (build this first — the harness)
1. **Extension** (`extension/`, Manifest V3, plain JS, no build step)
   - `manifest.json`: permissions `sidePanel`, `nativeMessaging`, `activeTab`, `scripting`; `side_panel.default_path = sidepanel.html`; background service worker sets `chrome.sidePanel.setPanelBehavior({ openPanelOnActionClick: true })`.
   - Add a fixed `"key"` to the manifest so the extension ID stays stable when reloaded unpacked; print the resulting ID in the README.
   - Side panel UI: transcript, input, Send/Stop, checkbox "include this page".
   - If "include this page" is on: grab `document.title`, URL and `document.body.innerText` (truncate to 20,000 chars) from the active tab via `chrome.scripting.executeScript`, and prepend it to the prompt.
   - Open the port with `chrome.runtime.connectNative("com.yourname.cli_agent")` (pick your own reverse-DNS-style host name), send `{type:"prompt", text}`, render streamed events.
2. **Native host** (`host/`, Node 20+)
   - Implements the native messaging protocol: each message = 4-byte length (native byte order) + UTF-8 JSON, both directions. Nothing else may be written to stdout — log to a file in `host/logs/` instead.
   - On prompt: spawn `claude -p "<text>" --output-format stream-json --verbose --permission-mode acceptEdits` with `cwd` = a dedicated workspace folder (create if missing); forward each JSON line as a separate message (keep each message under 1 MB, split if needed).
   - Resume the session with `--resume <session_id>` on follow-up prompts; `{type:"stop"}` kills the process.
   - `host/run.sh` wrapper that calls Node by **absolute path** (Chrome starts hosts with a minimal PATH) and sets PATH so `claude` is found.
3. **Installer** (`host/install.sh`)
   - Writes the native messaging manifest (macOS: `~/Library/Application Support/Google/Chrome/NativeMessagingHosts/<your-host-name>.json`) with `name`, `description`, absolute `path` to `run.sh`, `type: "stdio"`, `allowed_origins: ["chrome-extension://<ID>/"]`.
   - `chmod +x` on `run.sh`; `uninstall.sh` removes the manifest.

## Out of scope for the harness
Chrome Web Store publishing, Windows/Linux installers, page manipulation beyond reading (clicking/filling forms — add that later if your product needs it).

## Acceptance criteria (the harness is done when...)
- [ ] Load unpacked extension, run `install.sh`, click the toolbar icon → side panel opens.
- [ ] On any article page: "include this page" + "summarize this page into summary.md" → the file exists in your workspace folder.
- [ ] A follow-up prompt ("add three key quotes") edits the same file — the session resumed correctly.
- [ ] Stop works; closing the side panel kills the `claude` process (check with `ps`, no orphans left).
- [ ] If the host isn't installed, the panel shows a clear error ("native host not found — run install.sh").

## Notes for the builder
- Most failures are: wrong extension ID in `allowed_origins`, a non-executable `run.sh`, `node`/`claude` not on Chrome's PATH, or a stray `console.log` writing to stdout. Check those first.
- Only the side panel / service worker may call `connectNative` — never expose it to content scripts.

## Now make it yours
With the harness passing the acceptance criteria above, tell Claude Code what the extension should actually do — "give it buttons for 5 common actions instead of free text", "make it a shopping-comparison assistant", "make it narrate a story based on what I'm browsing." The native-messaging wiring stays the same.
