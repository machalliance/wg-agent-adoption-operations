# Monitoring Levels

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 4 standard of the [Agent Governance and Assurance Framework](../../README.md). You write it once for your company. Its companion is the [Monitoring and Incident Record](monitoring-and-incident-record.md), which you fill in once per agent.

It answers one question: **how much can you actually see of what an agent did, and can you check it without a person remembering to?**

Stage 2 uses the answer to set requirements, because a classification says an agent needs a given level. Stage 4 records which level each agent is really on, and stage 3's sign-off rests on that number being true.

These levels climb **separately** from the [Platform Control Levels](../03-platform-controls/platform-control-levels.md). Those measure what an agent can reach. These measure what you can see. An agent can sit at platform control Level 3 and monitoring Level 1: permissions enforced in code, behavior watched by a log nobody reads.

**This is a starting ladder, not a complete model.** It exists so a team with nothing can work out where they stand and what to do next. Part 4 says where to go when you need more, and part 5 says when that point has arrived.

---

## Part 1: The three levels

Every level requires that something is recorded on every run and that somebody is told when it looks wrong. What changes between levels is **how much of the run you keep** and **whether anything checks it without being asked**.

### Level 1 — the tool call log

You know what the agent did, after the fact, if you go looking.

- Every tool call and its arguments are logged.
- Inputs and outputs are kept for a stated period.
- Alerts fire on a few coarse signals: a call to a tool outside the declared set, unusual volume, a high escalation rate.
- Somebody is named to receive those alerts.

Most teams running their first agent are here, and there is nothing wrong with that. What Level 1 cannot tell you is why the agent did something, or whether a run that looked fine was correct.

### Level 2 — run records

You can reconstruct a run and compare it to what the agent was supposed to do.

- Everything in Level 1.
- The prompt, the context and the outputs of a run are stored, not just the tool calls.
- Live behavior is compared against the agent's design document, and drift raises an alert as well as errors.
- Evals run against the live agent without a person starting them, whether on a schedule, on each deployment, or continuously.
- Their results are compared against the baseline recorded at sign-off.
- You would know within a day if they stopped running.

The difference from Level 1 is that you find out about a problem because something checked, not because somebody complained.

### Level 3 — tested and replayable

You can re-run the past and test against it.

- Everything in Level 2.
- A specific past run can be replayed.
- Runs are tested against a maintained set of known failure modes.
- Failures found in production become permanent test cases.
- Records are held in a form an auditor accepts, which is stage 5's requirement, and the operating team cannot silently alter them.

---

## Part 2: Which level are you on

Answer for one platform. Any "no" means you are not yet at that level, whatever else is true.

**Level 1**

- Is every tool call logged, with its arguments?
- Are inputs and outputs kept for a period somebody has stated in writing?
- Would a call to a tool outside the declared set raise an alert?
- Is there a named person who receives that alert and is expected to act?

**Level 2**

- Can you retrieve the prompt and context of a specific run from last week?
- Does anything compare live behavior to the agent's design document?
- Do evals run with no person starting them?
- Are their results measured against the baseline recorded at sign-off?
- Would you find out within a day if they stopped running?

**Level 3**

- Can you replay a specific past run?
- Do you maintain a set of known failure modes that runs are tested against?
- Does a production failure reliably become a permanent test case?
- Are the records beyond the reach of the team that operates the agent?

Answer honestly, for the same reason the platform control levels give: a sign-off rests on this number being true.

---

## Part 3: What a level applies to

A level describes **a platform**, in the same way the platform control levels do. What your observability stack collects and retains is a property of the stack, not of one agent.

An individual agent then records the level actually applied to it, in its Monitoring and Incident Record. That level cannot be higher than its platform's, and it can be lower: a platform that stores full run records will still hold an agent nobody wired the alerting up for.

| | What it describes | Where it is recorded |
|---|---|---|
| Platform level | The most this platform can see and check | This document, one row per platform |
| Agent level | What is actually collected and checked for this agent | The agent's Monitoring and Incident Record |

### Your platforms

| Platform | Level | Assessed on | Who assessed it | What is needed to reach the next level |
|---|---|---|---|---|
| | | | | |
| | | | | |

---

## Part 4: Where to go deeper

Two destinations, because this stage has two halves.

For **what to record and in what shape**, use the [OpenTelemetry semantic conventions for generative AI](https://opentelemetry.io/blog/2026/genai-observability/). They define the span names, attributes, metrics and events for model calls, tool executions, agent runs, retrieval and memory, so your traces mean the same thing across frameworks and vendors. Agent spans are still marked experimental, so read the current status before you commit to them.

For **what can go wrong and therefore what to watch for**, use [OWASP's Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/). It is the closest thing to an agreed taxonomy of how these systems fail, and section E of the record is drawn from it.

Our three levels are a plain-language on-ramp. Where they disagree with either source, the source is the more considered one.

---

## Part 5: When you have outgrown this

Stop using this ladder and build against the conventions above when any of these becomes true:

- You need to know which agent in a chain caused an outcome, and your traces cannot tell you.
- You need to prove to somebody outside your company what an agent did months ago.
- You are comparing live behavior to a baseline by reading dashboards yourself.
- Your agents are created and destroyed faster than anybody configures alerting for them.
- You buy a product that supervises your agents, and you need to state what it does and does not cover.

By then you need the detail those conventions carry, and three levels will be flattening distinctions you have started to depend on.

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
