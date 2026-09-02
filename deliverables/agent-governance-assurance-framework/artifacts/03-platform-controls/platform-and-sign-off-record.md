# The Platform and Sign-off Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is a stage 3 artifact of the [Agent Governance and Assurance Framework](../../README.md). You keep one for each agent, alongside its [Agent Design Document](../01-agent-design/agent-design-document.md).

It records three things: what the agent actually runs on, what your evals found when you ran them against that setup, and who signed off on the result. Together they are the gate between stage 3 and stage 4. Nothing goes live without this record completed and section C signed.

**Why this is a separate document.** A sign-off is granted against a version. If the platform record lived inside the design document, a model upgrade would bump that document's version and, by the framework's own rule, void a sign-off on a design that had not changed. Separating them means a platform change re-opens the platform record and its sign-off, and leaves the design document alone. Expect this record to turn over several times faster than the design it serves.

**Who fills it in.** Whoever stood the agent up, with the person who will sign it off reading over their shoulder. Section A is a description of a running system, so fill it in after the agent exists and not before.

**If the platform is somebody else's.** For an agent you bought rather than built, section A describes a platform you do not operate. Record what the vendor publishes, name the rows they will not answer, and say where you asked. A model version you cannot see is not the same as one you have not looked up, and only the second is a gap you can close. The rows you cannot fill are the ones section C has to accept by name.

**This is not the [Platform Control Levels](platform-control-levels.md).** That one describes your whole company: the three levels, and what each requires. This record is the per-agent entry that names which level a given agent is on.

For the reasoning behind each section, see [the notes on this form](platform-and-sign-off-record-notes.md). The levels themselves are defined in the [Platform Control Levels](platform-control-levels.md).

The two platform control rows in section A ask different questions. The first is the strongest control the platform could enforce. The second is what was actually applied to this agent, which can be lower and cannot be higher. The monitoring levels are recorded once, in the [Monitoring and Incident Record](../04-live-operations/monitoring-and-incident-record.md), and not here.

---

## The form

### A. The platform it runs on

What the agent actually runs on, and not what it is supposed to run on.

| Field | Your answer |
|---|---|
| Agent name, and the version of its design document this record serves | |
| Version of this record | |
| Date of this version | |
| Model, and its exact version | |
| Model provider, and where inference happens | |
| Agent framework, and its version | |
| Where it is hosted | |
| Agent login: the identity it uses, and what else uses that identity | |
| How the credentials are revoked, by whom, and how long that takes | |
| Platform control level of the platform it runs on: 1, 2 or 3 | |
| Platform control level actually applied to this agent | |
| When this agent's access is reviewed again, and by whom | |
| Autonomy level, if you keep an autonomy scale | |
| Tool servers and connectors it reaches, and who publishes each one | |

**Where the grant list is enforced.** Section 3 of the design document lists the tools and the data this agent needs. Say what enforces that list here: a gateway, a policy engine, scoped credentials, or a tool wrapper. Name the component.

> 

**What is granted that the design document does not list.** Anything the agent can reach that section 3 does not name. This should be empty. Where it is not, write down what you found and carry it into section C as remaining risk. Do not fix it quietly and leave this row blank.

> 

### B. What the evals found

Evals run against the setup in section A, not against a development configuration.

| Field | Your answer |
|---|---|
| Which evals you ran | |
| Against which configuration, matching section A | |
| Date of the run | |
| What they found | |
| What you changed because of it | |
| What you know you did not test | |
| Where the results are kept | |

Fill in the last two rows carefully. What the evals found is what the person signing off is accepting. What you did not test is where stage 4's monitoring has to begin.

### C. Sign-off

One named person accepts the agent as a whole: what it is for, its classification, the platform it runs on, what the evals found, and the risk that is left.

| Field | Your answer |
|---|---|
| Name | |
| Role | |
| Date | |
| Version of the design document signed | |
| Version of this record signed | |
| The risk that is left, stated in their words | |
| Any classification floor lowered by a compensating control, named | |
| Conditions on the sign-off, and when it must be looked at again | |

**The level gap.** The agent's classification names a platform control level and a monitoring level that an agent in it requires. Where the level applied is lower than the level required, the gap is accepted here, by name, or it is not accepted at all.

| Field | Your answer |
|---|---|
| Platform control level the classification requires, and the level applied | |
| Monitoring level the classification requires, and the level applied | |
| Who accepts the gap, by name | |
| The date by which it closes | |
| How many consecutive sign-offs have accepted this same gap | |

Answer the last row honestly. A gap accepted once is a legitimate decision made under time pressure. A gap accepted three times in a row is a decision nobody is making, and this count is the only thing on any of these forms that would show it.

Two rules on this section.

**The sign-off is against versions, and both are named above.** When live behavior stops matching the description it was granted against, it is void until somebody looks again.

**A lowered classification floor is signed here or it does not hold.** If section 6 of the design document places the agent below its highest floor on the strength of a compensating control, the accountable person names that reduction in the row above. A floor lowered in the design document and not repeated here has not been accepted by anybody.

### D. Revision history

| Date | Version | What changed | Why | Who | Did it need a new sign-off |
|---|---|---|---|---|---|
| | | | | | |

A model version bump, a framework upgrade, a new tool, or a change of host all produce a row. Answer the last column every time, because an auditor will ask which changes went live without a fresh sign-off.

---
