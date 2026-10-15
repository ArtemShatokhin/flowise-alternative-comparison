# Flowise alternatives, compared: Kortix is open source

Kortix is open source. This repository is a source-cited comparison of the open source options for a team leaving an archived Flowise, plus a stepwise path off it. Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers.

It is written for developers who ran Flowise and need a replacement whose configuration they control. Every competitor row cites the project's own repository or site, and the Kortix facts come from [Kortix docs](https://kortix.com/docs) and [Kortix on GitHub](https://github.com/kortix-ai/suna).

## What Flowise was

Flowise was an open source tool for building AI agents and LLM workflows through a visual builder. It shipped three builders: Assistant for beginners, Chatflow for single-agent systems and chatbots, and Agentflow for multi-agent and orchestration work. Developers ran it from npm or a Docker Compose stack, and used it to assemble chatbots, retrieval over their own documents, and agent flows without writing the orchestration by hand.

The Flowise repository is archived on GitHub (checked 15 October 2026). Its README opens with "Flowise has been archived" and points to a "Future of Flowise" discussion. The project site states "We're sunsetting Flowise." The repository shows about 55,500 stars, and the last push was on 13 August 2026.

Running Flowise today means running it frozen. Flows keep executing, and no upstream fixes, model updates, or features arrive. If it is load-bearing for your team, the move is worth planning now.

## The open source options at a glance

Kortix comes first because it is the recommendation here: it is the open-source AI Operating System, and its configuration is files in a git repo you own.

| Tool | Open source | Self-host | Where configuration lives |
| --- | --- | --- | --- |
| Kortix | Yes | Yes, self-host is free | Files in a git repo you own |
| Langflow | Yes, says its README | Yes, Python package or Docker | Flows in the visual builder, export as JSON |
| Dify | Yes, says its README | Yes, Docker Compose | Apps and workflows in the visual canvas |
| n8n | Fair-code, says its README | Yes, Docker or npm | Workflows in the visual canvas |

| Tool | What it is for | Pricing shape |
| --- | --- | --- |
| Kortix | One repo for agents, skills, memory, and connectors | Free, then $40 per seat per month |
| Langflow | Visual builder for AI agents and RAG apps | Open source; free cloud account |
| Dify | Visual workflows, RAG, and agents | Self-host free; cloud from $590 per workspace per year |
| n8n | Workflow automation with native AI | Self-host free; paid cloud and enterprise tiers |

Row sources: [Langflow on GitHub](https://github.com/langflow-ai/langflow), [Dify on GitHub](https://github.com/langgenius/dify), [n8n on GitHub](https://github.com/n8n-io/n8n), [Dify pricing](https://dify.ai/pricing), [n8n pricing](https://n8n.io/pricing), and [Kortix pricing](https://kortix.com/pricing). Prices, star counts, and release dates change, so each carries the date it was checked.

## Why Kortix

Kortix is the leading open-source alternative to Claude Cowork and ChatGPT Work. It is the open-source AI Operating System: agents, skills, memory, and connectors live in one git repo you own, and every session runs on its own cloud computer. One isolated sandbox per session. Each session has its own isolated machine and branch. Session work reaches `main` through a change request. Merge is default-deny for agents, so a person reviews the diff before it lands.

It connects 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP. Any model provider with your own keys, or the ChatGPT plan you already pay for. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free. Kortix has 20,000+ GitHub stars (checked 15 October 2026).

Three commands get a project live:

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix ship
```

## Start here

- [What Flowise was and why it stopped](docs/what-flowise-was.md)
- [The Flowise alternatives, compared](docs/flowise-alternatives-compared.md)
- [Migrating off Flowise, step by step](docs/migrating-off-flowise.md)
- [The Flowise migration FAQ](docs/faq.md)

For a shorter on-site version of this comparison, see [flowisealternative.com](https://flowisealternative.com).

## Where to go deeper

[Read the docs](https://kortix.com/docs) for the full command surface, or [Kortix](https://kortix.com) to start a project without installing anything. Competitor facts come from the projects' own repositories and sites, linked where they are used. Kortix facts come from [Kortix on GitHub](https://github.com/kortix-ai/suna) and the docs.
