# Agent Governance & Assurance Framework

A working framework for governing, securing, and maintaining compliance for AI agents in
production. Developed in the context of the [MACH Alliance](https://machalliance.org)
[Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations).

## Goal

We want to give MACH Alliance end users and members guidance they can pick up and
implement, one agent at a time. Abstract principles documents already exist. This is a
structure.

The working group's charter proposes six artifacts spanning adoption, operating model,
governance, production readiness, operations, and observability. Three of them cover
governance, safety, and compliance. This repository organizes those three as five
interlocking layers instead of a flat list of deliverables. The layering is the point: a
governance claim made at the policy level is only true if the platform enforces it, the
agent's design reflects it, runtime behavior confirms it, and the audit record proves it.
Break any link and every layer above it is an assertion.

## The model

![Flow diagram titled "Agent Governance, Safety and Compliance: A Layered Model". Five boxes are stacked in a single column, shaded from light blue at the top to dark navy at the bottom, each connected by a downward arrow to the one below it. From top to bottom they are Layer 1, Enterprise Policy and Risk Classification; Layer 2, Permission and Access Control Maturity Ladder; Layer 3, Agent Design and Classification Dossier; Layer 4, Runtime Operations; and Layer 5, Audit Trail and Compliance Assurance. The table below this figure gives the contents of each box. A single orange line runs up the right-hand side from Layer 5 to an arrowhead at Layer 1, labelled "Audit findings revise risk tiers and enforcement thresholds".](layered_model.png)

| Layer | Primary artifact | What it does |
|---|---|---|
| 1. Enterprise Policy | Risk Classification Model + Diagnostic Rubric | Defines risk tiers and a repeatable way to place any agent into one |
| 2. Platform Enforcement | Permission & Access Control Maturity Ladder | Turns tiers into enforceable controls, deployable incrementally per agent |
| 3. Agent Design | Per-Agent Design & Classification Dossier | Documents one agent's purpose, tools, data access, oversight design, and its evidence for its claimed tier |
| 4. Runtime Operations | Observability & Alerting Spec + Incident Response Playbook | Continuously checks live behavior against the dossier; responds when an alert fires |
| 5. Audit & Assurance | Audit Trail & Compliance Logging Specification | Produces immutable, retained evidence mapped to SOC 2 / ISO 27001 / EU AI Act obligations. Findings loop back to revise Layer 1 |

The full write-up is in
[`agent-governance-layered-model.md`](agent-governance-layered-model.md). It covers the
reasoning behind each layer, a mapping to the working group's charter, and a suggested
incremental rollout plan.

## Relationship to other frameworks and standards

This framework does not start from a blank page. Several organizations are converging
independently on similar structures for agent governance. Where their work already covers
something well, we reference it and build on it instead of inventing competing vocabulary.

We add three things that existing work does not cover: a diagnostic procedure for placing
an agent into a risk tier, an incremental rollout path for permission enforcement in place
of an all-or-nothing enterprise mandate, and a per-agent design dossier that carries its
own tier justification. Each is flagged as ours where it appears.

Related work worth reading alongside this framework:

- **[Gartner AI TRiSM](https://www.gartner.com/en/articles/ai-governance-trism)**:
  Trust, Risk, and Security Management, covering AI Governance, Runtime Inspection &
  Enforcement, Information Governance, and Infrastructure & Stack. The closest parallel to
  Layers 1, 4, and 2 of this model.
- **[Gartner Market Guide for Guardian Agents](https://www.gartner.com/en/newsroom/press-releases/2026-04-28-gartner-identifies-six-steps-to-manage-artificial-intelligence-agent-sprawl)**:
  an emerging vendor category for independent oversight layers that supervise other
  agents, covering visibility & traceability, continuous assurance, and runtime inspection
  & enforcement. A parallel to Layer 4.
- **[AIUC-1](https://aiuc-1.com/)**: a certifiable agent standard published by the AIUC-1
  Consortium, covering data & privacy, security, safety, reliability, accountability, and
  society, with third-party audit and published crosswalks to NIST AI RMF, ISO 42001, the
  EU AI Act, MITRE ATLAS, and OWASP. It spans Layers 1 through 5 as certification criteria;
  this framework differs in being an operating structure rather than a conformance target.
- **[NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)**,
  extended by the **[Cloud Security Alliance's Agentic AI Profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/)**:
  a four-function (Govern/Map/Measure/Manage) extension with agent-specific categories. Its
  four-tier autonomy classification system parallels Layer 1, and its runtime behavioral
  telemetry and autonomy calibration parallel Layer 4's feedback into Layer 1.
- **ISO/IEC 42001**: the certifiable AI management system standard, and the natural
  counterpart to Layer 5's audit obligations.
- **[FIDO Alliance, Agentic Authentication Technical Working Group](https://fidoalliance.org/fido-alliance-to-develop-standards-for-trusted-ai-agent-interactions/)**:
  cross-vendor standards for agent identity, delegation, and authorization. A narrower,
  standards-body counterpart to Layer 2.
- **[ASG-WG](https://www.asg-wg.org/)** and the **[WEF AI Governance Alliance](https://www.deepinspect.ai/blog/ai-governance-alliance)**:
  peer multi-stakeholder efforts operating at a similar altitude to this working group.

## Status

Draft, under active discussion within the MACH Alliance Agent Adoption & Operations
Working Group. Feedback and contributions are welcome. Please open an issue or pull
request.
