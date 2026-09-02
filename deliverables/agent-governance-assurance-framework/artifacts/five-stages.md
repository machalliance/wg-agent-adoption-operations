# Agent Governance and Assurance: The Five Stages

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

## Purpose

Governance for agents holds together only when agent design, policy, platform controls, live operation and audit records reach each other. Each stage makes the one before it real.

This document says what each stage does and what it hands to the next. The [README](../README.md) is the short version. [The forms](README.md) are the fill-in documents, listed in the order to fill them in, each with a notes file carrying the reasoning behind it.

We do our best to use plain words throughout. The [glossary](../glossary.md) gives our word, what it means, and the word that other frameworks use for the same thing. [What we reference and cite](../references.md) lists the works this framework builds on and which stage each one matches.

## Where to start

Pick one agent you already run, or are about to. [The forms](README.md) list themselves in the order to fill them in.

Aim low on the first pass. One classification, the one your agent belongs to. Level 1 on both ladders, recorded honestly. Whatever evals you already have, run against the real setup, with the results and the gaps written down and signed. A narrow version working end to end beats a maturity program nobody has deployed. Widen stage 3 once it works.

The rest of this document is the reasoning: what each stage does, what it hands to the next, and why none of it is ever finished.

## The five stages at a glance

You work the stages in order. Each one hands something to the next, and the last one sends findings back to the first.

| Stage | What the stage does | What it hands on |
|---|---|---|
| 1. Agent design | Records what one agent is for and what it can touch. | A description that stage 2 can classify. |
| 2. Policy | Places that agent in a classification, with your reasons. | The controls stage 3 has to enforce. |
| 3. Platform controls | Stands the agent up on a platform that holds it to those limits, and runs your evals against it. | A sign-off, and then live operation. |
| 4. Live operations | Keeps the evals running, and says what happens when one fails. | The records stage 5 keeps. |
| 5. Audit and assurance | Keeps proof of what the agent did, and proof that somebody is still reading the evals. | Corrections to the classifications and the designs. |

The last column is the part most governance programs leave out. Stage 5's findings correct the classifications in stage 2 and the designs in stage 1, so the sequence is a loop and not a pipeline.

One finding, traced. A monitor alerts on a call to a tool the design document does not list. That is stage 4 telling you a stage 3 control is not holding, so the sign-off granted under it is void until somebody looks again. The team either revokes the access or adds the tool to the grant list, which is a new version of a stage 1 record. If that tool reaches data the old answers did not cover, the data sensitivity question in the stage 2 test has a new answer, the classification may move, and the levels stages 3 and 4 have to hold the agent to move with it. The stage 5 assurance record holds what was found, what it changed, and whether the change is live. One alert, five stages.

## Standards and records

Two kinds of document run through the five stages, and they behave differently.

A **standard** describes your whole company. You write it once and it grows as you build agents it does not yet describe. There are four, and only four: the [Risk Classifications](02-policy/risk-classifications.md), the [Platform Control Levels](03-platform-controls/platform-control-levels.md), the [Monitoring Levels](04-live-operations/monitoring-levels.md), and the [Audit Log Rules](05-audit-and-assurance/audit-log-rules.md). Everything else is a **record**. A record describes one agent: you fill in one per agent, and revise it whenever that agent changes.

The two are versioned against different things. A record is signed off against a version of itself. A standard is not signed off at all; it is the thing records are judged against. Keeping both in one file means a change to either invalidates both, which is why the stage 3 sign-off lives in its own record and not inside the design document.

Both sets of levels score a **platform**, not a company and not an agent. An agent then records the level actually applied to it, which can be lower than its platform's and can never be higher. Stages 3 and 4 each produce two numbers, and both go on that agent's record.

None of these documents is finished when you write it. An agent that fits no classification means the list is short a category. An audit finding means a classification's criteria were wrong. A monitor reporting a tool call outside the declared set means a control is not holding, and that the sign-off granted under it no longer applies. Write each one expecting to revise it, and record the date you last did. A framework that only runs one way governs the agents you had when you wrote it.

## Stage 1: The agent design document

**What you write: the [Agent Design Document](01-agent-design/agent-design-document.md), one per agent. It is a system card for the agent.**

An agent's name tells you nothing about its risk. The team that builds it writes down, before it goes near production, what it is for, what it can decide alone, how it escalates, and which tools and data it needs. That grant list is what stage 3 grants and nothing wider. That description comes first, and everything after it either enforces the description or checks it.

Fill in the outcome first: what the agent is for, how you measure it, and who owns that number. An agent with no stated outcome cannot be judged, and you cannot stop it on evidence. Section 6 then carries the answers to the stage 2 test, so the document carries the proof of its own classification.

The [notes](01-agent-design/agent-design-document-notes.md) cover the hard sections. The nearest thing to this document in production is the [A2A Agent Card](https://a2a-protocol.org/latest/specification/), which the platform agent registries follow: it declares capability and authentication, and carries no field for the accountable person, the classification, the sign-off, the sensitivity of the data reached, or the escalation path. A2A is solving discovery, so those omissions are deliberate. Where the two overlap, generate one from the other instead of maintaining both by hand.

## Stage 2: Policy and risk classifications

**What you write: [Risk Classifications and the Classification Test](02-policy/risk-classifications.md), one standard in two parts.**

This is the only stage that is not about a single agent. The classifications describe your whole company: the kinds of agent you build, and the controls that follow from each kind. Each agent is placed in one of them, and the record of that placement stays in stage 1.

You do not need the whole set before you ship. You need the one classification your first agent belongs to, and the rest grows as you build agents the set does not yet describe.

We ship four as a starting point — Routine, Significant, Sensitive, Critical — judged on what a mistake costs, not on how the agent works. Each names the platform control level and monitoring level an agent in it requires, who signs off, and what triggers reclassification. Those level columns tie this stage to stages 3 and 4: a classification requiring Level 2 rules out any platform still at Level 1. Replace all of it with your own.

The classifications need a test beside them. Skip it and every team declares its own agent low risk. The test is eight questions. Six measure what happens when the agent is wrong, question 7 asks how much of that happens with nobody watching, and question 8 asks who is on the receiving end. Every answer sets a **floor**, and the agent's classification is the highest floor any single answer sets. Averaging is what that rule exists to stop. Each question carries anchors saying what an answer has to reach to set each floor, because an open question beside a one-line classification is not yet a test.

The [notes](02-policy/risk-classifications-notes.md) cover the floor rule, the narrow escape hatch for compensating controls, the reclassification triggers, and why we do not use an autonomy scale.

## Stage 3: Platform controls, in three levels

**What you write: [Platform Control Levels](03-platform-controls/platform-control-levels.md), a standard, and a [Platform and Sign-off Record](03-platform-controls/platform-and-sign-off-record.md) for each agent.**

Some companies write one platform standard for every agent, and security must approve it before anything ships. Teams then debate the scope for two quarters, and nobody deploys. This stage has to work for one agent, in this sprint, with no company-wide dependency.

It covers the whole setup the agent runs on: the model and its version, the tools it can call, the framework it is built on, where it is hosted, and an agent login. Framework here means the software the agent itself is built on, and not this governance framework. The design document lists the tools and the data that the agent needs, so this stage grants that list and refuses the rest.

Every level requires least privilege. What changes between them is who decides the permissions and what stops them drifting. The three definitions, and the yes/no questions you score yourself against, are in the [standard](03-platform-controls/platform-control-levels.md); read them there rather than from a summary. Level 3 is the full company model, and the point of the ladder is to make it a destination instead of an entry requirement. Plenty of teams will sit at Level 1 for a long time.

Score each platform you run agents on, and state the level actually applied to each agent. Answer honestly. Somebody accepts residual risk on the understanding that a control exists, and a level claimed but not held turns that acceptance into something they did not agree to.

Run your evals against the setup you stood up: this model version, these tools, this framework, this host. An eval that passed against a different configuration tells you about that configuration. Record what they found, what you changed because of it, and what you know you did not test. The person signing off is accepting the first two. The third is where stage 4's monitoring has to begin.

**The step across.** A gate sits between this stage and stage 4. One named person signs off on the agent as a whole: what it is for, its classification, the platform it runs on, what the evals found, and the risk that is left. Record the name, the date, and the versions of both the design document and this record. What they sign off is what the platform enforces, and not a description of it. When live behavior stops matching the description it was granted against, the sign-off is void until somebody looks again.

The [standard](03-platform-controls/platform-control-levels-notes.md) and [record](03-platform-controls/platform-and-sign-off-record-notes.md) notes say where this ladder ends and when to move to the [Cloud Security Alliance's Agentic AI Identity and Access Management](https://cloudsecurityalliance.org/artifacts/agentic-ai-identity-and-access-management-a-new-approach).

## Stage 4: Live operations, from watching to response

**What you write: [Monitoring Levels](04-live-operations/monitoring-levels.md), a standard, and a [Monitoring and Incident Record](04-live-operations/monitoring-and-incident-record.md) for each agent. The first half of that record is the Monitoring Plan, which runs continuously. The second half is the Incident Playbook, which starts when an alert does.**

The Monitoring Plan defines what you record on every run: the tool calls and their arguments, the inputs and the outputs, and enough of the run to replay it. It runs the stage 3 evals without anybody remembering to start them, compares their results against the baseline recorded at sign-off, and says which numbers count as normal and what starts an alert. A failing eval is one of them.

The Incident Playbook defines what happens after an alert: triage, a review of the run record, a fix, and a review after the incident. Write it for the ways that agents fail, and name those ways: tool calls that fail in a chain, prompt injection, quiet scope creep. Ordinary software incident response does not cover any of them.

Monitoring gets its own ladder, because these levels measure what you can see and not what the agent can reach. What changes between them is how much of a run you keep, and whether anything checks it without being asked. The three definitions and their questions are in the [standard](04-live-operations/monitoring-levels.md); read them there rather than from a summary. An agent can sit at platform control Level 3 and monitoring Level 1. State the level each agent is actually on: a sign-off that assumes a monitor which does not exist is worse than one with the limit written on the record.

Stage 4 also corrects stage 3. A monitor reporting a call to a tool outside the declared set has told you that a control you believed you had is not holding.

The [standard](04-live-operations/monitoring-levels-notes.md) and [record](04-live-operations/monitoring-and-incident-record-notes.md) notes cover guardian agents and the two destinations this stage exits to: the [OpenTelemetry semantic conventions for generative AI](https://opentelemetry.io/blog/2026/genai-observability/) for what to record and in what shape, and [OWASP's Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) for what can go wrong.

## Stage 5: Audit and assurance

**What you write: [Audit Log Rules](05-audit-and-assurance/audit-log-rules.md), a standard, and an [Audit and Assurance Record](05-audit-and-assurance/audit-and-assurance-record.md) for each agent.**

Stage 4 records things for debugging. Compliance asks whether you can prove what happened and why, which needs the records held for a period somebody chose on purpose, alterable only in ways that get noticed, and in a form an auditor accepts.

You have a records policy for that already, and this stage does not write a second one. The log rules list what an agent produces that the policy never contemplated, and then say what is different about it: the record is free text rather than fields, re-running the agent does not reproduce the run, the model and tools move underneath the record, the identity in the log is the agent's rather than the person's, and four of the records outlive the agent. Those five differences are the conversation to have with whoever owns retention. Where each row lands, how long it is kept and which regime reaches it are their decisions, and the stage names where log evidence usually already sits instead of deriving a mapping of its own.

The rules govern the first of two records: what the agent did, which decisions it took, and who signed off on it. Most programs can produce something here. The second is the assurance record — where the eval signal comes from, whether it is still arriving, and what somebody concluded from reading it. The first shows what the agent did. The second shows that somebody is still checking, on a date after the sign-off. An auditor will ask for both, and the second is the one most programs cannot produce. It is also the evidence for the loop back to stages 1 and 2: a finding that changes a classification or a design should be traceable to the results that produced it.

Evals that run continuously make that second record harder rather than easier. A monthly schedule fails by stopping, which is visible; a continuous one fails quietly, with green results nobody reads and an eval set that stops growing while the agent changes. So the record holds the reviews rather than the runs, and asks when the eval set was last extended.

The [standard](05-audit-and-assurance/audit-log-rules-notes.md) and [record](05-audit-and-assurance/audit-and-assurance-record-notes.md) notes say when to fold these rules into your existing records-management policy and stop maintaining them separately.
