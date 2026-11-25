# PRD — Starter 1: Web app with a CLI coding agent as the engine

## What this is
A harness, not a finished product. Once it works, the browser tab you just built can become anything — a research tool, a game, a notes app, a "describe it and get an app" generator. The point of this PRD is only the wiring: **UI → your own Claude Code (or Codex) session → files on your machine, no API key.**

## Goal
Prove that a plain web page can drive a CLI coding agent running on a computer you own, and stream its work back live.

## Architecture
```
Browser tab ──WebSocket──► Node backend ──spawn──► claude -p … (cwd = ./workspace)
           ◄── streamed JSON events ──┘
```

## Scope (build this first — the harness)
1. **Backend** (`server/`, Node 20+, TypeScript, `ws` + `express`, nothing heavier)
   - Serves the static frontend and one WebSocket endpoint `/ws`.
   - On `{type:"prompt", text}`: spawn
     `claude -p "<text>" --output-format stream-json --verbose --permission-mode acceptEdits`
     with `cwd` = `WORKSPACE_DIR` (default `./workspace`, create if missing). Use `spawn` with an args array, never a shell string.
   - Parse stdout line by line (each line is one JSON event) and forward each event to the client.
   - Capture `session_id` from the first event; the next prompt in the same tab adds `--resume <session_id>` so the conversation continues.
   - `{type:"stop"}` kills the running child process.
   - `GET /files` lists files in `WORKSPACE_DIR` (name, size, mtime), not recursive beyond 2 levels.
2. **Frontend** (`web/`, one `index.html` + one JS file, no build step)
   - Chat transcript, input box, Send / Stop buttons.
   - Renders assistant text, tool calls (name + short input summary) and the final result with cost/duration if present.
   - A "Files" panel that refreshes `/files` after each finished run.
3. **Safety (required, even for a quick build)**
   - Binds to `127.0.0.1` by default. `HOST` env var to change it.
   - Every WebSocket connection must send an `AUTH_TOKEN` (env var) as its first message, else the connection closes.
   - One running `claude` process per connection; reject new prompts while busy.

## Out of scope for the harness
Multi-user accounts, databases, a frontend framework, Docker, persisting chat history across restarts, deployment to a VM (that's a stretch goal — ask for it by name if you want it, with Caddy for HTTPS and a `systemd` unit).

## Acceptance criteria (the harness is done when...)
- [ ] "Create hello.md with a haiku about terminals" → the file appears in `./workspace` and in the Files panel.
- [ ] A follow-up prompt ("make it rhyme") edits the same file — the session resumed correctly.
- [ ] The Stop button kills a long-running task within 2 seconds.
- [ ] A connection without the token is rejected.

## Notes for the builder
- Check flags with `claude --help` first; if `stream-json` output differs from what's described here, adapt the parser rather than guessing.
- This harness assumes one user (you). Don't add sign-up or multi-tenant features unless that becomes the actual product.

## Now make it yours
With the harness passing the acceptance criteria above, tell Claude Code what you actually want this to be — "turn this into a browser with tabs", "turn this into a game where the agent is the dungeon master", "turn this into a tool that builds a small app from one sentence." The wiring underneath stays the same; only the UI and the prompts you send change.
