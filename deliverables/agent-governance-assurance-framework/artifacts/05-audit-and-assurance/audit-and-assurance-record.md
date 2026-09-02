# The Audit and Assurance Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 5 artifact of the [Agent Governance and Assurance Framework](../../README.md). It holds two records. Most organizations already have something like the first. Very few have the second.

Section A is where this agent's records actually go. Section B is where this agent departs from the [Audit Log Rules](audit-log-rules.md), which are written once for every agent. Sections C and D are the **Assurance Record**: what the evals are telling you, who read them, and what changed because of it. Section E is filled in when the agent is switched off.

The first record shows what the agent did. The second shows that somebody is still checking, on a date after the sign-off. An auditor will ask for both.

For the reasoning behind each section, see [the notes on this form](audit-and-assurance-record-notes.md).

**Who fills it in.** The team that runs the agent, for sections A, B and E. Section C belongs to whoever reads the eval results, who may not be the same people. Section D belongs to whoever acted on a finding.

**If you bought the agent rather than built it.** The records still have to exist and you still have to be able to produce them. Where the vendor holds them, name the vendor, say how you obtain a copy and how long they keep it. "We would have to ask" is a gap the sign-off carries.

**This is not the same as stage 4.** Stage 4 records things so an operator can understand what an agent did. This one asks whether you can prove what happened, and why, to somebody who does not trust you: records held for a period somebody chose on purpose, and alterable only in ways that get noticed.

**Section D is the one that carries the framework.** Every arrow that runs back up the five stages is evidenced there, or it did not happen.

---

## The form

### A. Where this agent's records actually go

| Field | Your answer |
|---|---|
| Agent name, and the design document version this serves | |
| Version of this record | |
| Date of this version | |
| Who owns these records | |

The log rules say what happens to each kind of record. This table says whether this agent produces it, and where it ends up.

| What is kept | Is it recorded today | Where it is held | Which rule in the log rules applies | Who can reach or alter it |
|---|---|---|---|---|
| Tool calls and their arguments | | | | |
| Inputs and outputs | | | | |
| The prompt and context of a run | | | | |
| What the agent remembers between runs | | | | |
| Model, tool and prompt versions in play on a run | | | | |
| Escalations and their outcomes | | | | |
| Decisions the agent took alone | | | | |
| Sign-off records | | | | |
| Design document versions | | | | |
| Eval results | | | | |
| Incident records | | | | |

**Where personal data sits in the rows above, and under what basis it is kept.** Name the fields. Free-text inputs and outputs are where it turns up unplanned.

> 

**Whether one person's data can be found and removed from the rows above, and how long that takes.** For records in an append-only store or a trace backend the answer is often no. That is a finding the sign-off carries, not a box to leave blank.

> 

**Which of these rows nothing currently records, and who owns closing that.**

> 

### B. Where this agent departs from the standard

What happens to each kind of record is settled once, for every agent, in the [Audit Log Rules](audit-log-rules.md). Do not restate it here.

This section records only where this agent differs from them.

| Field | Your answer |
|---|---|
| Retention that differs from the rule the standard points at, and who agreed it | |
| Records the standard expects that this agent does not keep, and who accepted that | |
| Records this agent keeps longer than the applicable rule allows, and on what basis | |
| Anything about this agent the standard did not anticipate | |

The last row is the useful one. An agent that does not fit the standard is telling you the standard is short a case, and that belongs in the standard's revision history.

### C. Assurance: the evals, and who reads them

Stage 4 section B says what starts the evals. This section is not a second copy of their output. If they run on every deploy, or continuously against live traffic, the runs live in your eval system and there are thousands of them. What is needed here is where that signal comes from, whether it is still arriving, and what a person concluded from it.

| Field | Your answer |
|---|---|
| Who is accountable for reading these results, by name | |
| Which evals run continuously, and against what traffic | |
| Which run on a deploy, and which on a fixed schedule | |
| Where the results are held | |
| Current results against the baseline recorded at sign-off | |
| What alerts on a regression, and who receives it | |
| How you would know the evals had stopped running | |
| When the eval set was last extended, and what prompted it | |

Running continuously shows the suite still works. It does not show the suite still covers the agent, which is what the last row is for: new tools, new failure modes and new scope need new evals, and an unchanged eval set against a changed agent goes green for the wrong reason.

**The review.** One row per occasion somebody read the results and reached a conclusion. This is the record that shows somebody is still checking.

| Date | What period or runs were reviewed | What the evals covered | What the results showed, and what changed | Who reviewed, and where the evidence is |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |

**The date of the most recent review, and the interval it is meant to run at:**

> 

**Whether the signal is still arriving, and whether that interval is being met.** A stream nobody reads looks identical to a healthy one, and both look identical to a stream that stopped. Say which you have. An assurance record that has gone quiet is itself a finding.

> 

### D. Findings, and what they changed upstream

Every arrow that runs back up the five stages is evidenced here.

| Date | What was found | Which stage it corrects | What changed, and who approved it | Change confirmed live |
|---|---|---|---|---|
| | | 1 / 2 / 3 / 4 / 5 | | |
| | | 1 / 2 / 3 / 4 / 5 | | |
| | | 1 / 2 / 3 / 4 / 5 | | |

Stage 5 is in that list because section B's last row feeds findings back into the [Audit Log Rules](audit-log-rules.md). A standard short a case is a finding like any other.

**Findings raised and not acted on, and why.** A finding that was considered and consciously accepted is a legitimate outcome. A finding that was quietly dropped is not, and the difference is written here.

> 

### E. When this agent is retired

An agent gets switched off long before the questions about it stop arriving. Four kinds of record in section A outlive it: sign-offs, design document versions, eval results and incident records. All four usually sit on infrastructure that is torn down with the agent.

Fill this in when the agent is retired, and not before.

| Field | Your answer |
|---|---|
| Date it was switched off, and who decided | |
| Where its agent login and credentials were revoked, and who confirmed that | |
| Which records in section A were moved, and where they sit now | |
| Who holds them now | |
| Until when, and under which rule | |
| Which records were deleted on purpose, and on what basis | |

**What still points at this agent.** Other agents that called it, processes that assumed it, and reports that read its output. Say what happens to each.

> 

**Who to ask about this agent now.** The owner in section 0 of the design document has probably moved on. Name whoever answers a question about it in three years.

> 

### F. Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |
