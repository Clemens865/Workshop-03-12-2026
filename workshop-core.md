# The Terminal Is the Engine — Core Sources

Reference links backing the workshop talk ("Electron/Tauri as the shell, a CLI coding agent as the engine — no per-call API cost"). Compiled from `terminal-is-the-engine/master.md` and `build-prd.md`.

## Protocols: ACP · MCP · A2A

| Topic | Link | Takeaway |
|---|---|---|
| Agent Client Protocol (ACP) | [agentclientprotocol.com](https://agentclientprotocol.com/) | Zed's standard (Aug 2025) for the app↔agent harness: JSON-RPC `session/prompt` calls with structured permissions/diffs, replacing hand-parsed stdout. Native in Gemini CLI; Claude Code and Codex via adapters; also goose and JetBrains. |
| goose's ACP provider docs | [goose-docs.ai/docs/guides/acp-providers](https://goose-docs.ai/docs/guides/acp-providers) | Confirms the economics explicitly: runs on an existing Claude Code / ChatGPT / Gemini subscription, no per-token cost. |
| Protocol disambiguation | — | One-liner for Q&A: **MCP** = agent↔tools, **ACP** = app↔agent, **A2A** = agent↔agent. |

## Legal & monetization — the reselling line

| Topic | Link | Takeaway |
|---|---|---|
| Anthropic legal & compliance docs | [code.claude.com/docs/en/legal-and-compliance](https://code.claude.com/docs/en/legal-and-compliance) | Anthropic (Thariq, Feb 2026) wants to *encourage* local `claude -p` / Agent SDK use. Banned: routing **other people's** subscription logins through a third-party product. Each attendee authenticating their own CLI directly (this workshop's model) is on the permitted side. Enforced technically (harness-spoofing blocks) since Jan 2026. Open question: whether the Agent SDK itself can bill against a subscription — unsettled as of writing. |
| OpenAI Codex reselling question | [github.com/openai/codex discussion #8338](https://github.com/openai/codex/discussions/8338) | Apache-licensed, but whether reselling an app on a user's own ChatGPT login is allowed is unanswered in OpenAI's terms. |

## OAuth & embedded-webview limitations (e.g. Google login)

| Topic | Link | Takeaway |
|---|---|---|
| Google Developers Blog | [developers.googleblog.com — embedded webview OAuth changes](https://developers.googleblog.com/upcoming-security-changes-to-googles-oauth-20-authorization-endpoint-in-embedded-webviews/) | Since 2021, Google blocks the OAuth 2.0 authorization endpoint for embedded webviews (Electron `BrowserWindow`, unregistered custom Chromium) — `Error 403: disallowed_useragent`. Tightened again Feb 2023. Anti-phishing rationale: an embedded webview could inject JS and read the password field/session cookie. |
| Auth0 blog | [auth0.com/blog/google-blocks-oauth-requests-from-embedded-browsers](https://auth0.com/blog/google-blocks-oauth-requests-from-embedded-browsers/) | Same story, practitioner angle. Detection isn't just UA string — Google also fingerprints the JS environment, so UA spoofing is a losing arms race. |
| Pake issue #1148 | [github.com/tw93/pake/issues/1148](https://github.com/tw93/pake/issues/1148) | Real-world report of the same wall hit by another Electron-wrapper project. |
| The actual fix | — | Open the system default browser for the auth step (`shell.openExternal` in Electron, equivalent in Tauri), run a local loopback server or custom protocol handler to catch the redirect (OAuth 2.0 native-app loopback flow, RFC 8252), then hand the token back to the app. |

## Electron vs. Tauri

| Topic | Link | Takeaway |
|---|---|---|
| Tauri v2 — Window Menu docs | [v2.tauri.app/learn/window-menu](https://v2.tauri.app/learn/window-menu/) | Tauri v2 added real native application menus (window- or tray-attached) — the old "no menu bar" criticism is outdated. Remaining gap: a true macOS menubar-utility app (icon-only, no dock window) still needs manual tray-icon + frameless-window assembly. |
| "Building a Menubar App with Tauri v2" | [dev.to/hiyoyok/building-a-menubar-app-with-tauri-v2-what-nobody-tells-you-2nae](https://dev.to/hiyoyok/building-a-menubar-app-with-tauri-v2-what-nobody-tells-you-2nae) | Practical walkthrough of that remaining gap. |
| Tauri vs Electron in 2026 | [techkis.tech/insights/tauri-vs-electron-binary-ram-autoupdate](https://techkis.tech/insights/tauri-vs-electron-binary-ram-autoupdate) | Footprint/speed numbers: Tauri ~8MB installer / ~45MB idle RAM / sub-second cold start vs. Electron's 100MB+ installer / 200MB+ idle RAM / slower launch. Electron's edge: deeper OS integration (dock badges, file associations, drag-and-drop, deep links), more mature ecosystem, more prior art. |

## Workshop's own build artifacts

- `terminal-is-the-engine/master.md` — full talk structure (origin story → architecture trade-offs → Electron vs Tauri → product show-and-tell → hands-on build).
- `terminal-is-the-engine/build-prd.md` — PRD for the live-coding build: a small Electron app with a chat panel driving a real embedded browser (`BrowserView`), powered by the attendee's own Claude Code/Codex CLI session, zero API key. Explicitly calls out the Google-login/embedded-webview wall as a known limitation to name live rather than solve in the room.
