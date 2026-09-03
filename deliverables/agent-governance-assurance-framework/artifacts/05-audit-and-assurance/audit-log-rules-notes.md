# Notes on the Audit Log Rules

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Audit Log Rules](audit-log-rules.md): why stage 5 needs a company-level standard at all, what the group is asserting in it, and what we would like your feedback on. You do not need to read it to use the standard.

---

## Notes on the hard parts

### Why this is a standard and not part of the per-agent record

Where each kind of agent record sits in your policy is a company decision. So is which of your existing audits covers what. Neither varies by agent, and a company with forty agents that answered them per agent would hold forty copies that disagreed within two quarters.

What is left for the record is genuinely per agent: where this agent's records actually go, what it does not record, what the evals are saying, and what the findings changed.

### What the group is asserting, and what it is not

Part 1 lists what an agent produces. We can list it because stages 1 to 4 are what produce it.

Part 2 says how those records behave differently from the ones a records policy was written for. Free text where fields were expected, runs that do not reproduce, versions moving underneath a run, an identity in the log that belongs to the agent, and records outliving the agent. Those are observations about agents, and they are what we would defend.

Everything else is a question put to somebody who owns the answer. Retention periods, privacy bases and regime scoping are legal and regulatory decisions, and part 3 names where the evidence usually already sits, instead of deriving a mapping that would disagree with the one your auditor uses.

### Why part 4 tells you to stop using this

Because a records policy that lives beside your real records policy is a liability, and everybody filling this in has a real one.

This standard is a bridge. Its job is to get agent records in front of a policy that never contemplated them, and then to be absorbed. That is a shorter life than the other three standards in the framework have.

---

## Where this comes from

| Part | Who else asks for it |
|---|---|
| Records kept over a system's lifetime | EU AI Act [Article 12](https://artificialintelligenceact.eu/article/12/) is about automatic recording of events over the lifetime of a high-risk system, and [Article 11](https://artificialintelligenceact.eu/article/11/) about keeping the technical documentation current. AWS [AGENTOPS05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops05.html) asks that agent decisions be logged, traced and auditable so a team can reconstruct what happened. |
| Effort proportionate to risk | [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) GV.1.6 asks for an inventory of AI systems resourced according to risk priority. |
| Where log evidence usually already sits | **SOC 2** covers controlled and logged access and change management in its common criteria. **ISO/IEC 27001** covers event logging, log protection and evidence collection in Annex A. Which specific criteria or controls your evidence sits under is a question for whoever produces it. |
| The management-system home this belongs in | **ISO/IEC 42001** is the certifiable AI management system standard, and **ISO/IEC 42006** sets the requirements for bodies that certify against it. **ISO/IEC 23894** and **ISO/IEC 42005** are guidance rather than certifiable. |
| Reusing maps rather than deriving them | [AIUC-1](https://aiuc-1.com/) publishes maps to the NIST AI RMF, ISO 42001, the EU AI Act, MITRE ATLAS and OWASP, and pairs a governance audit with recurring adversarial testing. Log rules built against it inherit those maps. |
| What to record, and in what shape | The [OpenTelemetry semantic conventions for generative AI](https://opentelemetry.io/blog/2026/genai-observability/) define the spans, attributes and events for model calls, tool executions and agent runs. The agent spans are still experimental, so check their status before building against them. |

## What this standard is not

**It is not a records-management policy, and it is not legal advice.** It is a list of what agents add to a policy you already have, and the questions to put to the people who own it. Part 4 says when to fold it in and stop maintaining it separately.

**It is not your log configuration.** If these rules and your actual retention settings disagree, the settings win and this document is wrong rather than aspirational.

## What we want feedback on

1. **Is part 2 the right list?** It is what this document asserts, and anything missing from it is a gap in the argument.
2. **Is part 1 usable with a records owner in the room?** It is a set of questions instead of a table of answers, which makes it a meeting. Tell us if the meeting does not go anywhere.
3. **Is this thin enough to stop being a standard?** It now holds two fill-in tables and a list of pointers. It may belong inside the per-agent record after all, or inside stage 2.
4. **Are the five standards in part 3 the right five?** SOC 2, ISO/IEC 27001, ISO/IEC 42001, the EU AI Act and AIUC-1. We dropped PCI DSS because payment scope is narrower than it first appears for agents.
5. **Is part 4 right that this document should be absorbed?** The other three standards in the framework are meant to last. This one is not, and that may be the wrong call.

If you have taken part 1 to a records owner, we would like to hear how that meeting went. [Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues).
