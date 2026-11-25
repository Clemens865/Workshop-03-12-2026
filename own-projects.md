# Apps Built This Way: Clemens's Own Repos

Public repos most relevant to the "terminal is the engine" pattern (CLI coding agent as the engine, no per-call API cost) and AI-agent/desktop tooling generally. Snapshot source: `Private-Development/github-projects-inventory-2026-09-16.md` (GitHub API, 2026-09-16) — check current star/release counts before presenting live, this is a point-in-time snapshot.

## Public repos

| Repo | Language | Stars | What it is |
|---|---|---|---|
| [Claude-Pulse](https://github.com/Clemens865/Claude-Pulse) | TypeScript | 40 | One command. Global memory for Claude Code. |
| [Console-Buddy](https://github.com/Clemens865/Console-Buddy) | TypeScript | 34 | Chrome DevTools extension, 22+ analysis tools with AI-powered insights (security, performance, accessibility, SEO). |
| [Lazy-Fetch](https://github.com/Clemens865/Lazy-Fetch) | TypeScript | 12 | A CLI companion for Claude Code that solves context, persistence, and process tracking. |
| [WebhookBuddy](https://github.com/Clemens865/WebhookBuddy) | TypeScript | 11 | Chrome extension connecting your browser to automation platforms. |
| [My-Claude-Skills](https://github.com/Clemens865/My-Claude-Skills) | — | 6 | A collection of Agent Skills and Claude Code commands for design, development, and AI workflows. |
| [Phago_Project](https://github.com/Clemens865/Phago_Project) | Rust | 5 | Rust framework mapping cellular biology to computation — agents self-organize, build a Hebbian knowledge graph, exhibit emergent collective behavior without top-down control. |
| [chrome-buddy](https://github.com/Clemens865/chrome-buddy) | TypeScript | 4 | Universal agentic + LLM Chrome extension — model-transparent, BYO-key, does multi-step browser work. |
| [DeepBrain_OS](https://github.com/Clemens865/DeepBrain_OS) | Rust | 3 | Cognitive macOS desktop app: personal memory layer, semantic search, file indexing, self-learning, all local. |
| [ruVector-OS](https://github.com/Clemens865/ruVector-OS) | TypeScript | 2 | System-level intelligence layer for macOS — local semantic search giving AI agents access to your whole filesystem. |
| [Code-Pulse](https://github.com/Clemens865/Code-Pulse) | TypeScript | 1 | Self-hosted middleware turning a team's Claude Code sessions into shared, queryable knowledge fed back into every member's next session. |
| [knowledgeOS](https://github.com/Clemens865/knowledgeOS) | TypeScript | 1 | AI-powered knowledge management system — conversation, document analysis, glass-morphism UI. |
| [mic-labs-local](https://github.com/Clemens865/mic-labs-local) | TypeScript | 1 | Native macOS desktop app wrapping 215+ specialized AI micro apps. |
| [Company-Runner](https://github.com/Clemens865/Company-Runner) | Shell | 1 | AI-powered business operating playbook — zero cost, zero infrastructure, built entirely as Claude Code skill files reading/writing a shared `business-brain/` folder. |
| [micro-labs-chrome](https://github.com/Clemens865/micro-labs-chrome) | TypeScript | 1 | AI-powered productivity suite, 100 micro-apps, Chrome + Google Gemini. |
| [superbrain-app](https://github.com/Clemens865/superbrain-app) | Rust | 0 | macOS menu bar app: semantic memory, file search, reinforcement learning, workflow automation. Built with **Tauri 2** + React + Rust — direct Tauri reference example. |
| [Claude-Experimental](https://github.com/Clemens865/Claude-Experimental) | Rust | 0 | Agentic Coding Engine — built in Rust, powered by Claude. |
| [BattleChallenge](https://github.com/Clemens865/BattleChallenge) | Python | 0 | Open-source benchmarking system comparing agentic AI frameworks head-to-head on standardized tasks. |
| [RUSTY-AI](https://github.com/Clemens865/RUSTY-AI) | Rust | 0 | Extensible AI assistant, Rust backend + React frontend, voice interaction, plugin architecture. |
| [context-capsules](https://github.com/Clemens865/context-capsules) | TypeScript | 0 | "Docker for AI Expertise" — package, version, and deploy AI knowledge across platforms. |
| [devdigger](https://github.com/Clemens865/devdigger) | TypeScript | 0 | Enterprise-grade local knowledge management: RAG search, neural reranking, system-wide document indexing. |
| [Rusty_Claw](https://github.com/Clemens865/Rusty_Claw) | Rust | 0 | The full OpenClaw experience in a single Rust binary. |
| [Personal-AI-Assistant](https://github.com/Clemens865/Personal-AI-Assistant) | TypeScript | 0 | AI-powered personal assistant for VS Code with Obsidian-inspired knowledge management. |

*(Trimmed from the full 46-public-repo inventory — skipped one-offs, art/game projects, and repos with too little description to place in this pattern.)*

## Private flagship apps (named, not linked)

These are the "show, don't tell" examples from the talk itself — built on the same pattern (Electron/Tauri shell + Claude Code/Codex engine, no per-call API cost) but kept private:

- **Atelier** — Electron marketing-asset generator: social posts, carousels, whitepapers, presentations with PowerPoint export, brand kits, canvas/SVG editing, voice input, web research. User picks Claude Code *or* Codex as the engine. No paid AI call.
- **Workspace-OS** — "the only workspace you will ever need": real Word/Excel/PPT via embedded LibreOffice, native mail/calendar, full browser, notes with a knowledge graph, in-folder AI agents. The North Star example. ("The AI runs on your existing Claude Code subscription. No API key, no cloud dependency, no telemetry.")
- **TerminalOS** — personal AI desktop workspace that turns conversation into lasting, reopenable work (apps, documents, workflows). Standout mechanism: *mirrored-instance self-improvement* — a "live" instance and an isolated "candidate" instance where changes are built/tested before being promoted or discarded.
- **Designspace OS** — Tauri/Rust, local-first product-development tool (idea → CAD via FreeCAD/KiCad/Blender → manufacturing handoff), conversational agent "Astra," engine is Codex. Working macOS alpha.
- **Notebook_LLM** — the original Feb-last-year experiment: a Notion-style Electron app (callout blocks, toggle sections, slash commands), now v1.4.1 DMG release. The project that first proved the "reverse-engineered Cursor-like IDE" idea, before the pivot to terminal-as-engine.

*Bonus, worth a mention if it comes up live:* **Rabbit-Browser** (private) — "an agentic browser with AI-powered assistance, visual context awareness, and natural voice conversations" — an earlier personal experiment that previews exactly what Part 5's hands-on build (agentic browser) asks attendees to build from scratch.
