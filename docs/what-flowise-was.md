# What Flowise was, and why it stopped

Flowise was an open source tool for building AI agents and LLM workflows through a visual drag-and-drop builder. It let a developer assemble an agent from nodes on a canvas, connect a model, attach tools and a knowledge base, and run the result as a chat app or an API. Flowise ran locally from npm or a Docker Compose stack, or as a managed cloud service.

The project is now archived. Its repository opens with "Flowise has been archived" and links to a "Future of Flowise" discussion ([Flowise on GitHub](https://github.com/FlowiseAI/Flowise), checked 15 October 2026). The project site carries the same message: "We're sunsetting Flowise" ([flowiseai.com](https://flowiseai.com)). The repository shows about 55,500 stars, and the last push landed on 13 August 2026.

## The three builders

Flowise's own documentation described three visual builders, each a superset of the one before it ([Flowise docs](https://docs.flowiseai.com)).

Assistant was the entry point. A person wrote instructions, attached tools, and uploaded files for retrieval, and Flowise produced a chat assistant that answered from that material.

Chatflow added flexibility for single-agent systems and simple LLM flows, with access to techniques such as Graph RAG and reranking.

Agentflow was the widest. It covered chat assistants, single-agent systems, multi-agent systems, and workflow orchestration in one canvas.

Around those builders, Flowise shipped execution traces, an API and SDK, an embedded chat widget, and deployment options for cloud and on-premises servers.

## Who used it

Flowise found its audience among developers who wanted a visual layer over orchestration libraries. Building an agent flow node by node is faster to read than a wall of Python, and a canvas is easy to hand to a teammate. Teams used it for support chatbots, internal question-answering over documents, and prototypes that needed to show their wiring on a screen.

That audience is the one now looking for a replacement. The flows they built are real, and a frozen upstream means no new model providers, no fixes, and no security patches.

## What archived means in practice

An archived repository on GitHub is read-only. Issues and discussions close, pull requests stop, and maintainers step back. Your copy of Flowise keeps running. Nothing in it forces a migration, and nobody is coming to break it.

Two things do change. First, the model providers Flowise talks to keep moving, and a frozen connector eventually falls behind a provider's API. Second, security fixes stop, so a known flaw in a dependency stays open in your deployment.

Flowise still runs today, and the real question is what you run when it stops. The [comparison](flowise-alternatives-compared.md) in this repository covers the open source options, Kortix first, and [the migration guide](migrating-off-flowise.md) shows how to move a Flowise flow onto one of them.
