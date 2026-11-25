# Agentic Engineering, Dev Tools & Misc

A grab-bag of genuinely interesting resources from smaller research/notes files across the last few months.

## Agentic engineering — evals, observability & multi-agent workflows

From `Scraping-Knowledge/tips.md` — a curated set of tips pulled from conference/YouTube talks on building and evaluating production AI agents. The source videos are themselves a great watch-list:

| Talk | Link |
|---|---|
| $31K & 1,000 hours on Claude Code (Saraev) | https://youtu.be/45K3zHckCnQ |
| Super Simple Software Factory | https://youtu.be/haUfb1ievTE |
| 10 Levels of Jev | https://youtu.be/_U-O5lYhJ7Q |
| Agentic Engineering Benchmarks | https://youtu.be/9weiIHy9T_0 |
| Pi Durable Proactive Agents | https://youtu.be/DNDYYHsypZg |
| Hermes Agent Architecture Explained | https://youtu.be/n32qq7Kwzh0 |
| Uber — closed-loop multimodal evals | https://youtu.be/31GUkCBD-Uc |
| From Vibes to Production (Arize) | https://youtu.be/qZj7sqmidqA |
| Agentic Evals Workshop (Hugging Face) | https://youtu.be/UxMZfbWI3LY |

**Strongest cross-talk takeaways** (where multiple independent sources agreed): never trust a single run, measure pass-rate over many; use deterministic code checks before an LLM judge; log everything end-to-end before optimizing; combine cheap + frontier models rather than picking one; keep context lean (compact early, send only failures); let the agent say "I don't know"; expect and guard against reward hacking (agents editing tests to pass).

## Procedural 3D characters (Three.js) — research for code-only character animation

From `ThreeJS_Characters/RESEARCH.md` (Oct 2026 survey, no-asset/procedural crowd-rendering approach):

| Project | Link | Why it matters |
|---|---|---|
| INKWAVE (MIT) | https://github.com/jaydendavisnc/inkwave | Fully procedural characters: geometry, materials, 60-bone rig, spring-based pose system |
| sakura-atelier | https://github.com/claudetee/sakura-atelier | Procedural anime character creator, canvas-painted face |
| three-anime-style | https://github.com/xymeow/three-anime-style | Ink/cel-shading pass + stepped pose animation, same stack (r186 + WebGLRenderer) |
| meshoptimizer | https://github.com/zeux/meshoptimizer | Mesh simplification/remeshing, seamless single-mesh bodies |
| three-mesh-bvh | https://github.com/gkjohnson/three-mesh-bvh | Fast picking / closest-point / SDF queries in Three.js |
| three-vrm (springbone) | https://github.com/pixiv/three-vrm | VRM avatar spec implementation incl. physics-based spring bones |
| HeadAudio / TalkingHead | https://github.com/met4citizen/HeadAudio · https://github.com/met4citizen/TalkingHead | Audio-to-viseme lip-sync for web avatars |

## ML / vector-search research papers

From `ASI/RuVector/README.md` (a Rust vector-database project):

| Paper | Link | Relevance |
|---|---|---|
| LoRA: Low-Rank Adaptation of LLMs | https://arxiv.org/abs/2106.09685 | Fine-tuning embeddings efficiently |
| REFRAG — Compress-Sense-Expand architecture | https://arxiv.org/abs/2509.01092 | ~30x RAG latency reduction via pre-computed representation tensors |
| Subpolynomial fully-dynamic min-cut | https://arxiv.org/abs/2512.13105 | Graph-algorithm backing for `ruvector-mincut` |

## Small web-dev toolkit (from a creative-coding side project, `xyz/`)

| Tool | Link |
|---|---|
| View Transitions API (MDN) | https://developer.mozilla.org/docs/Web/API/View_Transitions_API |
| fflate (fast in-browser compression) | https://github.com/101arrowz/fflate |
| canvas-ui | https://github.com/DavidHDev/canvas-ui |
| culori (color manipulation) | https://github.com/Evercoder/culori |
| Fontsource (self-hosted Google Fonts) | https://fontsource.org |

## Deliberately skipped (low external-resource value)

- `Mobile_developments/app-discovery/CONCEPTS.md` and `game-discovery/CONCEPTS.md` — internal app/game idea brainstorms, almost no external links.
- `Worklive/PROGRESS.md` — mostly localhost dev-session notes; the two Unreal Engine doc links are niche to that one side project.
- `Workspace-OS/docs/BUGS.md`, `OUTLOOK-OAUTH-SETUP.md`, `HYPERFRAMES-ANIMATION.md`, `phago-wt-int/docs/INTEGRATION_GUIDE.md` — internal project docs/bug logs, no notable external references.
- `Decision_Model_Idea_USe cases/reports/real-timeline.md` — an interesting internal AI-eval study (can an LLM reorder shuffled incident timelines?) but its links are just raw GitHub-issue/postmortem source data, not curated resources.
