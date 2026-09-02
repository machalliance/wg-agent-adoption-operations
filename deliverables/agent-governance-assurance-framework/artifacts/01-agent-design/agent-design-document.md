# The Agent Design Document

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 1 artifact of the [Agent Governance and Assurance Framework](../../README.md). It is one document for one agent, and it is the document a team touches first.

You write it before the agent goes near production. It records what the agent is for, what it can touch, what it decides alone, and which risk classification it belongs to. Stage 3 grants exactly the access this document lists. Stage 4 checks live behavior against what this document claims. Stage 5 keeps it as evidence.

Three people read it. The person who signs the agent off, to decide whether the risk is acceptable. Whoever configures the platform, who needs section 3 to know what to grant. An auditor, later, to find out what was authorized and by whom.

The sections run description first and classification last, because nobody can classify an agent until somebody has written down what it does. Expect the answers to go out of date: one more tool, a widened scope or a new audience all change them, so record the date you last revised it in section 7.

For the reasoning behind each section, and where its questions come from, see [the notes on this form](agent-design-document-notes.md).

**Who fills it in.** The team that builds the agent, not a risk function.

**If you bought the agent rather than built it.** Most of what a vendor ships is a product decision you cannot change, and none of that moves the accountability: inside your company, this agent is yours. Fill in sections 1, 2, 4 and 5 as normal, from the configuration you chose and the work you pointed it at. Write section 3 from what you actually connected it to, and where the vendor will not say what it reaches or what runs underneath, write "not disclosed by the vendor" instead of guessing. That answer is a finding, not a gap in the form, and the person signing off in stage 3 has to see it.

**Fill it in badly rather than not at all.** A document with five honest gaps and a named owner is worth more than a complete one written to pass a review. Write "not known" where that is the answer, and the gap becomes work instead of a false claim.

**The platform, the evals and the sign-off are not in here.** They live in the [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md), one per agent, versioned separately. They have to be, because a sign-off is granted against a version: if a model upgrade bumped this document's version, it would void a sign-off on a design that had not changed.

---

## The form

### 0. The agent

| Field | Your answer |
|---|---|
| Name | |
| Identifier, if your agent registry gives it one | |
| Version of this document | |
| Date of this version | |
| Owner: the person accountable for this agent | |
| Team | |
| Status: in design, in review, live, retired | |

### 1. The outcome

**What is this agent for?** One or two sentences, stating the result the business wants and not the technique.

> 

**How do you measure that?** Name the number, where it comes from, and its value today.

> 

**Who owns that number?** One named person. Not a team.

> 

**What would make you switch it off?** The value of the measure, or the condition, at which this agent stops being worth running.

> 

### 2. Purpose and scope

**What the agent does.** The work it performs, in the order it performs it.

> 

**What the agent does not do.** The nearby work someone would assume is in scope and is not. Answer this as fully as the question above it.

> 

**Who is on the other end.** Internal staff, named customers, or the general public. Whether they are told they are dealing with an agent, and how.

> 

### 3. Tools and data

This is the grant list. Stage 3 grants what is in this table and refuses everything else. If it is not here, the agent does not get it.

| Tool or system | What the agent does with it | Read or write | Data it reaches, and how sensitive | Can the action be undone, and within what window | Where the limit is enforced |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |

The last column takes one of three answers: **tool level**, **data level**, or **not enforceable here**. Every platform we have looked at can scope access at tool level, meaning this agent may call this tool and not that one. Scoping *within* a tool, to particular records or particular fields, is not portable and on some platforms is not possible at all. Where the limit you need is a data-level one your platform cannot express, write "not enforceable here". The agent can then reach more data than you intended, which is what question 2 of section 6 asks about.

**Other agents.** An agent that this one calls is a row in the table above, named as the agent and not as the tools behind it. Then say which agents call this one, whose authority those calls run under, and what this agent does when it cannot tell. A call arriving from another agent is not the same as a call from the person who started the chain, and a grant list is worth little if the agent cannot tell the two apart.

> 

**What the agent must never reach**, even though its credentials or its host could technically get there. Say where that refusal is enforced.

> 

**Value ceiling.** The most money or value the agent can move in one action, and in one day. Write "none" if there is no ceiling, and expect section 6 to charge you for it.

> 

### 4. What it decides alone

| Action or decision | Alone, never, or needs a person to approve | Where that is enforced |
|---|---|---|
| | | |
| | | |
| | | |

Enforcement is one of four answers: in the prompt, in the tool layer, in the platform, or nowhere. "In the prompt" counts, and it is the weakest of the four. Section 6 charges you for it.

### 5. Escalation and override

**How the agent hands work to a person.** What triggers it, who receives it, in which channel, and what happens if nobody answers.

> 

**How a person stops the agent.** The specific action somebody takes, who can take it, and how long it takes to have effect. Include how a run already in progress is stopped, and not only how the agent is turned off for the next one.

> 

**How a person reverses what it already did.** Per row of section 3 where the answer differs.

> 

**Who is told when it fails.** The person, the channel, and the time within which they are told.

> 

### 6. Classification, and the Classification Test

**The classification you are claiming for this agent:**

> 

Then answer the test. Every row asks one question, and every answer sets a floor: the lowest classification this agent can be in given that answer alone.

The questions and the rules below are reproduced from your [Risk Classifications](../02-policy/risk-classifications.md), so that this form stands on its own. That document is the authoritative one. If your copy of the test has been revised and this form has not, use theirs. The anchors that say what each answer has to reach to set each floor are in part 2 of that document, and are not reproduced here: read them before you fill in the floor column.

The classifications below are placeholders. If you already keep your own risk classifications, put those names in the floor column instead. Do not use an autonomy scale here; the notes explain why.

- **Routine.** A mistake is annoying. Somebody notices within a day and fixes it in an hour.
- **Significant.** A mistake costs money or time that somebody has to account for.
- **Sensitive.** A mistake reaches personal data, regulated processes, or people outside your company.
- **Critical.** A mistake is expensive, hard to reverse, reportable, or reaches many people at once.

| # | Question | Your answer | Where the evidence is | Floor this answer sets |
|---|---|---|---|---|
| 1 | How critical is the process it automates? If the agent stopped for a day, what stops with it? | | | |
| 2 | How sensitive is the data it can read? Name the most sensitive item, not the average. | | | |
| 3 | Which regulations reach this process? Name them, or write "none that we have identified" and say who looked. | | | |
| 4 | How much money or value can it move, in one action and in one day? | | | |
| 5 | Can you undo what it does? Name the action that is hardest to undo, and how long you have. | | | |
| 6 | How far does the damage spread beyond the system it acted on? | | | |
| 7 | What can it do with no person in the loop at all? | | | |
| 8 | Who is on the other end: internal staff, your customers, or the public? | | | |

**The rule.** The classification is the highest floor that any single row sets. One critical row makes the agent critical, however routine the other seven are.

**If you are placing this agent lower than its highest floor**, name the control that lowers it, where it is enforced, and who confirmed it holds. A control that exists in a plan does not lower a floor.

> 

Three limits on lowering a floor:

1. Questions 5 and 6 cannot be lowered. A control can stop the agent reaching them, but it cannot make the consequence smaller.
2. A control enforced only in the prompt cannot lower a floor. If section 4 says "in the prompt", the floor stands.
3. A lowered floor must also be named in the sign-off, in the [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md), by the person accepting it.

**A blank row is not a low answer.** An unanswered row means the classification is not yet established, and the agent is not ready for sign-off.

**What would change this classification?** The change to the agent, its tools, its data, or its model that would make you run this test again.

> 

### 7. Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |

Stage 4 and stage 5 findings land here. An eval that catches drift, an audit finding against your classification criteria, or a monitor reporting a tool call outside section 3 all produce a row.

Retiring the agent produces the last row. Set the status in section 0 to retired, date it, and go to section E of the [Audit and Assurance Record](../05-audit-and-assurance/audit-and-assurance-record.md): this document, the sign-off and the eval results all outlive the agent, and somebody has to say where they went.

---
