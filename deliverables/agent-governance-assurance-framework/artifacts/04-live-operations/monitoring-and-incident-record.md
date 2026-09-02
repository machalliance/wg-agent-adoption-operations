# The Monitoring and Incident Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 4 artifact of the [Agent Governance and Assurance Framework](../../README.md). It is a **record**: one per agent, alongside its [Agent Design Document](../01-agent-design/agent-design-document.md) and its [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md).

It holds two connected things. Sections A to C are the Monitoring Plan: what you record on every run, what counts as normal, and what starts an alert. Sections D and E are the Incident Playbook: what happens once an alert starts, and who does it.

For the reasoning behind each section, see [the notes on this form](monitoring-and-incident-record-notes.md). The levels themselves are defined in the [Monitoring Levels](monitoring-levels.md).

**Who fills it in.** The team that operates the agent, with whoever owns the alerting it will use. Section D needs whoever is on call.

**If you bought the agent rather than built it.** Section A describes what the vendor's platform records and what it will hand you. Name the rows they will not answer, and say where you asked. A signal you cannot get is a monitoring gap like any other, and section C is where it shows up as an alert you cannot implement.

**Fill this in before the agent goes live, not after the first incident.** The sign-off in stage 3 is granted against a described set of behaviors. This document is how anybody finds out whether the live agent is still inside them.

**The hard part is section B.** Everything else describes intent. Section B is what makes the evals run without a person remembering to start them, and it is the difference between assurance and a good intention.

The two monitoring rows in section A ask different questions. The first is the most this platform can see. The second is what is actually collected and checked for this agent, which can be lower and cannot be higher.

---

## The form

### A. What you record on every run

| Field | Your answer |
|---|---|
| Agent name, and the design document version this serves | |
| Version of this record | |
| Date of this version | |
| Monitoring level of the platform it runs on: 1, 2 or 3 | |
| Monitoring level actually applied to this agent | |
| Who owns this monitoring | |

| What you record | Do you record it | Where it goes | How long you keep it |
|---|---|---|---|
| Every tool call, and its arguments | | | |
| Inputs to the run | | | |
| Outputs of the run | | | |
| The prompt and context as sent | | | |
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

### D. What an alert starts

| Stage | What happens | Who does it | Within what time |
|---|---|---|---|
| Triage: is this real | | | |
| Contain: stop or narrow the agent | | | |
| Review the run records | | | |
| Fix | | | |
| Tell the people affected | | | |
| Review after the incident | | | |

**How the agent is stopped, and by whom.** Point at section 5 of the design document rather than restating it, and say who is on call to do it.

> 

**What you tell a customer, and who decides.** For any agent where the person on the other end is not internal staff.

> 

### E. The failure modes this playbook covers

Agents fail in ways ordinary software does not. Copying your existing incident process will not cover these. For each one, say what you would do, or write "not covered" and let the sign-off carry it.

| Failure mode | OWASP | What you do |
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
| A supervising agent fails, or supervises wrongly | ASI07, ASI10 | |

The OWASP column names the entry in the [Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) each row is drawn from, so a team already working that list can see the overlap without deriving it. One entry has no row of its own: ASI05, unexpected code execution. Add a row for it if your agent can run code or shell commands that it composed itself.

### F. Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |

A new alert, a threshold you had to move, or a failure mode you learned the hard way all produce a row. So does an incident that this playbook did not cover.
