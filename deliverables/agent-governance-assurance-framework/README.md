# Agent Governance and Assurance Framework

A framework to govern AI agents in production, and to keep them safe and ready for an
audit. You can start with one agent. You do not need a plan for the whole company first.

The [MACH Alliance](https://machalliance.org)
[Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations)
develops this framework.

## Who this is for

You have an AI agent in production, or you will soon put one there. Other people will ask
you questions about it:

- What can this agent do on its own?
- Which data can it read, and which systems can it change?
- Who approved it, and when?
- What do you do when it goes wrong?
- Can you prove what it did?

This framework tells you which documents answer those questions. It also shows how the
documents connect to each other. Many good documents about AI principles already exist.
This is a structure, not a set of principles.

## What you do first

Pick one agent. Then do these six steps in order:

1. Give the agent a risk tier. Write down why you chose that tier.
2. Give the agent its own login. Limit the login to the tools and the data that this one
   agent needs.
3. Write the agent design document. It records what the agent does and what it can touch.
4. Name one person to accept the risk and to approve the agent. Record the date.
5. Log every tool call the agent makes. Set a small number of alerts.
6. Keep the records that an auditor will ask for.

Steps 1, 3 and 4 are documents. They need no new platform work, and you can write them
this week. Step 2 needs one login and one set of permissions, not a company standard.

Each step belongs to one layer of the framework.

## The five layers

Each layer holds up the layer above it. A rule in your policy is true only if the platform
enforces it. The control is correct only if the agent's design uses it. The design is
valid only if a person accepted it. The record is proof only if you keep it safe. Break
one link, and every layer above it is only a claim.

![Flow diagram titled "Agent Governance, Safety and Compliance: A Layered Model", from the MACH Alliance Agent Adoption & Operations Working Group. Five boxes are stacked in a single column, shaded from light blue at the top to dark navy at the bottom. Each box names the layer and, below it, the document you write for that layer. From top to bottom they are Layer 1, Policy, holding Risk Tiers and the Tier Test; Layer 2, Platform Controls, holding the Access Control Ladder; Layer 3, Agent Design, holding the Agent Design Document; Layer 4, Live Operations, divided by a horizontal rule into Continuous above, holding the Monitoring Plan, and Triggered below, holding the Incident Playbook; and Layer 5, Audit Evidence, holding the Audit Log Rules. The table below this figure gives the same contents and says what each layer does. Grey arrows connect each box down to the next, labelled in order: "tiers set the controls", "controls limit each agent", "a person approves the agent", and "records become evidence". A single orange line runs up the right-hand side of the diagram, leaving the Layer 5 box at the bottom and arriving as an arrowhead at the Layer 1 box at the top; it is labelled "audit findings correct the tiers".](layered-model.svg)

| Layer | What you write | What it does |
|---|---|---|
| 1. Policy | Risk Tiers and the Tier Test | Sets the risk tiers. Gives you a test that puts any agent into the correct tier. |
| 2. Platform Controls | Access Control Ladder | Turns each tier into controls you can enforce. You climb the ladder one step at a time, one agent at a time. |
| 3. Agent Design | Agent Design Document | Records one agent: its purpose, its tools, its data, its limits, and why it is in its tier. One named person accepts the risk that is left and approves the agent before it goes live. |
| 4. Live Operations | Monitoring Plan and Incident Playbook | Compares live behavior to the design document. Tells you what to do when an alert starts. |
| 5. Audit Evidence | Audit Log Rules | Keeps proof of what the agent did, and maps that proof to SOC 2, ISO 27001 and the EU AI Act. |

Layer 5 also sends its findings back to Layer 1. Audits show you where your tiers are
wrong. Without that return path, the tiers stay as you first wrote them while the agents
keep changing.

The [full write-up](agent-governance-layered-model.md) gives the reason for each layer and
a plan to deliver the layers one at a time.

## Words we use

Risk and compliance work has a large vocabulary. We use plain words instead, because a
control that nobody understands is a control that nobody applies. This table gives our
word, what it means, and the word that other frameworks use for the same thing.

| We say | It means | Other frameworks say |
|---|---|---|
| risk tier | A level of risk, from low to high. Each tier gets stronger controls. | risk classification, autonomy level |
| tier test | A set of questions that puts an agent into the correct tier. | diagnostic rubric, risk assessment |
| agent design document | One document that records what one agent does and what it can touch. | system card, model card, design dossier |
| the risk that is left | The risk that stays after you add your controls. | residual risk |
| how far the damage spreads | The number of systems, records or people that one agent mistake can affect. | blast radius, impact scope |
| approval to go live | A record of who accepted the risk, on what date, and against which version of the design document. | risk acceptance, authorization to operate |
| agent login | An account that belongs to one agent and to nothing else. | service identity, non-human identity, workload identity |
| decision record | The prompts, tool calls, inputs and outputs that you store from one agent run. | trace, telemetry, decision trace |
| tool call | One action that the agent takes through a tool: a search, a write, a payment, an email. | function call, action invocation |
| drift | The agent's live behavior moves away from what its design document says. | behavioral drift, scope creep |
| locked record | A record that nobody can change after you write it. | immutable log, WORM storage |
| changes are visible | You can prove that nobody changed a record. | tamper-evident |
| ladder | A set of steps. The first step is small and quick. The top step is the full model. | maturity model |

## How this fits with other frameworks

This framework does not start from an empty page. Several organizations now build similar
structures for agent governance. Where their work is already good, we point to it. We do
not invent a second vocabulary for the same idea.

We add three things that the other work does not give you:

1. A test that puts an agent into a risk tier, and that shows your reasons.
2. A path that adds access control one agent at a time, instead of one company mandate.
3. A design document for one agent that carries the proof of its own tier.

Read these alongside this framework:

- **[Gartner AI TRiSM](https://www.gartner.com/en/articles/ai-governance-trism)**: Trust,
  Risk, and Security Management. It covers AI governance, runtime inspection and
  enforcement, information governance, and infrastructure. It is the closest match to
  Layers 1, 4 and 2.
- **[Gartner Market Guide for Guardian Agents](https://www.gartner.com/en/newsroom/press-releases/2026-04-28-gartner-identifies-six-steps-to-manage-artificial-intelligence-agent-sprawl)**:
  a new group of products that supervise other agents. They cover visibility, continuous
  assurance, and runtime enforcement. A match to Layer 4.
- **[AIUC-1](https://aiuc-1.com/)**: an agent standard that you can certify against,
  published by the AIUC-1 Consortium. It covers data and privacy, security, safety,
  reliability, accountability, and society. It includes third-party audit and published
  maps to NIST AI RMF, ISO 42001, the EU AI Act, MITRE ATLAS and OWASP. It covers Layers 1
  to 5 as certification criteria. This framework is different, because it tells you how to
  operate rather than what to certify against.
- **[NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)**,
  with the **[Cloud Security Alliance Agentic AI Profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/)**:
  four functions (Govern, Map, Measure, Manage) and extra categories for agents. Its four
  autonomy levels match Layer 1. Its runtime records and autonomy checks match how Layer 4
  feeds back into Layer 1.
- **ISO/IEC 42001**: the AI management standard that you can certify against. It is the
  natural partner to Layer 5.
- **[FIDO Alliance, Agentic Authentication Technical Working Group](https://fidoalliance.org/fido-alliance-to-develop-standards-for-trusted-ai-agent-interactions/)**:
  standards for agent identity, delegation and authorization across vendors. A narrower
  partner to Layer 2.
- **[ASG-WG](https://www.asg-wg.org/)** and the
  **[WEF AI Governance Alliance](https://www.deepinspect.ai/blog/ai-governance-alliance)**:
  other multi-party groups that work at the same level as this working group.

## What comes next

The five documents in the table are not written yet. The `artifacts/` directories hold a
place for each one. For each layer we plan to publish a form that you fill in, short notes
on how to fill it in, and one worked example. The agent design document comes first,
because a team touches that one first.

## Status

Draft. The MACH Alliance Agent Adoption & Operations Working Group discusses it now. We
welcome your feedback. Please open an issue or a pull request.
