# Migrating off Flowise, step by step

Moving a Flowise flow onto Kortix takes a handful of steps and a little writing. Kortix is open source, and it is an AI Operating System built on a git repo you own. There is no automated Flowise importer, and there does not need to be one. A Flowise flow is a graph of nodes; a Kortix agent is a markdown file plus a block in `kortix.yaml`. You describe the same job in text, and the runtime reads it from your repository.

The commands are the real ones from [Kortix docs](https://kortix.com/docs) and the [Kortix on GitHub](https://github.com/kortix-ai/suna) README. Budget an afternoon for the first flow and less for each one after it.

## Step 0: inventory what Flowise was doing

Export each flow you still depend on and read it as a list of jobs. Every Flowise canvas answers three questions: what starts the flow, which model answers, and which tools or documents it reaches. Write those three down for each flow before you touch a terminal. This is the whole migration plan, because each Kortix agent needs the same three facts.

Decide what you can drop. A frozen Flowise rarely means every flow is still earning its keep, and a prototype you never shipped is not worth rebuilding.

## Step 1: install the Kortix CLI

Install the CLI with the project's own installer.

```bash
curl -fsSL https://kortix.com/install | bash
```

The CLI runs on Linux and macOS. On Windows, use WSL. It creates projects, runs sessions, and manages agents, secrets, connectors, and triggers from a terminal or a script.

## Step 2: create the project

Turn a directory into a Kortix project.

```bash
kortix init
```

`kortix init` writes `kortix.yaml` and the runtime config, and scaffolds the directories for your agents and skills. Commit the result to a git repo you own. This repository becomes the source of truth that the Flowise canvas never was.

## Step 3: describe each flow as an agent

Write one agent per job from your Step 0 list. An agent is `agents/<name>.md` for its behavior, plus an `agents.<name>` block in `kortix.yaml` for its governance. The markdown is the prompt: what the agent does, in plain language. The `kortix.yaml` block says which connectors it may reach.

A Flowise "Chatflow" that answered support questions becomes an agent whose markdown says to read the ticket, find the answer in the connected knowledge source, and draft a reply. The node graph is gone, and the job is now readable text that a teammate can edit without opening a canvas.

## Step 4: reconnect the tools

Replace Flowise tool nodes with connectors. Kortix connects 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP. You can set each connector action to Allow, Ask or Block, down to the arguments of each call, so the send step can wait for a person.

Move credentials into secrets. Secrets are encrypted at rest with a key per project. Connector credentials are brokered server-side and never enter the machine, so a key that sat in a Flowise credential store does not have to sit in your repository.

## Step 5: ship it

Push the project up and run it.

```bash
kortix ship
```

`kortix ship` checks that the project compiles, asks for any missing secrets, pushes the repository, and brings the whole thing live in the cloud.

## Step 6: run sessions and review the work

Start a session and watch it work.

```bash
kortix sessions new --prompt "Summarize this week's commits and open a change request"
kortix cr ls
kortix chat
```

Each session runs one agent on its own cloud computer, cloned from your repo and working on a new branch. The agent commits, pushes its branch, and opens a change request against the default branch. Session work reaches `main` through that change request, and merge is default-deny for agents. Read the diff and merge it, or send it back. From the terminal, `kortix cr ls` lists what agents propose and `kortix chat` talks to a session's agent.

## Optional: self-host the whole platform

If Flowise ran inside your own network, Kortix can too.

```bash
kortix self-host start
```

A self-hosted instance is the full platform on a server you control, one Docker Compose stack that the `kortix self-host` CLI installs, configures, and updates. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free. The first run asks a few questions and needs a sandbox provider key, and you add a model key in the app after the first sign-in.

## The Flowise to Kortix mapping

| In Flowise | In Kortix |
| --- | --- |
| Visual flow or canvas | Agent markdown plus a `kortix.yaml` block |
| Node credentials | Secrets, encrypted at rest with a key per project |
| Model node | Model picked per agent, per session, or per message |
| Tool nodes | Connectors, 3,000+ apps plus MCP and raw HTTP |
| Execution traces | Sessions on their own cloud computer, with an audit trail |
| Embedded chat widget | Web, Slack, Microsoft Teams, CLI, and API |

## What does not carry over

Two Flowise ideas have no direct equivalent, and it is worth knowing before you start.

A shared canvas is now a shared repository. Instead of opening one flow and editing nodes together, your team reviews changes as diffs. That is a workflow change, and it is the point: every edit is reviewable and reversible.

A single attached knowledge base is now a connector. Point the agent at the document source you already use, and it reaches the same material through a connector with an audience and a policy instead of a base baked into one flow.
