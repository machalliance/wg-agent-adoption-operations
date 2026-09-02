# Notes on the Agent Design Document

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Agent Design Document](agent-design-document.md): why each section is there, where its questions come from, what it is not, and what we would like your feedback on. You do not need to read it to fill the form in.

---

## Notes on the hard parts

### The outcome, and why it comes first

An agent with no stated outcome and no measure cannot be judged, and you cannot switch it off on evidence. It is usually an agent that exists because agents are available.

This is not a MACH Alliance idea. The AWS Well-Architected Agentic AI Lens opens its operational-excellence pillar with [AGENTOPS01: define agent roles, success criteria, and handoff procedures](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops01.html), in that order. Success criteria and handoff belong to the same question.

The switch-off condition is the part teams skip. Write it now, while you still want the agent to succeed. It gets much harder later.

### The grant list

Section 3 is the only place in the framework where a machine-checkable claim is made. Every other section describes intent, and this one enumerates access. Stage 3 grants from it, stage 4 alerts on calls outside it, and stage 5 keeps it as the record of what was authorized.

So write it at the granularity your platform can actually enforce. "The CRM" is not a row. "Read contact records in region X, write only to the notes field" is a row, because a permission can be shaped like that. If your platform cannot express a row, say so in the enforcement column in section 4, and take the honest answer into section 6.

The reversibility column feeds question 5 of the test, and the Incident Playbook in stage 4 works from it.

### The enforcement column in section 4

"Where is this enforced?" is the column that separates this document from an escalation table. Four teams will answer it four ways for the same-looking agent: one has it in the system prompt, one in a tool wrapper that refuses the call, one in a platform policy the agent cannot reach, and one has it nowhere and has not noticed.

The first three are legitimate answers and carry very different weight in section 6. "Nowhere" is the fourth, and it is most of the reason the column exists: it turns the row above it into a statement of intent, and a reviewer who cannot see that has been told the agent is constrained when it is not. A reviewer needs to see which one you have, so it is a column on every row instead of one question under the table. Vercel's guidance on [guardrails that hold in production](https://vercel.com/i/five-ai-agent-guardrails-production) makes the same distinction: a tool that requires approval before it executes is a different control from an instruction not to call it. Anthropic's agent products default to read-only and require approval before an action modifies anything, which is the same choice made in the tool layer rather than the prompt.

### Why the classifications are not autonomy levels

The classifications measure consequence: how bad it is when the agent is wrong. An autonomy scale measures how much the agent does without a person. The two move independently, so one cannot stand in for the other.

The full argument is in [the notes on the Risk Classifications](../02-policy/risk-classifications-notes.md). Record the autonomy level in the [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md) instead.

### The test, and what it is for

Skip the test and every team declares its own agent low risk.

The highest-floor rule exists because averaging is the failure mode. Take an agent that reads only public data, moves no money, and does one thing you cannot undo. Average the answers and it looks medium risk. The thing you cannot undo is still there.

Questions 1 to 6 test properties of the systems the agent touches. Question 8 tests a property of the audience, and it is there because in practice it changes the answer: the same summarization agent is routine for internal staff and sensitive the moment a customer reads its output as your company's position. Question 7 is not a criterion of its own. It asks how much of the above happens with nobody watching, which is what turns any of it into a risk.

---

## Where each section comes from

Every section of this form answers a question that at least one other credible framework, platform, or standard already asks. This table is here so you can see the overlap, and so you can carry an answer you have already written somewhere else straight into this document.

| Section | Who else asks for it |
|---|---|
| 1. Outcome, measure, owner | AWS Well-Architected Agentic AI Lens, [AGENTOPS01](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops01.html): agent roles, success criteria, handoff procedures. AWS [AGENTOPS06](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops06.html) ties evaluation to whether the agent achieves its intended objective. [Microsoft's Responsible AI Impact Assessment](https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf) opens with intended uses and stakeholders. |
| 2. Purpose and scope | [EU AI Act Annex IV](https://artificialintelligenceact.eu/annex/4/) §1(a) requires the intended purpose with its context and conditions of use. The [A2A Agent Card](https://a2a-protocol.org/latest/specification/) carries `name`, `description`, `version` and `skills` for the machine-readable version of the same thing. |
| 3. Tools and data | AWS [AGENTSEC03](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentsec03.html) (agent identity, least-privilege access) and [AGENTREL02](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentrel02.html) (atomic tasks, least-privilege permissions). [Amazon Bedrock AgentCore Gateway](https://aws.amazon.com/blogs/machine-learning/govern-ai-agent-tool-access-with-amazon-bedrock-agentcore-gateway/) governs tool access on a Connect, Control, Catalog, Harden progression, and AgentCore Policy expresses it in [Cedar](https://aws.amazon.com/blogs/machine-learning/control-agent-behaviors-and-cost-beyond-a-single-action-new-capabilities-in-amazon-bedrock-agentcore/). Google's [approach for secure AI agents](https://research.google/pubs/an-introduction-to-googles-approach-for-secure-ai-agents/) requires that agent powers be carefully limited. [OWASP ASI02 Tool Misuse and ASI03 Identity and Privilege Abuse](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) are what this table is defending against. |
| 4. What it decides alone | Google's three principles require well-defined human controllers with explicit confirmation for critical or irreversible actions. AWS [AGENTSEC04](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentsec04.html) pairs guardrails with human-in-the-loop for critical decisions. [Vercel's five guardrails](https://vercel.com/i/five-ai-agent-guardrails-production) name approval gates and tool scoping as runtime controls, not instructions. [Anthropic's framework for safe and trustworthy agents](https://www.anthropic.com/news/our-framework-for-developing-safe-and-trustworthy-agents) puts keeping humans in control first among five commitments. EU AI Act Annex IV §2(e) and §3 require an assessment of the human oversight measures needed under Article 14. |
| 5. Escalation and override | AWS [AGENTSEC07](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentsec07.html): protect human oversight and detect rogue agents. OWASP's governance maturity Level 3 requires working kill switches, and [ASI10 Rogue Agents](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) is the risk. Anthropic's second commitment, transparency in agent behavior, is what makes an override decision possible in time. |
| 6. Classification and the test | The [CSA Agentic AI profile for the NIST AI RMF](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/) supplies autonomy tiers and requires that authority held, tools reached, and revocation timing be tracked per agent. [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) GV.1.6 requires an inventory of AI systems resourced according to risk priority. [AIUC-1](https://aiuc-1.com/) certifies against 51 requirements over data and privacy, security, safety, reliability, accountability and society. OWASP's maturity model pairs an adoption tier with a governance-maturity level, which is the same move as pairing a classification with your platform control level. |
| 7. Revision history | AWS [AGENTOPS05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops05.html) (tracing, anomaly detection) and Annex IV §9 (the post-market monitoring plan) are what produce the rows. AIUC-1 refreshes the standard quarterly, on the same reasoning. |

## What this document is not

**It is not an A2A Agent Card.** The [A2A specification](https://a2a-protocol.org/latest/specification/) v1.0.0 defines an `AgentCard` with `id`, `name`, `description`, `provider`, `capabilities`, `skills`, `interfaces`, `securitySchemes`, `extensions` and `signature`. It is a discovery and interoperability manifest: it tells another agent what this one can do and how to authenticate to it. It has no field for the accountable person, the risk classification, the approval, the sensitivity of the data reached, or the escalation path. [Google Cloud's Agent Registry schemas](https://docs.cloud.google.com/agent-registry/json-schemas) follow the Agent Card shape and inherit the same omissions.

A2A is solving a different problem, so those omissions are deliberate. They are also why this document exists. Sections 0, 6 and 7 here, and the sign-off in the platform record, are the governance metadata the machine-readable manifests leave out. Sections 2 and 3 overlap with them enough that you should generate one from the other instead of maintaining both by hand.

**It is not a model card or a system card.** Those describe a model: its training data, its benchmarks, its known limitations. Anthropic's [system cards](https://www.anthropic.com/news/our-framework-for-developing-safe-and-trustworthy-agents) and the equivalents from other labs cover the model you build on. This document covers the behavior and the authority of one agent you built, and the [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md) is where it points at the model card of the model underneath.

**It is not the first proposal of its kind.** It is the first with a standards body behind it. Two prior efforts reached a similar conclusion, and neither has institutional backing. [Agent Cards: A Documentation Standard for Operational AI Agents](https://link.springer.com/chapter/10.1007/978-3-032-17933-3_25) (MICAI 2025 workshops, Springer) is a peer-reviewed workshop proposal covering roles, memory, tools, protocols, monitoring hooks, governance scope and evaluation metrics. [Agent Manifest](https://agent-manifest-spec.org/) is a single-author specification, published across five repositories with one contributor and no adopters at the time of writing.

We record them because they show the gap is real and independently felt. Neither constrains this work. Neither carries a classification argument, and neither has a governing body that could maintain it. That is the difference this framework is trying to make: a document of this kind is only useful if somebody is still revising it in three years.

**It is not an agent registry entry.** A registry entry is the index: one row per agent, held centrally, for discovery and inventory. This is the document the row points at. The commercial platforms are converging on requiring the former before production, which is a good pattern to copy: no registry entry, no deployment.

## If you have EU AI Act duties

We do not print the compliance dates. They have moved more than once, the Annex III deadline moved separately from the Article 50 transparency duties, and anything we printed here would be wrong within a quarter. Check the current dates at [artificialintelligenceact.eu](https://artificialintelligenceact.eu/) or with your counsel.

Two parts of the Act reach an agent, and they are on different clocks:

- **Article 11 and Annex IV technical documentation**, for systems that are high-risk under Annex III. This is the part this form holds most of the material for.
- **Article 50 transparency duties**, about telling a person they are dealing with an AI system. Section 2 of this form asks who is on the other end and whether they are told, which is where that answer belongs.

If an agent of yours falls in scope of Annex III, this document is not the Article 11 technical documentation, but it holds much of the material Annex IV asks for, and it holds it per agent rather than per company.

| This document | Annex IV |
|---|---|
| 2. Purpose and scope | §1(a) intended purpose, with context and conditions of use |
| 4. What it decides alone, 5. Escalation and override | §2(e) and §3, the human oversight measures needed under Article 14 |
| The Platform and Sign-off Record, section A | §1, the general description of the system and its versions |
| The Platform and Sign-off Record, section B | §3, performance capabilities and their limits |
| 7. Revision history, and stage 4's Monitoring Plan | §9, the post-market monitoring plan under Article 72 |

Small and medium enterprises may supply the Annex IV elements in a simplified form. Whether this document is enough of that simplified form is a question for your counsel, and one the working group would like to hear the answer to.

## What we want feedback on

1. **Is section 6 the right test?** Eight questions, highest floor wins. Too many, too few, or the wrong ones. Question 8 in particular is an addition beyond the six criteria in the five stages, and it may belong in stage 2 instead.
2. **Is the highest-floor rule usable, or will teams route around it?** The escape hatch is the naming of a compensating control, and we are not sure it is tight enough.
3. **Does section 3 survive contact with your platform?** Specifically, whether you can write rows at a granularity your permission system can actually enforce.
4. **Is splitting the platform record out the right call?** It is separate so that a model upgrade does not void a design sign-off. The cost is two files per agent at Level 1, which is friction the framework elsewhere tries to avoid.
5. **Would you generate this from an Agent Card, or the Agent Card from this?** If the machine-readable manifest is the source of truth in your stack, the overlap in sections 2 and 3 should be generated and not typed.

This is the form most teams will meet first, so it is the one we most want broken. [Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues).
