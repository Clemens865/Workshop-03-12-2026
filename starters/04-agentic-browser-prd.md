# PRD — Starter 4: A browser with a terminal built in

## What this is
Unlike the other three starters, this one *is* the product: a real, usable desktop browser — tabs, address bar, back/forward, the works — with a CLI coding agent wired in as a first-class panel, not bolted on afterward. You browse normally; the agent panel can read, narrate, and act on whatever tab is active, powered by your own Claude Code or Codex session. No API key, ever.

## One-line pitch
Electron shell with real browser tabs + an agent chat panel, where the chat can see and drive the page you're looking at — navigate, read, summarize, extract — narrating its steps live instead of working silently.

## Goal
Prove that a daily-driver browser and an agent panel can share one window, with the agent able to act on real tabs, not a hidden offscreen one.

## Architecture
```
┌─────────────────────────────┬───────────────┐
│  Browser chrome (tabs, URL   │  Chat panel   │
│  bar, back/forward)          │  (agent)      │
│                               │               │
│  BrowserView per tab ─────────┤ ──IPC──► main-process
│                               │   orchestrator ──spawn──► claude -p …
└─────────────────────────────┴───────────────┘
```
- **Shell:** Electron, multiple `BrowserView` instances (one per tab) managed by the main process; a thin custom UI for the tab strip + address bar (don't just wrap `<webview>` — use `BrowserView` for real isolation and to give the agent clean access to page content).
- **Engine:** Claude Code CLI or Codex CLI, spawned as a child process per agent task, using your own authenticated session.
- **Agent's tools (what you give it, backed by the active `BrowserView`):**
  - `navigate(url)` — load a URL in the active or a new tab.
  - `read_page()` — return title, URL, and visible text (truncated sensibly).
  - `click(selector)` / `type(selector, text)` — basic page interaction.
  - `screenshot()` — capture the active tab for the agent to reference.
- **Harness (the part you actually build):**
  - Main-process orchestrator: takes a chat instruction, hands it to the CLI engine as a prompt with the tools above, streams back each step.
  - IPC bridge between the chat renderer and the orchestrator for live status ("opening search", "reading page 2", "found 3 sources").
  - A result formatter: final answers get written to a `.md` file in a local `/outputs` folder and shown as a clickable card in the chat, not just a chat bubble.

## Scope (build this first — the harness)
1. **Browser chrome**: tab strip (new tab / close tab), address bar (type a URL or search term, Enter navigates), back/forward buttons, one `BrowserView` per tab, properly resized to fill the content area.
2. **Chat panel**: docked to one side, can be shown/hidden; transcript, input, Send/Stop.
3. **Engine wire-up**: chat input spawns the CLI engine with `--output-format stream-json --verbose --permission-mode acceptEdits`, raw events streamed into the chat pane. Prove this works before wiring any browser tools.
4. **Browser tools**: give the engine `navigate`/`read_page` first (read-only is enough to prove the concept), then `click`/`type` if time allows.
5. **Output**: final answer saved as a Markdown file in `/outputs`, with a "view result" card in the chat.

## Out of scope
- Authenticated browsing / login flows for the agent — this hits the Google embedded-webview OAuth block (`Error 403: disallowed_useragent`, see `workshop-core.md`). Name it as a known wall rather than solving it here; the fix (system-browser handoff + loopback redirect, RFC 8252) is a separate, bigger piece of work.
- Multi-user, packaging/distribution, auto-update, syncing bookmarks/history.
- Persistent memory across sessions (stretch goal only).
- A full extension system, ad blocking, or any other "real browser" feature beyond tabs/address bar/navigation.

## Acceptance criteria
- [ ] You can open multiple tabs and navigate normally, like a real (if minimal) browser.
- [ ] With a tab open on some page, asking the chat "summarize this page" returns a summary grounded in that tab's actual content (not a generic answer).
- [ ] Asking "go to X, research Y, summarize Z" drives navigation in a tab (new or existing) and narrates each step in the chat as it happens.
- [ ] The final answer is saved as a file in `/outputs` and shown as a card in the chat, not just text.
- [ ] No API key anywhere in the code — only your existing CLI session.
- [ ] The known Google-login wall is named out loud if you hit it, rather than silently failing.

## Notes for the builder
- Build the plain browser chrome *first*, with zero agent logic, and confirm tabs/navigation feel normal before wiring in the engine — it's much easier to debug one layer at a time.
- `BrowserView` bounds have to be manually kept in sync with window resizes; don't skip this or the page will render under your UI chrome.
- This is deliberately the same architecture as a research-assistant browser — if you'd rather build *that* narrower version first (agent drives a hidden/secondary browser instead of your main tabs), that's a smaller, faster path to the same core proof.

## Now make it yours
Once tabs + agent-panel + one working tool (`navigate` or `read_page`) are proven, decide what kind of browser this really is — a research co-pilot, a shopping-comparison browser, a reading/summarizing browser, a browser that narrates a story about whatever you look at. The harness (real tabs + an agent that can see and act on them) stays the same.
