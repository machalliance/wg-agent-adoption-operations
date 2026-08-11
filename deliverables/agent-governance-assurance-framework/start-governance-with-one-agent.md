# Start Governance with One Agent, Not the Whole Enterprise

*A draft five-layer framework from the MACH Alliance Agent Adoption & Operations Working Group*

Most enterprises with an AI governance policy could not pick one agent in production and show that its behavior matches it.

The usual approach guarantees that. Agent governance gets scoped as an enterprise program: one permission and access-control standard, covering every agent, agreed by every team that owns one. That agreement can take longer than the agents take to reach production. Teams ship in the meantime, on shared credentials, with no record of what an agent decided or why.

The MACH Alliance [Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations) has published a [draft structure](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/agent-governance-assurance-framework) built the other way round, scoped so a team can govern one agent in a sprint without waiting for a standard that covers all of them.

## The layers hold each other up

A governance claim made in policy is only true if the platform enforces it, the agent's design reflects it, someone accountable has accepted it, runtime behavior confirms it, and the audit record proves it. Break any one of those links and every layer above it is an empty assertion. So the draft organizes the work as five connected layers rather than five documents that never reference each other.

| Layer | Primary artifact | What it does |
|---|---|---|
| 1. Enterprise policy | Risk Classification Model + Diagnostic Rubric | Defines risk tiers and a repeatable way to place any agent in one |
| 2. Platform enforcement | Permission & Access Control Maturity Ladder | Turns tiers into enforceable controls, deployable per agent |
| 3. Agent design | Per-Agent Design & Classification Dossier | Documents one agent's purpose, tools, data access, oversight design, and its evidence for the tier it claims. An accountable owner accepts the residual risk and authorizes operation before it goes live |
| 4. Runtime operations | Observability & Alerting Spec + Incident Response Playbook | Checks live behavior against the dossier, and responds when an alert fires |
| 5. Audit & assurance | Audit Trail & Compliance Logging Specification | Produces retained, tamper-evident proof mapped to SOC 2, ISO 27001, and EU AI Act obligations |

Layer 5 feeds back into Layer 1. Audit findings revise the tiers and thresholds they were built to satisfy, and without that return path the tiers stay as first written while the agents keep changing. The full reasoning is in the [layered model write-up](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/agent-governance-layered-model.md), which also sets out where the draft leans on existing work instead of restating it, including [AI TRiSM](https://www.gartner.com/en/articles/ai-governance-trism), [AIUC-1](https://aiuc-1.com/), the [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) and the Cloud Security Alliance's [agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/), ISO/IEC 42001, and [FIDO's agentic authentication work](https://fidoalliance.org/fido-alliance-to-develop-standards-for-trusted-ai-agent-interactions/).

## Three ideas doing the heavy lifting

Layer 2 is built as a ladder. Its bottom rung is reachable this sprint for a single agent: a service identity that is not shared with anything else, credentials scoped to only that agent's tools and data, and a documented way to revoke them. Higher rungs tie credential scope to the agent's risk tier automatically, then to policy-as-code. The full enterprise model sits at the top of the ladder instead of at the entrance.

Layer 4's monitoring gets the same treatment, because this is where the gap between what a framework asks for and what most organizations can do today is widest. A baseline worth having is narrow: log every tool call and its arguments, retain inputs and outputs for a bounded window, and alert on a few coarse signals such as calls to tools outside the agent's declared set. Trace-level reasoning capture, replay, and scheduled evaluation are the destination, not the entry price.

Layer 1 needs more than a tier list. It needs a diagnostic, so someone can walk through a procedure and justify why a given agent is Tier 2 and not Tier 1 or 3, judged on data sensitivity, financial exposure, reversibility, and blast radius. Skip that and every team declares its own agent low risk, and now there is a document asserting the risk was assessed. Tiers also drift. A model update or a new tool grant can push real behavior above what the paperwork claims, which is why the diagnostic has to be re-run against what monitoring sees.

Layer 3 answers that diagnostic with one agent's specifics rather than in the abstract, which is what makes the dossier more than a design template: it carries its own tier justification, and it is the document a reviewer reads to decide whether the agent is what it claims to be. Nothing crosses into production on the strength of that claim alone. A named person accepts the residual risk and authorizes operation, on a recorded date, against a specific version of the dossier. That authorization is provisional, and the distinction matters: when runtime behavior stops matching the description it was granted against, the acceptance is not merely stale, it is void until someone reconsiders it. Without that, the runtime feedback loop is informational.

## Fill this in with us

The structure is public so it can be argued with while arguing is still cheap. Tell us whether five layers are the right five, whether one is missing, and whether something sits in the wrong place.

The bigger invitation is the drafting. All five artifacts still have to be written, and the group would like the people who will have to operate them in the room while that happens. If you are scoping permission boundaries for an agent this quarter, or arguing with an auditor about what an agent's log has to contain, we would love to have you join the group.

Read the [layered model](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/agent-governance-layered-model.md), then [open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues) on the part you disagree with. The charter, minutes, and deliverables are all in the open, and the group meets bi-weekly.

Members of the working group will be at [MACH X: Amsterdam](https://mach-x.machalliance.org/amsterdam/) on September 29 and 30. We would love to meet with you there.

---

*The Agent Adoption & Operations Working Group is part of the MACH Alliance [Agent Ecosystem](https://github.com/machalliance/agent-ecosystem) initiative. Its earlier three-part position paper, [What Changed](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/what-changed-articles), argues that frameworks are the organizational mechanism for scaling the mental model shift agentic systems require.*
