# Notes on the Audit and Assurance Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Audit and Assurance Record](audit-and-assurance-record.md): why it is separate from stage 4, why section C records reviews and not runs, and what we would like your feedback on. You do not need to read it to fill the form in.

---

## Notes on the hard parts

### Why this is separate from stage 4

Stage 4 and stage 5 draw on the same underlying records and ask different questions of them.

An operator asks: what did the agent do, so I can fix this. They need depth, speed, and the freedom to add a log line this afternoon. A short retention period is fine.

An auditor asks: can you prove what happened, and why, without my having to trust you. They need the record fixed, complete for a period somebody chose on purpose, and alterable only in ways that get noticed. A log the operating team can edit is not evidence, however good it is for debugging.

Those requirements conflict. Keeping them in one document produces a logging policy that satisfies neither, which is why they are two stages.

### Why section A does not ask for retention periods

An agent team is not a retention authority, and asking it for a period produces either a guess or a copy of whatever the last team wrote. The period comes from the rule the [Audit Log Rules](audit-log-rules.md) point at, and section A just names which rule that is.

What it asks instead is local: does this agent produce this kind of record, where does it end up, and who can reach or alter it. Those are answers an agent team has and nobody else does. The last of them is the one an auditor asks first, because a log the operating team can edit is useful for debugging and is not evidence.

The row asking what nothing currently records is the one to fill in honestly. A blank read as "yes, we have that" is worse than a stated gap with a name against it.

### Why section A asks for the versions in play on a run

A model version, a tool, a retrieved document or a system prompt can change without anything in the agent's code changing.

A run record that captures the inputs and outputs but not what sat underneath them cannot be tied back to what was signed off. The gap is invisible until somebody tries to use the record.

### Why section B is only departures

What happens to each kind of record is settled once in the standard. Restating it per agent produces forty copies that disagree within two quarters. That is why the framework separates standards from records everywhere else.

So section B holds only the difference. Its last row is the one that feeds back: an agent the standard did not anticipate is telling you the standard is short a case.

### Why the form names no regimes

Which regimes reach you depends on where you operate and what industry you are in. A Canadian retailer, a German bank and a US health insurer share almost none of their obligations, and a form anchored on any one of them tells most readers that this is not about them. The standard's part 3 names the ones you may already hold and leaves the scoping question with whoever owns it at your company.

### Why the assurance record is the harder of the two

Most organizations can produce something for section A. It is the record their existing logging already wanted to be, and an audit function knows how to ask for it.

Section C is different. It requires that the evals kept running, that somebody read what they were saying, and that the reading is written down with a date after the sign-off. Nothing about existing logging produces that, and no tool creates it as a side effect. It has to be somebody's job.

It is also the only evidence that the framework is running rather than merely written, because a sign-off only shows that somebody accepted the risk on one date.

### Why section C records reviews and not runs

One row per run works for evals that fire monthly and breaks for everything else. Evals increasingly run on every deploy, or continuously against a sample of live traffic, and a per-run table then either fills with thousands of rows or gets summarized by hand into something less trustworthy than the eval system it was copied from.

So the runs stay where they are produced, and section C holds three things a run log does not: where the signal comes from, whether it is still arriving, and what a person concluded from it.

Continuous evals also move the failure mode. A monthly schedule fails visibly, by stopping. A continuous one fails quietly: results stay green, nobody reads them, and the suite stops being extended while the agent keeps changing. Green against a stale eval set is the harder failure to see, which is why the section asks when the set was last extended and what prompted it.

### Why section D separates "accepted" from "dropped"

A finding that was considered and consciously accepted is a normal outcome of a working process. Someone weighed it and decided.

A finding that quietly disappeared is the opposite, and from the outside the two are indistinguishable unless somebody wrote down which happened. That distinction is most of what an assurance process is for, and it is one line in a table.

### Why "is the change confirmed live" is a column

A finding that produced a document change and no behavior change is still open, whatever the ticket says. The column exists because closing tickets is easier than changing systems, and an auditor who finds that gap will discount everything else in the record.

---

## Where each section comes from

| Section | Who else asks for it |
|---|---|
| A. Where this agent's records go | EU AI Act [Article 12](https://artificialintelligenceact.eu/article/12/) is about automatic recording of events over the lifetime of a high-risk system, and [Article 11](https://artificialintelligenceact.eu/article/11/) about keeping the technical documentation current. AWS [AGENTOPS05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops05.html) asks that agent decisions be logged, traced and auditable so a team can reconstruct what happened. |
| B. Departures from the standard | The standard's part 1 places agent records against the policy you already have, and its part 3 names the standards that policy was probably built for. |
| C. Assurance: the evals, and who reads them | [AIUC-1](https://aiuc-1.com/) pairs a governance audit with recurring adversarial testing, not one annual review, and refreshes the standard quarterly. The [Cloud Security Alliance's agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/) for the NIST AI RMF asks that the authority an agent holds be reviewed, and names when it should be revoked. |
| D. Findings, and what they changed | [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) is built as four functions that feed each other rather than a sequence, and MANAGE is where findings return to GOVERN and MAP. OWASP's [State of Agentic AI Security and Governance v2.01](https://genai.owasp.org/resource/state-of-agentic-ai-security-and-governance/) puts telemetry and red-team findings automatically tuning guardrails at its highest maturity level. |

## What this record is not

**It is not a certification.** [ISO/IEC 42001](https://www.iso.org/standard/81230.html) and AIUC-1 have audit processes behind them and this framework does not. What this form produces is evidence a certifier would have asked for anyway, in a shape you can hand over.

**It is not your log store.** Section A describes where records go, not a schema. If it and your actual configuration disagree, the configuration wins, and this document is wrong rather than aspirational.

## What we want feedback on

1. **Is the operator-versus-auditor split the right line?** It is the line we drew between stages 4 and 5. In a single logging pipeline it may be a line nobody can hold.
2. **Is section A now too thin?** It states where records go and who can touch them, and points at the standard for everything else. What is left may not make a team think as hard.
3. **Should section C be per agent or per company?** We made it per agent, which is consistent with the rest of the framework but means a company with forty agents keeps forty assurance records. A single register with an agent column may be more honest about how this gets operated.
4. **Is "is the change confirmed live" answerable?** It is the column we most want and the one most likely to be filled in optimistically.
5. **What does a review interval look like for continuous evals?** The form asks for one and does not suggest a number. If you run evals continuously, tell us how often a person actually reads them and what triggers a closer look.
6. **Does anyone actually have a working assurance record today?** We have asserted that this is the record that usually does not exist. If you have one, the group would like to see its shape.

[Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues) on the part you disagree with.
