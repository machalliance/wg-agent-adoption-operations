# The Platform and Sign-off Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is a stage 3 artifact of the [Agent Governance and Assurance Framework](../../README.md): one per agent, alongside its [Agent Design Document](../01-agent-design/agent-design-document.md). It records what the agent actually runs on, what your evals found when you ran them against that setup, and who signed off on the result. Nothing goes live without this record completed and section C signed.

Whoever stood the agent up fills it in, with the person who will sign it off reading over their shoulder. It is completed last, after stage 4's [Monitoring and Incident Preparedness Record](../04-live-operations/monitoring-and-incident-preparedness-record.md), because section C compares the monitoring the agent actually has against what its classification requires.

[The notes on this form](platform-and-sign-off-record-notes.md) carry the guidance for filling it in and the reasoning behind each section. The levels themselves are defined in the [Platform Control Levels](platform-control-levels.md).

---

## The form

### A. The platform it runs on

What the agent actually runs on, and not what it is supposed to run on.

The two platform control rows ask different questions. The first is the strongest control the platform could enforce. The second is what was actually applied to this agent, which can be lower and cannot be higher. The monitoring levels are recorded once, in the [Monitoring and Incident Preparedness Record](../04-live-operations/monitoring-and-incident-preparedness-record.md); section C here records only whether the level applied meets what the classification requires.

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
| Autonomy level, on the four-level scale in the [CSA agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/), or your own if you keep one | |
| Tool servers and connectors it reaches, and who publishes each one | |

**Where the grant list is enforced.** Section 3 of the design document lists the tools and the data this agent needs. Say what enforces that list here: a gateway, a policy engine, scoped credentials, or a tool wrapper. Name the component.

> 

**What was actually granted, row by row.** Take each row of section 3 and write the permission that was really created for it, using the exact name your platform uses. This is the list your monitor compares live tool calls against.

| Row in section 3 | The permission actually granted, as the platform names it | Wider, narrower, or the same |
|---|---|---|
| | | |
| | | |
| | | |

**Anything narrower than the design document asks for.** Say what the agent cannot do as a result, and whether anybody has worked around it.

> 

**What is granted that the design document does not list.** Anything the agent can reach that section 3 does not name. This should be empty. Where it is not, write down what you found and carry it into section C as remaining risk. Do not fix it quietly and leave this row blank.

> 

### B. What the evals found

Evals run against the setup in section A, not against a development configuration.

| Field | Your answer |
|---|---|
| Which evals you ran | |
| Adversarial testing performed, and what it was tested against | |
| Against which configuration, matching section A | |
| Date of the run | |
| What they found | |
| What you changed because of it | |
| What you know you did not test | |
| Where the results are kept | |

For any agent that reads content it did not author, whether it can be talked into something is what the sign-off most needs to know. Name what you tested against from [OWASP's Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/), which is the same list stage 4's incident playbook works from.

Two rows carry more weight than the rest. "What they found" is what the person signing off is accepting. "What you know you did not test" is where stage 4's monitoring has to begin.

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
