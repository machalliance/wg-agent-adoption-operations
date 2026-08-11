# Agent Governance, Safety & Compliance: A Layered Model

*Working document of the MACH Alliance Agent Adoption & Operations Working Group. Draft prepared August 2026, for discussion.*

## Purpose

The working group's charter proposes six artifacts spanning adoption, operating model, governance, production readiness, operations, and observability. Three of them cover governance, safety, and compliance. Written as separate documents, the connections between them are easy to lose.

This document proposes organizing that work as five interlocking layers instead of a flat list of deliverables. Governance for agentic systems holds together only when policy, technical enforcement, per-agent design, runtime operation, and audit evidence form a connected loop. Each layer depends on the layer above it being true. The evidence produced at the bottom has to climb back up and correct the top.

## The model at a glance

![Flow diagram titled "Agent Governance, Safety and Compliance: A Layered Model", from the MACH Alliance Agent Adoption and Operations Working Group. Five boxes are stacked in a single column, shaded from light blue at the top to dark navy at the bottom. From top to bottom they are Layer 1, Enterprise Policy and Risk Classification; Layer 2, Permission and Access Control Maturity Ladder; Layer 3, Agent Design and Classification Dossier; Layer 4, Runtime Operations; and Layer 5, Audit Trail and Compliance Assurance. Each box names its primary artifact and summarizes what the layer does; the table below this figure repeats that content. Grey arrows connect each box down to the next, labelled in order: "tiers set enforcement requirements", "controls are scoped per agent", "dossier claims go live", and "telemetry becomes evidence". The Layer 4 box is divided by a horizontal rule into two halves, Continuous above and Triggered below. A single orange line runs down the right-hand side of the diagram, leaving the Layer 5 box at the bottom and arriving as an arrowhead at the Layer 1 box at the top; it is labelled "Audit findings revise risk tiers and enforcement thresholds".](layered_model.png)

*Figure 1. The five-layer governance loop. Blue arrows show the cascade from policy down to operations; the orange loop shows assurance evidence feeding back up to revise policy.*

| Layer | Primary artifact | What it does | Feeds into |
|---|---|---|---|
| 1. Enterprise Policy | Risk Classification Model + Diagnostic Rubric | Defines risk tiers and a repeatable way to place any agent into one. | Sets enforcement requirements for Layer 2. |
| 2. Platform Enforcement | Permission & Access Control Maturity Ladder | Turns tiers into enforceable, incrementally deployable controls. | Scopes what each agent in Layer 3 is technically permitted to do. |
| 3. Agent Design | Per-Agent Design & Classification Dossier | Documents one agent's purpose, tools, data access, oversight design, and its evidence for its claimed tier. | Its claims go live and become what Layer 4 watches. |
| 4. Runtime Operations | Observability & Alerting Spec + Incident Response Playbook | Continuously checks live behavior against the dossier; responds when an alert fires. | Telemetry becomes the evidence Layer 5 relies on. |
| 5. Audit & Assurance | Audit Trail & Compliance Logging Specification | Produces immutable, retained evidence mapped to SOC 2 / ISO 27001 / EU AI Act obligations. | Findings loop back to revise Layer 1's tiers and thresholds. |

## The five layers

### Layer 1: Enterprise policy & risk classification

**Primary artifact: Risk Classification Model + Diagnostic Rubric.**

A tier list works only if it comes with two things: a repeatable way to place a given agent into one of its tiers, and a description of what each tier's behavior looks like in practice, not just its criteria on paper.

So this layer has two parts. The first is the rubric itself, with criteria such as data sensitivity, financial exposure, reversibility of actions, and blast radius. The second is a diagnostic procedure: a structured set of questions or tests someone can walk through to determine, and justify, why a given agent is Tier 2 and not Tier 1 or Tier 3. Without the diagnostic, every team self-declares its agent low-risk to avoid scrutiny, which defeats the purpose of having tiers.

Declared tier and observed behavior also drift apart over time. A model update, a new tool grant, or a prompt change can push real-world behavior into a higher tier than the paperwork claims. So the diagnostic cannot be a one-time, design-time exercise. It has to be re-checked periodically against what Layer 4 observes.

### Layer 2: Platform enforcement, as a maturity ladder

**Primary artifact: Permission & Access Control Maturity Ladder.**

An enterprise-wide permission and access-control standard, written as a single document that security has to bless before anything ships, gets scoped, debated for two quarters, and never deployed. For this layer to be real, it has to be adoptable for one agent, this sprint, with no enterprise-wide dependency.

The fix is a maturity ladder. Its baseline level is achievable immediately, per agent: a named service identity that is not shared, credentials scoped to only the tools and data that one agent needs, and a manual revocation process. A middle level ties credential scope automatically to the agent's Layer 1 tier, so policy narrows a higher-tier agent's permissions instead of an engineer's judgment call. A mature level adds policy-as-code, automated provisioning and revocation, and continuous verification that granted permissions still match the declared tier. That mature level is the full enterprise model, but the ladder makes it a destination rather than a prerequisite for starting.

### Layer 3: Agent design & classification dossier

**Primary artifact: Per-Agent Design Dossier, a system card for the agent.**

A human-oversight-and-escalation matrix answers what to do when something goes wrong. It does not answer how anyone knows this specific agent belongs in the tier it claims. Those two things belong in the same document, because the escalation design depends on the tier claim being true.

This layer is one document per agent, produced before it goes near production. It covers the agent's purpose and scope, the tools and data it can touch, its decision authority (what it can do without a human, and what it cannot), its escalation and override design, and the evidence and reasoning for why this agent sits at the tier claimed in Layer 1.

That last section carries the most weight. It answers Layer 1's diagnostic with this agent's specifics instead of in the abstract. The dossier is close in spirit to a model or system card, scoped to an agent's behavior and authority instead of a model's training data and benchmarks. The nearest counterpart in existing standards is [AIUC-1](https://aiuc-1.com/)'s accountability requirements for compliance documentation and failure planning, which sit at the level of an organization's conformance; the dossier is per-agent and carries its own tier justification. It is the document a reviewer reads to decide whether the agent is what it claims to be.

### Layer 4: Runtime operations, from observation to response

**Primary artifacts: Observability & Alerting Specification (continuous) and Incident Response & Post-Mortem Template (triggered).**

This layer is two connected loops. The continuous loop defines what telemetry is captured on every run (decision traces, tool calls, inputs and outputs), what evaluations run on a schedule against known failure modes, what thresholds define normal, and what triggers an alert. The triggered loop is what happens once an alert fires: triage, review of the decision trace, remediation, and a post-incident review. Adapt that second loop to agent-specific failure modes such as cascading tool-call errors, prompt injection, and silent scope creep. Do not borrow it wholesale from traditional software incident response.

The continuous loop is also the mechanism that re-verifies Layers 1 and 3 over time. If an agent's live behavior starts touching more sensitive data or taking less reversible actions than its dossier claims, that should surface as a monitoring signal within days. Six months later, during an audit, is too late.

### Layer 5: Audit & compliance assurance

**Primary artifact: Audit Trail & Compliance Logging Specification.**

Layer 4's observability is scoped for debugging: decision traces and tool usage that help an operator understand what an agent did. Compliance has different requirements: immutability, defined retention periods, tamper-evidence, and mapping to existing frameworks such as SOC 2, ISO 27001, and the EU AI Act's logging obligations for higher-risk systems. [AIUC-1](https://aiuc-1.com/)'s accountability domain covers the same ground for agents specifically, and its published crosswalks to NIST AI RMF, ISO 42001, the EU AI Act, and MITRE ATLAS mean a log specification built against it inherits those mappings instead of re-deriving them. This layer keeps the debugging question separate from the question an auditor asks, which is whether you can prove what happened and why. Both draw on overlapping telemetry, but they are not the same artifact.

The loop closes here: this layer's findings should periodically revise Layer 1's risk tiers and thresholds. Without that feedback path, governance stays fixed on paper while the agents it is meant to govern keep changing underneath it.

## A path to deliver this incrementally

A five-layer governance system sounds like a multi-quarter enterprise program, and programs like that tend not to ship. This model has to answer that concern. The layers are designed so a narrow, end-to-end version can exist quickly, with maturity added layer by layer afterward. No layer has to be complete before any of it is real.

A reasonable first pass: pick one or two pilot agents already in flight. Write their Layer 1 tier and diagnostic answer and their Layer 3 dossier first. Both are documentation work with no platform dependency. Apply Layer 2's baseline controls, a named identity and scoped credentials, to those same agents. Stand up Layer 4's continuous loop for just those agents, even a minimal one that logs decision traces and a handful of alert thresholds. Add Layer 5's logging specification once there is real telemetry to retain.

Generalizing Layer 2 toward automated, tier-linked provisioning and eventually policy-as-code comes after that narrow slice works end to end. By then the working group is scaling something proven instead of designing something that has never been deployed.
