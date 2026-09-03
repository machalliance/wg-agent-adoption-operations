# Audit Log Rules

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 5 standard of the [Agent Governance and Assurance Framework](../../README.md). You write it once for your company. Its companion is the [Audit and Assurance Record](audit-and-assurance-record.md), which you fill in once per agent.

It answers one question: **what does an agent produce that your records policy has never seen, and who decides what happens to it?**

You have a records policy already, and at least one audit you pass. Retention periods, legal holds and control mappings belong to whoever owns those, and this document does not set them. It lists what agents add for them to decide, says what is different about it, and leaves the columns for the people who own the answer.

Part 4 says when to fold this into the policy you already have and stop maintaining it separately.

---

## Part 1: What agents produce

Stages 1 to 4 generate records. Some fit a data class your policy already names, and the answer is a pointer to a rule that exists. The rest need a decision, because nothing in your estate produced them before.

Take this list to whoever owns records, once, and fill in the rows.

| What agents produce | Which data class in our policy this is | Retention rule that applies | Where it is held | Already evidence for an audit we pass |
|---|---|---|---|---|
| Tool calls and their arguments | | | | |
| Inputs and outputs, including whatever a user typed | | | | |
| The prompt and context of a run | | | | |
| What the agent remembers between runs | | | | |
| Escalations to a person, and the outcome | | | | |
| Decisions the agent took alone | | | | |
| Sign-off records | | | | |
| Design document versions | | | | |
| Eval results and the assurance record | | | | |
| Incident records | | | | |

| Field | Your answer |
|---|---|
| Who owns retention and deletion decisions for these rows | |
| Which rows had no existing data class, and who is deciding | |
| Which rows contain personal data, and under what basis they are kept | |
| Which rows nothing currently records, and who owns closing that | |
| Where the rows that outlive the agent go once it is switched off, and who confirms they got there | |

The last two rows are the new work. The rest is pointing at rules you already have.

## Part 2: What is different about an agent's records

This is the part to take into that conversation, because it is the part a records policy did not contemplate.

**The record is free text, not fields.** An agent's inputs and outputs hold whatever a person typed and whatever the agent said back. Personal data arrives in a column nobody classified, whether or not the agent was designed to handle it.

**Re-running it does not reproduce it.** Two runs on the same input can differ. A conventional system can be re-executed to show what it would have done; an agent can only be shown what it did, from the stored run.

**What the agent ran on moves underneath the record.** A model version, a tool, a retrieved document or a system prompt can change without the agent's code changing. A run record that does not say which versions were in play cannot be tied back to what was signed off.

**The identity in the log is the agent's.** An agent acts for somebody, so reconstructing who is accountable means holding the delegation as well as the action.

**Four of these records outlive the agent.** Tool calls answer what happened last week. Sign-offs, design versions, eval results and incidents answer whether the agent was ever permitted to do that, and that question arrives when a customer disputes something old or a process has since been redesigned. The agent is usually switched off by then, and records get torn down with the infrastructure they sat on. Section E of the [Audit and Assurance Record](audit-and-assurance-record.md) is where a team says where those four went; the rule they are held under is yours to set here.

## Part 3: Where the answers probably already exist

Log evidence usually already sits under one of the standards below. Naming them saves you deriving an answer to part 1 that somebody at your company can give you by pointing at evidence they already produce.

**SOC 2.** Who can read and alter a log is covered by the common criteria for logical access and change management. Ask whether the operating team's access to agent run records was in scope when that evidence was produced.

**ISO/IEC 27001.** Event logging, log protection and evidence collection are controls you already maintain. Ask whether a run record counts as a log under them, given that it holds free text and not events.

**[ISO/IEC 42001](https://www.iso.org/standard/81230.html).** The certifiable AI management system standard, and the natural home for everything in this document. If you are heading there, part 4 applies. ISO/IEC 42006 sets the requirements for the bodies that certify against it.

**[EU AI Act](https://artificialintelligenceact.eu/).** [Article 12](https://artificialintelligenceact.eu/article/12/) concerns automatic recording of events over a system's lifetime, and [Article 11](https://artificialintelligenceact.eu/article/11/) keeping technical documentation current. Whether an agent of yours is in scope, and what those articles then require, is a question for counsel. We do not print compliance dates; several moved during 2026.

**[AIUC-1](https://aiuc-1.com/).** Publishes maps to the NIST AI RMF, ISO 42001, the EU AI Act, MITRE ATLAS and OWASP. Use those instead of deriving a second set that disagrees with them.

**Your privacy regime.** We do not name one, because which reaches you depends on where you operate. Whichever it is will ask whether you can find and remove one person's data, and free-text run records are where that gets hard. Section A of the [Audit and Assurance Record](audit-and-assurance-record.md) asks each agent whether it can.

For what to record and in what shape, stage 4 points at the [OpenTelemetry semantic conventions for generative AI](https://opentelemetry.io/blog/2026/genai-observability/).

| Field | Your answer |
|---|---|
| Which regimes apply to us, and who decided | |
| Who we ask when a question here turns out to be legal or regulatory | |

## Part 4: When you have outgrown this

Fold these rules into your existing records-management policy, and stop maintaining them separately, when any of these becomes true:

- Every row of part 1 points at a data class your records team maintains, and this document duplicates their index.
- You are certifying against ISO/IEC 42001, which expects records management inside a management system and not beside it.
- You are audited against AIUC-1, whose published maps replace part 3.
- An agent's records are subject to a regime part 3 does not name, and a lawyer is now involved.

At that point this document has done its job, which was to get agent records in front of a policy that already existed.

---

## Who owns this standard

| Field | Your answer |
|---|---|
| Owner: the person accountable for keeping these rules current | |
| Reviewed on a schedule of | |
| Last reviewed | |
| Records or legal function consulted | |

## Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |
