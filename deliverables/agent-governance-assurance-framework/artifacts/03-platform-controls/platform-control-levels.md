# Platform Control Levels

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 3 standard of the [Agent Governance and Assurance Framework](../../README.md). You write it once for your company. Its companion is the [Platform and Sign-off Record](platform-and-sign-off-record.md), which you fill in once per agent.

It answers one question: **how tightly is an agent's access actually controlled, and who decides?**

Stage 2 uses the answer to set requirements, because a classification says an agent needs a given level. Stage 3 records which level each agent is really on. Without this document those levels mean whatever the reader assumes.

**This is a starting ladder, not a complete model.** It exists so a team with nothing can work out where they stand and what to do next, in an afternoon. Part 4 says where to go when you need more than that, and part 5 tells you when that point has arrived.

---

## Part 1: The three levels

Every level requires least privilege: an agent gets the tools and data its design document lists, and nothing else. What changes between levels is **who decides the permissions** and **what stops them drifting**.

### Level 1 — a person sets the scope

An engineer creates a login for the agent, scoped by hand to what its design document lists.

- The agent has its own login. It is not shared with a person, a service, or another agent.
- The scope was set from the agent's design document.
- There is a written way to revoke the login, and somebody named can do it.
- Credentials are not embedded in code or configuration that people can read.

Level 1 is a legitimate place to stand while you learn. Most teams shipping their first agent are here, and the record should say so.

### Level 2 — the classification sets the ceiling

The agent's risk classification decides the most access it can be granted. An engineer works inside that ceiling and cannot exceed it.

- Everything in Level 1.
- Each classification has a defined maximum scope.
- Granting past that maximum is blocked, not merely discouraged.
- Credentials are short-lived and reissued, not long-lived and rotated occasionally.
- Somebody reviews each agent's access on a stated schedule.

The difference from Level 1 is that a mistake by one engineer can no longer produce an over-permissioned agent.

### Level 3 — code grants it and keeps checking

Access is granted and removed by policy expressed as code, and something continuously checks that what is granted still matches what the classification allows.

- Everything in Level 2.
- Permissions are granted and revoked automatically, from the agent's declared design.
- A continuous check compares granted access against declared access and reports the difference.
- Revocation takes effect in seconds, across every system the agent reaches.
- Access review is automatic and its results are recorded.

---

## Part 2: Which level are you on

Answer for one platform. Any "no" means you are not yet at that level, whatever else is true.

**Level 1**

- Does each agent have a login used by nothing else?
- Was its scope set from its design document rather than copied from an existing role?
- Can a named person revoke it, using a written procedure?
- Are its credentials absent from readable code and configuration?

**Level 2**

- Does each risk classification have a defined maximum scope?
- Would an attempt to exceed that maximum be blocked rather than logged?
- Do credentials expire in hours rather than months?
- Is each agent's access reviewed on a schedule somebody owns?

**Level 3**

- Are permissions granted and revoked by code from a declared source, with no manual step?
- Does something continuously compare granted access against declared access?
- Can you revoke an agent everywhere within seconds?
- Are access reviews automatic, with recorded results?

Answer honestly. A level you claim and do not have is worse than a lower level recorded accurately, because the sign-off in stage 3 rests on it.

---

## Part 3: What a level applies to

A level describes **a platform**, not a company and not an agent.

Most companies run agents in more than one place, and those places are rarely controlled equally well. A single company-wide score would be wrong everywhere. Score each platform separately.

An agent usually touches more than one. The model sits behind a provider's API, the tools behind a gateway, the process on a host. Score the platform that grants the agent's access, because that is what a control level describes, and name the others in section A of the agent's record.

An individual agent then records the level it actually runs at, in its Platform and Sign-off Record. That level **cannot be higher than its platform's**, and it can be lower: a platform capable of Level 3 will still hold an agent that somebody scoped by hand.

So there are two numbers, and both matter:

| | What it describes | Where it is recorded |
|---|---|---|
| Platform level | The strongest control this platform can enforce | This document, one row per platform |
| Agent level | The control actually applied to this agent | The agent's Platform and Sign-off Record |

### Your platforms

| Platform | Level | Assessed on | Who assessed it | What is needed to reach the next level |
|---|---|---|---|---|
| | | | | |
| | | | | |

---

## Part 4: Where to go deeper

This ladder is deliberately short. When you need the real thing, go to the **[Cloud Security Alliance's Agentic AI Identity and Access Management](https://cloudsecurityalliance.org/artifacts/agentic-ai-identity-and-access-management-a-new-approach)**. It is free, it is written for agents rather than for software generally, and it covers what this document does not: agents that spawn other agents, delegation you can trace back to a person, credentials that exist only for one task, and revoking an agent across systems that do not share a login.

Our three levels are a plain-language on-ramp to that work. Where the two disagree, CSA is the more considered source.

---

## Part 5: When you have outgrown this

Stop using this ladder and use CSA's model when any of these becomes true:

- One of your agents calls another agent, and you need to know who authorized what.
- An agent acts for several different people and its permissions should differ for each.
- You need to revoke an agent across systems that do not share an identity provider.
- Your agents are created and destroyed faster than a person can review them.
- An auditor asks how you prove an agent acted within delegated authority, and "we scoped the login" is not enough.

At that point three levels are too coarse to describe what you are doing, and this document becomes a summary of a problem you have already moved past.

---

## Who owns this standard

| Field | Your answer |
|---|---|
| Owner: the person accountable for keeping these levels current | |
| Reviewed on a schedule of | |
| Last reviewed | |

## Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |
