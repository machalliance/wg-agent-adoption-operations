# Agent Governance and Assurance Framework

A framework to govern AI agents in production, and to keep them safe and ready for an audit. You do not need a plan for the whole company; you can start with one agent.

The [MACH Alliance](https://machalliance.org) [Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations) develops this framework. This is the September 2026 Draft.

## Who this is for

You have an AI agent in production, or you will soon put one there. Other people will ask you questions about it:

- What can this agent do on its own?
- Which data can it read, and which systems can it change?
- Who approved it, and when?
- What do you do when it goes wrong?
- Can you prove what it did?

Plenty of documents already set out AI principles. This one tells you which documents answer those five questions, and how they connect to each other.

## What you do first

Pick one agent, and work the five stages in order.

1. **Agent design.** Write down what the agent is for, what it does, and the tools and the data it needs. You need that description before you can judge the agent's risk.
2. **Policy.** Place the agent in one of your Risk Classifications, and write down why it belongs there. If none of them fits, add the one that does.
3. **Platform controls.** Stand the agent up on a platform that holds it to that classification's limits, and run your evals against that exact setup.
4. **Live operations.** Keep those evals running against the live agent, log enough of each run to replay it, and say what happens when an eval fails.
5. **Audit and assurance.** Keep proof of what the agent did, and proof that somebody is still reading the evals.

A gate sits between stages 3 and 4. One named person signs off on the agent as a whole: what it is for, its classification, the platform it runs on, what the evals showed, and the risk that is left. Record the name, the date, and the versions of the documents they signed. That record is the [Platform and Sign-off Record](artifacts/03-platform-controls/platform-and-sign-off-record.md), one per agent.

[The five stages in full](artifacts/five-stages.md) is the rest of the framework: what each stage hands to the next, the reason for each one, and why none of these documents is ever finished.

## Words we use

Risk and compliance work has a large vocabulary. We use plain words instead, so that the people who have to apply a control can understand it. The [glossary](glossary.md) gives our word, what it means, and the word that other frameworks use for the same thing.

## How this fits with other frameworks

Several organizations already build similar structures for agent governance. Where their work is complementary, we cite it and point at it instead of inventing a second vocabulary for the same idea.

NIST's four functions give the shape of the loop. Scoring each dimension on a ladder of its own, instead of collapsing everything into a single number, comes from CISA's Zero Trust Maturity Model, and the content of our two ladders compresses work from the Cloud Security Alliance, CISA and Gartner. What none of them gives you is a way to start. Everything here works for one agent, governed by one team, in one sprint: no company program, no standard every team has to agree first. Each stage checks the one before it, so what you end up holding is evidence.

The [A2A Agent Card](https://a2a-protocol.org/latest/specification/), which the platform agent registries follow, declares what an agent can do and how to reach it. It carries no field for the accountable person, the classification, the sign-off, or the escalation path. Discovery got standardized first.

[What we reference and cite](references.md) lists the works this framework builds on, what each one covers, and which stage it matches. Read it if you already run a program against one of them, because it tells you how much of that program you can keep.

## How the documents are split

For each stage we publish the form on its own, and the reasoning behind it separately, so that you can fill one in without reading the other. A **standard** describes your whole company and you write it once; a **record** describes one agent and you keep one per agent.

The per-agent records are also available as a single spreadsheet, [agent-governance-forms.xlsx](artifacts/agent-governance-forms.xlsx), for teams who would rather fill them in there. The four standards are not in it. They are policies you write once for the whole company, and they stay in this repository as markdown.

## License

[CC BY 4.0](LICENSE.md). Copy the forms, rename them, and rewrite them for your own company. Attribution and the version you built against are all we ask. The MACH Alliance name and logo are not covered by that license, so replace the branding if you adapt the spreadsheet.

## Status

**September 2026 Draft.** Cite the version you built against.

The MACH Alliance Agent Adoption & Operations Working Group discusses this version now. We welcome your feedback. Please open an issue or a pull request.
