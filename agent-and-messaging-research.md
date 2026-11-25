# Agent Protocols, LLM Infrastructure & Messaging Platforms

Curated from the Communicy (Kolvi) product research — ~32 deep-dive reports written while researching an EU-sovereign, agent-native, E2EE team chat product (Oct–Nov 2026). The reports themselves are internal product strategy; these are the external reference links worth keeping.

## Agent-to-agent & agent-to-tool protocols

| Topic | Link | Notes |
|---|---|---|
| Model Context Protocol (MCP) spec + changelog | https://modelcontextprotocol.io/specification/2026-07-28/changelog | Current spec version as of late 2026 |
| MCP authorization (OAuth 2.1) | https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization | |
| MCP security best practices | https://modelcontextprotocol.io/specification/2026-07-28/basic/security_best_practices | |
| MCP Apps extension (interactive UIs) | https://github.com/modelcontextprotocol/ext-apps | |
| MCP Tasks extension | https://modelcontextprotocol.io/extensions/tasks/overview | Long-running/async tool calls |
| A2A (Agent2Agent) specification | https://a2a-protocol.org/latest/specification/ | Agent-to-agent protocol, now Linux Foundation |
| Agentic AI Foundation (AAIF) launch | https://workos.com/blog/the-linux-foundation-launches-the-aaif | Umbrella foundation for MCP/A2A/AGNTCY |
| AGNTCY ("internet of agents") | https://www.splunk.com/en_us/blog/artificial-intelligence/agntcy-structure-the-internet-of-agents.html | Cisco/Linux Foundation agent interoperability project |
| OWASP MCP Top 10 / tool poisoning | https://www.speakeasy.com/resources/mcp-tool-poisoning | Security risks specific to MCP tool definitions |
| IETF: OAuth for AI agents acting on behalf of a user | https://datatracker.ietf.org/doc/html/draft-oauth-ai-agents-on-behalf-of-user-02 | Draft standard |
| Anthropic — Building effective agents | https://www.anthropic.com/research/building-effective-agents | Widely-cited agent design patterns reference |
| Anthropic Agent Skills (open standard) | https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/ | |

## Platform-native agent/MCP integrations

| Platform | Link | Notes |
|---|---|---|
| Slack MCP server docs | https://docs.slack.dev/ai/mcp-server/ | GA'd Feb 2026 |
| Slack real-time Search API | https://docs.slack.dev/apis/web-api/real-time-search-api | |
| Linear MCP + agents | https://linear.app/docs/mcp · https://linear.app/developers/agents | Often cited as a clean agent-as-member model |
| Notion MCP tools | https://developers.notion.com/docs/mcp-supported-tools | |
| GitHub MCP server | https://github.com/github/github-mcp-server | |
| Stripe MCP | https://docs.stripe.com/mcp | |
| Microsoft Agent 365 / Entra Agent ID | https://learn.microsoft.com/he-il/microsoft-agent-365/tooling-servers-overview | Agent identity/governance layer |
| Google Workspace Chat MCP server | https://developers.google.com/workspace/chat/api/guides/configure-mcp-server | |
| Mistral Le Chat MCP connectors | https://docs.mistral.ai/le-chat/knowledge-integrations/connectors/mcp-connectors | |

## Chat-platform developer APIs (for anyone building bots/integrations)

| Platform | Link |
|---|---|
| Slack Web API rate limits | https://docs.slack.dev/apis/web-api/rate-limits |
| Discord developer docs (reference) | https://docs.discord.com/developers/reference |
| Discord gateway (realtime events) | https://docs.discord.com/developers/events/gateway |
| Telegram Bot API | https://core.telegram.org/bots/api |
| Matrix specification | https://spec.matrix.org/latest/ |
| Microsoft Teams SDK overview | https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/tool-sdk-overview |
| Zulip real-time events API | https://zulip.com/api/real-time-events |
| Mattermost incoming webhooks | https://developers.mattermost.com/integrate/webhooks/incoming/ |
| WhatsApp Cloud API overview | https://developers.facebook.com/docs/whatsapp/cloud-api/overview |

## Matrix protocol & sovereign/E2EE messaging infra

| Topic | Link |
|---|---|
| Tuwunel (Apache-licensed Matrix server, Rust) | https://github.com/matrix-construct/tuwunel |
| Synapse (reference Matrix server, now AGPL) | https://github.com/element-hq/synapse |
| Element — why Synapse moved to AGPL | https://element.io/blog/sustainable-licensing-at-element-with-agpl |
| Matrix v1.16 release (room v12) | https://matrix.org/blog/2025/09/17/matrix-v1.16-release/ |
| Are We MLS Yet (Matrix ↔ MLS encryption tracker) | https://arewemlsyet.com/ |
| OpenMLS (Rust MLS implementation) | https://blog.openmls.tech/ |
| MIMI protocol draft (IETF, interoperable messaging) | https://datatracker.ietf.org/doc/html/draft-ietf-mimi-protocol-06 |
| openDesk (German government Matrix-based workplace suite) | https://en.wikipedia.org/wiki/OpenDesk |
| WhatsApp "Private Processing" (confidential-compute AI over E2EE chat) | https://engineering.fb.com/2025/04/29/security/building-private-processing-for-ai-tools-on-whatsapp/ |

## LLM gateways, EU data residency & sovereign inference

| Topic | Link |
|---|---|
| Anthropic data residency docs | https://platform.claude.com/docs/en/manage-claude/data-residency |
| OpenAI — data residency in Europe | https://openai.com/index/introducing-data-residency-in-europe/ |
| Google Vertex AI data residency | https://cloud.google.com/vertex-ai/generative-ai/docs/learn/data-residency |
| Envoy AI Gateway v1.0 (OSS LLM gateway) | https://github.com/envoyproxy/ai-gateway/releases/tag/v1.0.0 |
| OpenRouter — sovereign AI / in-region routing | https://openrouter.ai/docs/guides/features/sovereign-ai |
| LiteLLM enterprise docs | https://docs.litellm.ai/docs/enterprise |
| Mistral Compute (EU sovereign inference) | https://mistral.ai/products/compute |
| MCP Sampling (client-mediated model calls) | https://modelcontextprotocol.io/specification/2025-11-25/client/sampling |

## Automation & agent-builder platforms

| Platform | Link |
|---|---|
| OpenAI AgentKit launch | https://techcrunch.com/2025/10/06/openai-launches-agentkit-to-help-developers-build-and-ship-ai-agents |
| n8n — human-in-the-loop for AI tools | https://docs.n8n.io/advanced-ai/human-in-the-loop-tools |
| Temporal + OpenAI Agents SDK integration | https://temporal.io/blog/announcing-openai-agents-sdk-integration |
| Vercel Workflow (durable execution) | https://vercel.com/workflow |
| τ-bench — agent reliability benchmark (paper) | https://arxiv.org/abs/2406.12045 |
| TheAgentCompany — agent benchmark (paper) | https://arxiv.org/abs/2412.14161 |
| METR — AI agent time-horizon tracking | https://theaidigest.org/time-horizons |

## EU regulation relevant to AI/agent products

| Topic | Link |
|---|---|
| EU AI Act — Art. 50 Code of Practice (AI-generated content labelling) | https://digital-strategy.ec.europa.eu/en/policies/code-practice-ai-generated-content |
| EU AI Act — GPAI provider guidelines | https://digital-strategy.ec.europa.eu/en/policies/guidelines-gpai-providers |
| DORA — Regulation (EU) 2022/2554 | https://eur-lex.europa.eu/eli/reg/2022/2554/oj |
| NIS2 — Directive (EU) 2022/2555 | https://eur-lex.europa.eu/eli/dir/2022/2555/oj |

## Consumer messengers & EU sovereign-messaging attempts

| Topic | Link |
|---|---|
| Discord — E2EE for all voice/video calls | https://discord.com/blog/every-voice-and-video-call-on-discord-is-now-end-to-end-encrypted |
| Telegram Bot API changelog | https://core.telegram.org/bots/api-changelog |
| BEAM — Belgium's Matrix-based government messenger | https://resiliencemedia.co/a-beam-of-light-for-eu-sovereignty-as-belgium-rolls-out-matrix-based-messaging-app-for-government/ |
| Threema (Swiss E2EE messenger) | https://threema.com/about |

*Source: `Software-Projects/Communicy/research/` reports 04, 08, 09, 10, 12, 13, 21, 23 (each report's own "Sources" section has the full citation list).*
