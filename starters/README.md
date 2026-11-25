# Starter PRDs — "The Terminal Is the Engine"

Four ready-to-build project briefs. Each one is a complete PRD you can hand straight to Claude Code to get a working harness in minutes — no API key, ever. The engine is always your own Claude Code (or Codex) CLI session, already paid for by your subscription.

**Three of these are shells, not products.** They each give you a different wrapper — a web app, a browser extension, a mobile app — around the same core idea: a UI sends a prompt, a CLI coding agent does the work, files/results land back in the UI. What you actually *build* inside that shell is up to you: a browser, a game, a productivity tool, a "lovable"-style app generator, a personal dashboard, anything. The harness doesn't change — only what you ask the engine to do once it's wired up.

The fourth is a specific product PRD: a real, usable browser with a terminal/agent panel built in.

| # | File | Shell | What it proves |
|---|---|---|---|
| 1 | [`01-web-app-starter.md`](./01-web-app-starter.md) | Browser tab + local backend | Any web UI can drive a CLI agent on a machine you own |
| 2 | [`02-browser-extension-starter.md`](./02-browser-extension-starter.md) | Chrome side panel | A browser extension can drive the same CLI agent via Native Messaging |
| 3 | [`03-mobile-app-starter.md`](./03-mobile-app-starter.md) | Phone app (Expo) | A phone can be a remote for a CLI agent running on a computer |
| 4 | [`04-agentic-browser-prd.md`](./04-agentic-browser-prd.md) | A real browser | A full browsing app with the terminal built in as a first-class panel, not bolted on |

## How to use one of these

1. Pick the shell that matches what you want to build (or start with #1 — it's the simplest).
2. Create a new, empty folder for your project.
3. Save the file into it (e.g. as `PRD.md`).
4. Open a terminal in that folder and run `claude`.
5. Paste: *"Read PRD.md and build this, step by step. Ask me before anything destructive. Once the harness works end-to-end, I'll tell you what the actual app should do."*
6. Let it build the harness first (that's the acceptance criteria in the PRD). Then tell it what you actually want — the next 90 minutes are yours.

No API key, no cloud account, no sign-up. Just your existing Claude Code (or Codex) login.
