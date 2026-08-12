# Agent Governance, Safety and Compliance: A Layered Model

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. Draft
prepared August 2026, for discussion.*

## Purpose

The working group plans three documents about governance, safety and compliance. Written
as three separate documents, they lose the connections between them.

This document proposes five connected layers instead. Governance for agents holds together
only when policy, platform controls, agent design, live operation and audit evidence make
one loop. Each layer is true only if the layer above it is true. The evidence at the bottom
must climb back up and correct the top.

We also use plain words for each part. The
[table of words](README.md#words-we-use) in the README gives our word, its meaning, and the
word that other frameworks use.

## The model at a glance

![Flow diagram titled "Agent Governance, Safety and Compliance: A Layered Model", from the MACH Alliance Agent Adoption & Operations Working Group. Five boxes are stacked in a single column, shaded from light blue at the top to dark navy at the bottom. Each box names the layer and, below it, the document you write for that layer. From top to bottom they are Layer 1, Policy, holding Risk Tiers and the Tier Test; Layer 2, Platform Controls, holding the Access Control Ladder; Layer 3, Agent Design, holding the Agent Design Document; Layer 4, Live Operations, divided by a horizontal rule into Continuous above, holding the Monitoring Plan, and Triggered below, holding the Incident Playbook; and Layer 5, Audit Evidence, holding the Audit Log Rules. The table below this figure gives the same contents and says what each layer does. Grey arrows connect each box down to the next, labelled in order: "tiers set the controls", "controls limit each agent", "a person approves the agent", and "records become evidence". A single orange line runs up the right-hand side of the diagram, leaving the Layer 5 box at the bottom and arriving as an arrowhead at the Layer 1 box at the top; it is labelled "audit findings correct the tiers".](layered-model.svg)

*Figure 1. The five layers as one loop. The grey arrows run from policy down to operations.
The orange arrow returns audit evidence to policy.*

| Layer | What you write | What it does | What it feeds |
|---|---|---|---|
| 1. Policy | Risk Tiers and the Tier Test | Sets the risk tiers. Gives you a test that puts any agent into the correct tier. | Tells Layer 2 which controls each tier needs. |
| 2. Platform Controls | Access Control Ladder | Turns each tier into controls you can enforce, one step and one agent at a time. | Limits what each Layer 3 agent can do. |
| 3. Agent Design | Agent Design Document | Records one agent: its purpose, its tools, its data, its limits, and why it is in its tier. | One named person accepts the risk that is left and approves the agent. It then goes live under Layer 4. |
| 4. Live Operations | Monitoring Plan and Incident Playbook | Compares live behavior to the design document. Tells you what to do when an alert starts. | Its records become the evidence for Layer 5. |
| 5. Audit Evidence | Audit Log Rules | Keeps proof of what the agent did, and maps it to SOC 2, ISO 27001 and the EU AI Act. | Its findings correct the tiers in Layer 1. |

## Layer 1: Policy and risk tiers

**What you write: Risk Tiers and the Tier Test.**

A list of tiers works only if it comes with two more things. You need a repeatable way to
put a given agent into one tier. You also need a description of how an agent in each tier
behaves in practice, not only the criteria on paper.

### The tiers

The first part is the list of tiers and their criteria. Judge each agent on how sensitive
its data is, how much money it can move, whether you can undo its actions, and how far the
damage spreads.

### The tier test

The second part is the test. It is a set of questions that a person walks through. The
answers show why this agent is Tier 2 and not Tier 1 or Tier 3.

Without the test, every team declares its own agent low risk to avoid attention. You then
hold a document that asserts that somebody assessed the risk. That defeats the purpose of
the tiers.

### Tiers drift

The declared tier and the real behavior move apart over time. A new model version, a new
tool, or a change to a prompt can push the real behavior above the tier on paper.

So you cannot run the test once, at design time. You must run it again against what Layer 4
sees.

## Layer 2: Platform controls, as a ladder

**What you write: Access Control Ladder.**

Some companies write one access control standard for every agent. Security must approve it
before anything ships. Teams then debate the scope for two quarters, and nobody deploys it.

This layer must work for one agent, in this sprint, with no company-wide dependency.

### The three steps

A ladder does that. Each step is useful on its own.

1. **The first step, available today, for one agent.** Give the agent its own login that it
   shares with nothing else. Limit its credentials to the tools and the data that this one
   agent needs. Write down how to revoke the credentials by hand.
2. **The middle step.** Tie the scope of the credentials to the agent's tier from Layer 1.
   Policy then narrows the permissions of a higher-tier agent. An engineer no longer
   decides this case by case.
3. **The top step.** Add policy as code, automatic setup and revocation, and a continuous
   check that the granted permissions still match the declared tier.

The top step is the full company model. The ladder makes it a destination. It is not a
condition that you must meet before you start.

## Layer 3: The agent design document

**What you write: Agent Design Document. It is a system card for the agent.**

A table of human oversight and escalation tells you what to do when something goes wrong.
It does not tell you how anybody knows that this agent belongs in the tier it claims. Both
things belong in one document, because the escalation design depends on a true tier.

### What it contains

You write one document for each agent, before it goes near production. It covers:

- the purpose and the scope of the agent;
- the tools and the data that it can touch;
- what it can decide alone, and what it cannot;
- how it escalates to a person, and how a person overrides it;
- why this agent sits in the tier that Layer 1 gave it.

### Why the last section matters most

That last section carries the most weight. It answers the Layer 1 test with this agent's
own details instead of in the abstract.

The document is close to a model card or a system card. It covers the behavior and the
authority of an agent, and not the training data and benchmarks of a model. The nearest
match in other standards is the accountability section of
[AIUC-1](https://aiuc-1.com/), which asks for compliance documents and failure plans at
the level of a whole company. This document is for one agent, and it carries the proof of
its own tier. It is the document that a reviewer reads to decide whether the agent is what
it claims to be.

### The step across: approval to go live

Nothing crosses from Layer 3 to Layer 4 on its own. The design document is only a claim. A
person must accept it.

That step is a single recorded act. By then, Layer 1 has set the tier, Layer 2 has put the
matching controls in place, and Layer 3 has recorded the agent and the risk that is left. A
named person then accepts that risk and approves the agent to operate.

This is one person and one record. It is not a review board. The weight sits in the
attribution, not in the ceremony: who accepted, on what date, for what scope, and against
which version of the document.

That record is also evidence for Layer 5.

### The approval is temporary

You grant the approval against one description of how the agent behaves. Layer 4 can show
you behavior that no longer matches that description. The approval is then not merely old.
It is void until somebody looks at it again.

That is what gives the feedback loop from Layer 4 a consequence. Without it, the loop only
informs.

## Layer 4: Live operations, from watching to response

**What you write: Monitoring Plan (continuous) and Incident Playbook (when an alert
starts).**

This layer holds two connected loops.

### The continuous loop

The Monitoring Plan defines what you record on every run: the decision record, the tool
calls, and the inputs and outputs. It also defines which tests you run on a schedule
against known failure modes, which numbers count as normal, and what starts an alert.

### The loop that an alert starts

The Incident Playbook defines what happens after an alert starts: triage, a review of the
decision record, a fix, and a review after the incident.

Write this loop for the ways that agents fail. Examples are tool calls that fail in a
chain, prompt injection, and quiet scope creep. Do not copy the loop from ordinary software
incident response.

### The loop also re-checks Layers 1 and 3

The continuous loop is how you re-check Layer 1 and Layer 3 over time.

An agent can start to touch more sensitive data, or to take actions that you cannot undo.
If its design document does not allow this, a monitor must show you within days. An audit
six months later is too late.

The loop also puts the Layer 3 approval back in play. Drift of that kind means that
somebody must accept the risk again, on today's evidence, or stop the agent.

### Monitoring is also a ladder

The distance between what a framework asks for and what most companies can do today is
largest here. So give this loop the same treatment as Layer 2. Full decision records with
scheduled tests are the destination, not the entry price.

A useful first step is narrower:

- Log every tool call and its arguments.
- Keep the inputs and the outputs for a fixed period.
- Alert on a few coarse signals: a call to a tool outside the declared set, an unusual
  volume, or a high escalation rate.

Reasoning records, replay and automatic tests come later. State the step that each agent is
actually on. An approval that assumes a monitor that does not exist is worse than an
approval with the limit on the record.

### Your records can hold more risk than your systems

Records are not harmless exhaust. A decision record holds the prompts, the context and the
outputs of a system that reaches into whatever data its tools expose. That regularly makes
your record store more sensitive than any single system that the agent reads from, because
the store concentrates data from all of them.

So reduce what you capture, at capture time and not at query time. Remove sensitive fields
before they land. Control access to the records at least as tightly as access to the
systems underneath.

A monitor that quietly makes an unclassified copy of regulated data has broken Layer 2 from
the inside.

## Layer 5: Audit evidence

**What you write: Audit Log Rules.**

Layer 4 records things for debugging. The decision records and the tool calls help an
operator understand what an agent did.

Compliance asks for different things: locked records, a defined retention period, proof
that changes are visible, and a map to the frameworks that you already follow. Those
include SOC 2, ISO 27001, and the logging duties in the EU AI Act for higher-risk systems.

### Reuse the maps that already exist

The accountability section of [AIUC-1](https://aiuc-1.com/) covers the same ground for
agents. It publishes maps to NIST AI RMF, ISO 42001, the EU AI Act and MITRE ATLAS. Log
rules that you build against AIUC-1 inherit those maps. You do not have to derive them
again.

This layer keeps the debugging question apart from the question that an auditor asks: can
you prove what happened, and why? Both draw on the same records. They are not the same
document.

### Retention pulls two ways

Compliance sets a floor on how long you keep the evidence. Data protection law sets a
ceiling on how long you may hold personal data. It also gives people the right to erasure,
and a locked record is a poor structure for that right.

Reconcile the two. Do not pick one. Usually you split the record in two parts:

- **What happened.** What the agent did, which decisions it took, and who approved it. Keep
  this for a long time.
- **The data it touched.** Keep this for a short time.

Access to the audit record is itself an event that you must record.

### The loop closes here

The findings from this layer must correct the tiers and the thresholds in Layer 1. Those
tiers were written to satisfy exactly these audits.

Without that return path, your governance stays as first written on paper, while the agents
that it governs keep changing underneath it.

## How to deliver this one piece at a time

Five layers sound like a company program that runs for many quarters. Programs like that
tend not to ship. This model must answer that concern.

The layers are designed so that a narrow version can work from end to end, quickly. You
then add maturity one layer at a time. No layer must be complete before any of it is real.

A reasonable first pass:

1. Pick one or two agents that you already build.
2. Write their tier and their answer to the tier test, and their design documents. Both are
   documents. Neither needs platform work.
3. Apply the first step of the Layer 2 ladder to those same agents: a login of their own,
   and narrow credentials.
4. Record who accepted the risk and who approved each agent to run. At this size, that is a
   few lines at the end of the design document, not a process.
5. Start the Layer 4 continuous loop for those agents only. A minimal loop that logs tool
   calls and holds a few alerts is enough.
6. Add the Layer 5 log rules once you hold real records to keep.

After that narrow slice works from end to end, widen Layer 2. Move toward automatic
setup that follows the tier, and then toward policy as code. By then the working group
scales something that works. It does not design something that nobody has deployed.
