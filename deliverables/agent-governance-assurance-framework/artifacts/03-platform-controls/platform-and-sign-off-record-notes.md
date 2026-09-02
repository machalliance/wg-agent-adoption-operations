# Notes on the Platform and Sign-off Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Platform and Sign-off Record](platform-and-sign-off-record.md): why each section is there, where its questions come from, and what we would like your feedback on. You do not need to read it to fill the form in.

---

## Notes on the hard parts

### State the levels you are on, not the levels you intend to reach

The gap between what a framework asks for and what most companies can do today is widest in monitoring. A record that says "monitoring Level 1" is a working document. One that implies Level 3 is a liability.

An agent can sit at platform control Level 3 and monitoring Level 1, and that combination is common: permissions enforced in code, behavior watched by a log nobody reads. The platform control levels are recorded here and the monitoring levels in the [Monitoring and Incident Record](../04-live-operations/monitoring-and-incident-record.md). Record all four, and let the sign-off carry the gap.

OWASP's governance maturity model, in [State of Agentic AI Security and Governance v2.01](https://genai.owasp.org/resource/state-of-agentic-ai-security-and-governance/), puts named accountability and mandatory human review of high-impact decisions at its Level 2, and real-time anomaly detection with working kill switches at Level 3. Most organizations that have written an AI policy are at Level 1.

### Autonomy level is a separate field, not a classification

If you keep an autonomy scale, record it in section A and not as the agent's risk classification. Autonomy is how much the agent does without a person; the classification is how bad it is when the agent is wrong.

The argument for keeping them apart is in [the notes on the Risk Classifications](../02-policy/risk-classifications-notes.md).

### Why section A asks what you granted beyond the design document

"What is granted that the design document does not list" is the only row in this framework where stage 3 can contradict stage 1 in writing, before stage 4 catches the same thing at runtime. Most teams find something the first time they fill it in, usually an inherited role or a credential shared with a service.

Write it down anyway. Recorded now, it is a scoping decision that somebody accepts or refuses at sign-off, and the same discovery after go-live is handled as an incident instead.

---

## Where each section comes from

| Section | Who else asks for it |
|---|---|
| A. The platform it runs on | [Microsoft Entra Agent ID](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview) gives an agent a first-class identity, and [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/foundry/agents/concepts/agent-identity) registers each agent under it so administrators can inventory, apply policy and audit. [AgentCore Identity](https://aws.amazon.com/blogs/machine-learning/secure-ai-agents-with-amazon-bedrock-agentcore-identity-on-amazon-ecs/) does the same on AWS, and [AgentCore Gateway](https://aws.amazon.com/blogs/machine-learning/govern-ai-agent-tool-access-with-amazon-bedrock-agentcore-gateway/) governs tool access on a Connect, Control, Catalog, Harden progression. The [FIDO Alliance's agentic authentication work](https://fidoalliance.org/fido-alliance-to-develop-standards-for-trusted-ai-agent-interactions/) is where the cross-vendor version is being standardized. [OWASP ASI04](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/), agentic supply chain vulnerabilities, is why the framework version and the tool servers belong in this table: an MCP server or a shared connector is a dependency the agent inherits, published by somebody who can change it without telling you. |
| B. What the evals found | AWS [AGENTOPS06](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops06.html) establishes testing and evaluation frameworks because agent behavior is stochastic and deterministic testing alone will not do. [LangSmith](https://docs.langchain.com/langsmith/observability) evaluates against real production traces and turns production failures into regression datasets. [AIUC-1](https://aiuc-1.com/) pairs a governance audit with recurring adversarial testing rather than one annual review. |
| C. Sign-off | OWASP governance maturity Level 2 requires named accountability. EU AI Act [Article 11](https://artificialintelligenceact.eu/article/11/) requires the technical documentation to be drawn up before the system is placed on the market or put into service. [OpenAI's practices for governing agentic AI systems](https://openai.com/index/practices-for-governing-agentic-ai-systems/) argues for agent identifiers carrying the user-principal, so that a human can be held accountable. |
| D. Revision history | AWS [AGENTOPS05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops05.html) (tracing, anomaly detection) and EU AI Act [Annex IV](https://artificialintelligenceact.eu/annex/4/) §9 (the post-market monitoring plan) are what produce the rows. AIUC-1 refreshes the standard quarterly, on the same reasoning. |

## What we want feedback on

1. **Is one record per agent per platform change sustainable?** This document turns over faster than the design document by design. At what point does that become a change log nobody writes.
2. **Does the "granted but not declared" row get filled in honestly?** We expect teams to leave it blank when they should not.
3. **Should the sign-off name a second person for the highest classification?** One named person is deliberate, and it may not survive a critical agent.

[Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues) if you have signed one of these off and something was missing from it.
