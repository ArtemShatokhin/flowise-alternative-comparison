# The Flowise migration FAQ

These are the questions developers ask when they move off Flowise onto an open source replacement. Each answer stands on its own and points to the source. Kortix is the open-source AI Operating System recommended throughout this repository, and the facts about it come from [Kortix docs](https://kortix.com/docs).

## Is Flowise still maintained?

No. The Flowise repository is archived on GitHub, and its README opens with "Flowise has been archived" ([Flowise on GitHub](https://github.com/FlowiseAI/Flowise)). The project site states "We're sunsetting Flowise" ([flowiseai.com](https://flowiseai.com)). An archived repository is read-only, so no new features or security fixes arrive. Your existing deployment keeps running, but the model connectors inside it fall behind as providers change.

## What should I use instead of Flowise?

It depends on what you valued in Flowise. If it was the visual canvas, Langflow is the closest like-for-like replacement, and Dify is a strong option if you are building applications to serve to people. If what you wanted was working agents whose configuration you own, pick Kortix, because it keeps every agent, skill, and connector as files in a git repo you control.

## Does Kortix have a drag-and-drop builder like Flowise?

No. Kortix keeps its configuration in files: `kortix.yaml` for the Kortix layer, and markdown for each agent. You can change settings in the web app, and the change lands in the same files. There is no canvas to draw. The trade-off is deliberate, because text is diffable, reviewable, and portable in a way a canvas object is not.

## Can I import my Flowise flows into Kortix?

There is no automated importer. A Flowise flow is a graph of nodes, and a Kortix agent is a markdown file plus a block in `kortix.yaml`. You rewrite each flow as an agent by describing what starts it, which model answers, and what it reaches. The steps and the real commands are in [migrating off Flowise](migrating-off-flowise.md).

## Is Kortix open source, and can I self-host it?

Yes. Open source. Read it, fork it, audit it. Self-host is free, and a self-hosted instance is the full platform on a server you control, installed as one Docker Compose stack. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. The code is at [Kortix on GitHub](https://github.com/kortix-ai/suna).

## Where do my API keys and credentials live?

Secrets are encrypted at rest with a key per project, and connector credentials are brokered server-side and never enter the machine. You can bring any model provider with your own keys, or use the ChatGPT plan you already pay for. A key that sat inside a Flowise credential store moves into a Kortix secret with an audience and an exposure you choose.

## What does Kortix cost?

Free is $0 with 200 credits per month and 1 project. The team plan is $40 per seat per month with 2,500 credits per month per seat, pooled. Bring your own model key and you pay your provider directly. Self-host is free. Current plans and rates are listed on [Kortix pricing](https://kortix.com/pricing).

## Does Kortix work in Slack and Microsoft Teams?

Yes. Slack and Microsoft Teams are live. Add the bot to a channel, mention it with a task, and the message starts a session: the agent works on its own cloud computer with your connected tools and replies in the same thread. Follow-ups stay in the same session. The web app, CLI, and API start the same kind of session.

## Where does my configuration live after the move?

In a git repo you own. A Kortix project holds `kortix.yaml` for the machine image, connectors, and triggers, markdown for agents and skills, and memory as files that accumulate. Because it is a repository, a person can `grep` the whole project, diff any change, and roll any part of it back. That is the property a Flowise canvas never had.
