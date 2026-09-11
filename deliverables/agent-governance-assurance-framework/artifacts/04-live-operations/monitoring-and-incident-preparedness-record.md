# The Monitoring and Incident Preparedness Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 4 artifact of the [Agent Governance and Assurance Framework](../../README.md): one per agent, alongside its [Agent Design Document](../01-agent-design/agent-design-document.md) and its [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md). Sections A to C are the Monitoring Plan: what you record on every run, what counts as normal, and what starts an alert. Sections D and E are the Incident Playbook: what happens once an alert starts, and who does it.

The team that operates the agent fills it in, before the agent goes live rather than after the first incident. Section B needs whoever owns the pipeline the agent is deployed through, and section D needs whoever is on call.

[The notes on this form](monitoring-and-incident-preparedness-record-notes.md) carry the guidance for filling it in and the reasoning behind each section. The levels themselves are defined in the [Monitoring Levels](monitoring-levels.md).

---

## The form

### A. What you record on every run

The two monitoring rows ask different questions. The first is the most this platform can see. The second is what is actually collected and checked for this agent, which can be lower and cannot be higher.

| Field | Your answer |
|---|---|
| Agent name, and the design document version this serves | |
| Version of this record | |
| Date of this version | |
| Monitoring level the classification requires | |
| Monitoring level of the platform it runs on: 1, 2 or 3 | |
| Monitoring level actually applied to this agent | |
| Version of the Monitoring Levels this score was made against | |
| Who owns this monitoring | |

Where the level applied is lower than the level the classification requires, the gap is accepted in section C of the [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md), not here. This form records what is true; that one records who accepted it.

| What you record | Do you record it | Where it goes | How long you keep it |
|---|---|---|---|
| Every tool call, and its arguments | | | |
| Inputs to the run | | | |
| Outputs of the run | | | |
| The prompt and context as sent | | | |
| The agent's steps between the request and the answer | | | |
| Escalations to a person, and the outcome | | | |
| Enough of the run to replay it | | | |
| Cost and token use per run | | | |

**What you deliberately do not record, and why.** Usually personal data you have no basis to retain. Say what you lose by not recording it.

> 

**Who can read these records, and who can change them.** If the team that operates the agent can edit its own logs, say so here.

> 

### B. The evals, and what runs them

| Field | Your answer |
|---|---|
| Which evals run against the live agent | |
| What starts them: a schedule, a deployment, live traffic, or a person | |
| How often, or what share of live traffic if they run continuously | |
| Where the results go | |
| Who is told when one fails | |
| Who owns extending the eval set as the agent changes | |
| How you would know they had stopped running | |

**Which baseline the results are compared against.** Normally the eval results recorded in the Platform and Sign-off Record at sign-off. Name the version.

> 

### C. What counts as normal, and what starts an alert

| Signal | What normal looks like | What starts an alert | Who receives it | Implemented today |
|---|---|---|---|---|
| A call to a tool outside the declared set | Never | | | |
| Volume of runs | | | | |
| Escalation rate to a person | | | | |
| Eval failure | Never | | | |
| Cost per run or per day | | | | |
| Error or retry rate | | | | |
| Drift from the design document | | | | |
| | | | | |

Answer the last column for what is implemented today, not for what is planned. A row with nothing behind it is a gap the sign-off has to carry.

The first row needs the granted permissions from section A of the Platform and Sign-off Record. Naming where the monitor gets that list is the difference between an alert you can build and one you intend to.

### D. What an alert starts

| Stage | What happens | Who does it | Within what time |
|---|---|---|---|
| Triage: is this real | | | |
| Contain: stop or narrow the agent | | | |
| Review the run records | | | |
| Fix | | | |
| Tell the people affected | | | |
| Decide whether anybody outside has to be told, and start that clock | | | |
| Review after the incident | | | |
| Decide whether the agent resumes, and whether the sign-off still holds | | | |

For an agent inside a regulated process, notifying a regulator or a data-protection authority runs on a clock that starts well before the fix is finished. Stage 2 classifies agents on whether a mistake is reportable, so somebody has to decide here whether this one is.

The stage 3 sign-off is void once live behavior stops matching what it was granted against, and an incident is that moment. Name who re-confirms it, or re-issues it, before the agent runs again.

**How the agent is stopped, and by whom.** Point at section 5 of the design document rather than restating it, and say who is on call to do it.

> 

**What you tell a customer, and who decides.** For any agent where the person on the other end is not internal staff. Say also how that person challenges the outcome, pointing at section 5 of the design document rather than restating it.

> 

### E. What goes wrong, and what you do about it

Agents fail in ways ordinary software does not. Copying your existing incident process will not cover these. For each one, say what you would do, or write "not covered" and let the sign-off carry it.

| What goes wrong | OWASP | What you do |
|---|---|---|
| The agent calls a tool outside its declared set | ASI02, ASI03 | |
| A chain of tool calls each succeeds but the outcome is wrong | ASI08 | |
| Prompt injection through content the agent reads | ASI01 | |
| Scope creep: the agent is used for work it was not designed for | ASI09 | |
| The agent loops, or runs away on cost | ASI08 | |
| A model or framework update changes behavior with no code change | ASI04 | |
| Memory or retrieved context has been poisoned | ASI06 | |
| The agent is confidently wrong and a person acts on it | ASI09 | |
| The agent stops escalating when it should | ASI09 | |
| The agent runs code or shell commands it composed itself | ASI05 | |
| A supervising agent fails, or supervises wrongly | ASI07, ASI10 | |

The OWASP column names the entry in the [Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) each row is drawn from, so a team already working that list can see the overlap without deriving it. Where a row does not apply to your agent, write "the agent cannot do this" rather than leaving it blank. A blank reads as an unanswered question, and the ASI05 row in particular is the one that decides whether this playbook covers a coding agent.

### F. Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |

A new alert, a threshold you had to move, or a way of going wrong you learned the hard way all produce a row. So does an incident that this playbook did not cover.
