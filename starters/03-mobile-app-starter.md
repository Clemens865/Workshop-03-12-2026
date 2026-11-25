# PRD — Starter 3: Phone app as a remote for a CLI coding agent

## What this is
A harness, not a finished product. Once it works, you have a phone that can trigger real work on a computer you own — a notes app, a remote game master, a dictation-to-document tool, anything. The CLI agent never runs on the phone; files always land on the computer.

## Prerequisite
Starter 1's backend running (`01-web-app-starter.md`), on your laptop or a small VM. This PRD builds the phone side on top of it.

## Two paths
- **Path B — built-in (10 minutes, no code):** Anthropic's Remote Control, built into Claude Code itself. Do this first as a baseline before building your own.
- **Path A — your own app:** an Expo (React Native) app that talks to the Starter 1 backend directly, so you control the UI completely.

## Path B — Remote Control (verify only)
1. On your computer: `claude --version` (needs ≥ 2.1.51), then in a project folder run `claude --remote-control` (or type `/remote-control` inside a running session). Check `claude --help` if the syntax has changed.
2. On your phone: Claude app → Code tab → pick the session (or scan the QR code shown in the terminal).
3. Ask it to create `phone-test.md` → the file appears on your computer.
4. Note what works and what doesn't (e.g. terminal-only slash commands) — this tells you what your own app in Path A needs to cover.

## Path A — Your own app (build this)
1. **Network access from phone to backend** — pick one and document it in the README:
   - **Tailscale** on both devices, backend exposed with `tailscale serve` (gives HTTPS, works off-Wi-Fi). *Preferred.*
   - Or the Starter 1 backend deployed behind Caddy on a small VM (HTTPS already).
   - Do **not** bind the backend to `0.0.0.0` on an open network.
2. **App** (`mobile/`, Expo SDK latest, TypeScript, runs in **Expo Go** — no Apple/Google developer account needed yet)
   - Settings screen: backend URL + auth token, stored with `expo-secure-store`.
   - Chat screen: transcript, input, Send/Stop; same WebSocket protocol as Starter 1 (`auth` → `prompt` / `stop`, streamed JSON events).
   - Files screen: list from `GET /files`, pull-to-refresh.
   - One native touch to prove it's more than a website: a share-sheet target, or "attach photo" (`expo-image-picker`) that uploads an image to the backend workspace and references it in the prompt. Add a `POST /upload` endpoint to the Starter 1 backend for this (10 MB size limit, auth required).
3. **README** with: start backend → start Tailscale serve → `npx expo start` → scan the QR code with Expo Go (iOS camera / Android Expo Go app).

## Out of scope for the harness
App Store / Play Store builds, push notifications, offline mode, running anything on-device.

## Acceptance criteria (the harness is done when...)
- [ ] Path B: a file created from the phone appears on the computer.
- [ ] Path A: from the phone over mobile data (Wi-Fi off), "create todo.md with 3 items" → the file appears on the backend host and in the Files screen.
- [ ] A follow-up prompt edits the same file — the session resumed correctly.
- [ ] Photo attach: "describe this photo into photo.md" works.
- [ ] A wrong token produces a clear error, no connection.

## Notes for the builder
- iOS blocks plain `http://` by default — that's why HTTPS via Tailscale/Caddy is required, not optional.
- Store-readiness later: Apple rejects thin web wrappers (guideline 4.2), so keep at least one native feature if you ever want to ship it; Apple Developer Program is $99/yr, Google Play is $25 one-time.

## Now make it yours
With the harness passing the acceptance criteria above, tell Claude Code what the phone app should actually be for — "make it a voice-memo-to-task app", "make it a trip planner I talk to on the go", "make it control the browser extension from Starter 2 remotely." The remote-control wiring stays the same.
