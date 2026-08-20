# Agent Governance and Assurance Framework

A framework to govern AI agents in production, and to keep them safe and ready for an audit. You can start with one agent. You do not need a plan for the whole company first.

The [MACH Alliance](https://machalliance.org) [Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations) develops this framework. This is the September 2026 Draft.

## Who this is for

You have an AI agent in production, or you will soon put one there. Other people will ask you questions about it:

- What can this agent do on its own?
- Which data can it read, and which systems can it change?
- Who approved it, and when?
- What do you do when it goes wrong?
- Can you prove what it did?

This framework tells you which documents answer those questions, and how those documents connect to each other. Many good documents about AI principles already exist. This one gives you a structure instead.

## What you do first

Pick one agent, and work the five stages in order.

1. **Agent design.** Write the Agent Design Document: the outcome the agent is for, what it does, and the tools and the data it needs. You need that description before you can judge the agent's risk.
2. **Policy.** Place the agent in one of your Risk Classifications, with that document in front of you, and write down why it belongs there. If none of them fits, add the one that does. That happens often at the start. Your first agent needs one classification; the rest can come later.
3. **Platform controls.** Stand the agent up on a platform you control, at one of your Platform Control Levels: the model and its version, the tools it can call, the framework, the hosting, and an agent login scoped to the design document and nothing wider. Run your evals against that exact setup, and record what they found.
4. **Live operations.** Keep those evals running against the live agent, on a schedule that nobody has to remember. Your Monitoring Plan says what you log: the tool calls and their arguments, the inputs and outputs, and enough of each run to replay it. Alert when an eval fails, and let the Incident Playbook say what you do when one does.
5. **Audit and assurance.** Keep the records an auditor will ask for, under your Audit Log Rules. Then keep a second record: which evals ran, when, what they found, and what changed because of it. The first record shows what the agent did. The second shows that somebody is still checking, and its findings correct the classifications in stage 2 and the designs in stage 1.

A gate sits between stages 3 and 4. One named person signs off on the agent as a whole: what it is for, its classification, the platform it runs on, what the evals showed, and the risk that is left. Record the name, the date, and the version of the document they signed.

Each stage makes the one before it real. A design document describes an agent, and a classification says what risk that description carries. The platform then enforces the limits the classification sets, and evals that run on their own tell you whether live behavior stays inside them. The records are proof only if they are safe and somebody still reads them. Where one of those links fails, the stages resting on it are paperwork.

None of these documents is finished when you write it. An agent that fits no classification, an audit finding against a classification's criteria, or an eval that catches a control not holding will each tell you that something earlier needs work. Expect to revise all of them.

[The five stages in full](five-stages.md) is the rest of the framework: what each stage does, the reason for each one, and a plan to deliver them one at a time.

## Words we use

Risk and compliance work has a large vocabulary. We use plain words instead, so that the people who have to apply a control can understand it. The [glossary](glossary.md) gives our word, what it means, and the word that other frameworks use for the same thing.

## How this fits with other frameworks

Several organizations already build similar structures for agent governance. Where their work is good, we cite it and point at it instead of inventing a second vocabulary for the same idea.

We add three things that the other work does not give you:

1. A test that puts an agent into a risk classification, and that shows your reasons.
2. A path that adds platform controls one agent at a time, instead of one company mandate.
3. A design document for one agent that carries the proof of its own classification.

[What we reference and cite](references.md) lists the works this framework builds on, what each one covers, and which stage it matches. Read it if you already run a program against one of them, because it tells you how much of that program you can keep.

## What comes next

The documents for the five stages are not written yet. The `artifacts/` directories hold a place for each one. For each stage we plan to publish a form that you fill in, short notes on how to fill it in, and one worked example. The agent design document comes first, because a team touches that one first.

## Status

**September 2026 Draft.** Cite the version you built against.

The MACH Alliance Agent Adoption & Operations Working Group discusses this version now. We welcome your feedback. Please open an issue or a pull request.
