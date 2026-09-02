# Risk Classifications and the Classification Test

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This is the stage 2 artifact of the [Agent Governance and Assurance Framework](../../README.md). It is a **standard**: you write it once for your company, and it grows as you build agents it does not yet describe. The framework has four standards: this one, the [Platform Control Levels](../03-platform-controls/platform-control-levels.md), the [Monitoring Levels](../04-live-operations/monitoring-levels.md) and the [Audit Log Rules](../05-audit-and-assurance/audit-log-rules.md). Everything else is a **record**, filled in once per agent.

Stage 2 is the only stage that is not about a single agent. This document says which kinds of agent you build, what risk each kind carries, and which controls come with it. The argument that a *particular* agent belongs in a particular classification stays with that agent, in section 6 of its [Agent Design Document](../01-agent-design/agent-design-document.md).

**You do not need the whole set before you ship.** You need the one classification your first agent belongs to. Fill in that row, leave the others, and come back when an agent arrives that the set does not describe.

**The four classifications below are a starting point, not a recommendation.** They are filled in so that you have something to argue with. Rename them, merge them, split them, or replace them. What matters is that the criteria are yours and that somebody can tell which classification an agent belongs to without asking you.

For the reasoning behind the criteria and the test, see [the notes on this standard](risk-classifications-notes.md).

---

## Part 1: The classifications

Filled in as a starting point. Replace with your own.

### Routine

| Field | Starting point |
|---|---|
| What a mistake costs | A mistake is annoying. Somebody notices within a day and fixes it in an hour. |
| Typical agents | Internal search, summarizing documents a person already has access to, drafting text a person sends. |
| Data it may reach | Data the person on the other end could already read. |
| Money it may move | None. |
| Reversibility required | Everything it does can be undone by the person who received it. |
| Who may be on the other end | Internal staff. |
| Platform control level required, applied to the agent | Level 1. |
| Monitoring level required | Level 1. |
| Who signs off | The team's own manager. |
| Reclassify when | It reaches data the reader could not already see, or it starts writing to a system of record. |

### Significant

| Field | Starting point |
|---|---|
| What a mistake costs | A mistake costs money or time that somebody has to account for. |
| Typical agents | Updating records in a system of record, routing work, generating operational reports others act on. |
| Data it may reach | Internal commercial data. No personal data beyond names and work contact details. |
| Money it may move | Up to a stated ceiling per action and per day, set per agent. |
| Reversibility required | Every action reversible within one working day. |
| Who may be on the other end | Internal staff, and named customers under supervision. |
| Platform control level required, applied to the agent | Level 1. |
| Monitoring level required | Level 1. |
| Who signs off | The owner of the process being automated. |
| Reclassify when | It reaches personal data, or an action becomes hard to reverse. |

### Sensitive

| Field | Starting point |
|---|---|
| What a mistake costs | A mistake reaches personal data, regulated processes, or people outside your company. |
| Typical agents | Anything customer-facing, anything touching personal data, anything inside a regulated process. |
| Data it may reach | Personal data, under a named lawful basis, with the fields listed in the design document. |
| Money it may move | Up to a stated ceiling, with a person approving anything above it. |
| Reversibility required | Irreversible actions require a person to approve them first. |
| Who may be on the other end | Customers, who are told they are dealing with an agent. |
| Platform control level required, applied to the agent | Level 2. |
| Monitoring level required | Level 2. |
| Who signs off | A named accountable executive, with your privacy or compliance function consulted. |
| Reclassify when | It can move money without a ceiling, or a mistake would be reportable. |

### Critical

| Field | Starting point |
|---|---|
| What a mistake costs | A mistake is expensive, hard to reverse, reportable, or reaches many people at once. |
| Typical agents | Anything that moves money without a person, changes production systems, or speaks publicly as your company. |
| Data it may reach | As listed in the design document and nothing wider. Special category data only with a specific decision recorded. |
| Money it may move | Only within a hard ceiling enforced by the platform, not by the agent. |
| Reversibility required | Irreversible actions require a person to approve them, and that approval is logged. |
| Who may be on the other end | Anyone, including the public. |
| Platform control level required, applied to the agent | Level 3. |
| Monitoring level required | Level 3. |
| Who signs off | A named accountable executive. Consider a second signature. |
| Reclassify when | Nothing moves an agent up from here. It leaves only when its scope narrows: the test is re-run, and the reduction is signed by the person who accepted the original risk. |

### A note on the two level numbers

The rows above set the level that must be **applied to the agent**. The [Platform Control Levels](../03-platform-controls/platform-control-levels.md) also scores each platform, and an agent's level can never exceed its platform's. A classification requiring Level 2 therefore rules out any platform still at Level 1, whatever is done to the individual agent.

Each classification names exactly one level per ladder. Do not qualify the number — "Level 1, moving to Level 2" and "Level 1 with extra alerting" are not levels, and a rule stated that way cannot be enforced or checked. If you want more than a level gives you, raise the number.

Routine and Significant both sit at Level 1 here, which is deliberate. What separates them is the data the agent may reach, the money it may move, how fast an action has to be reversible, and who signs off. None of that is a question about how mature your platform is.

### When a classification demands more than you have

The starter classifications above require platform control Level 2 for sensitive agents and Level 3 for critical ones. Most companies are at Level 1. Read literally, that means you should not be running the agent you are already running.

That is a real finding, not a flaw in the table, and there are three honest responses. You can stop the agent. You can raise the platform control level before it ships. Or you can record the gap in the agent's [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md) and have the accountable person accept it by name, with a date by which it closes.

The third is the common answer and it is legitimate, once. A gap that has been accepted three times in a row is a decision nobody is making.

### Your classifications

Copy the table above for each classification you keep. Fill in every row, including the last one: a classification with no stated trigger for leaving it is a classification agents never leave.

---

## Part 2: The Classification Test

The classifications need a test beside them, or every team declares its own agent low risk and you are left with a document asserting that the risk was assessed.

This is the authoritative definition of the test. The **answers** for a given agent go in section 6 of that agent's design document, not here.

Section 6 of the design document reproduces the questions so that a team can fill the form in without opening this one. When you revise the test here, those copies go stale. Say in your revision history that you have changed it, so that agents classified under the old version can be found.

### The eight questions

| # | Question | What it measures |
|---|---|---|
| 1 | How critical is the process it automates? If the agent stopped for a day, what stops with it? | Process criticality |
| 2 | How sensitive is the data it can read? Name the most sensitive item, not the average. | Data sensitivity |
| 3 | Which regulations reach this process? Name them, or write "none that we have identified" and say who looked. | Regulatory reach |
| 4 | How much money or value can it move, in one action and in one day? | Financial exposure |
| 5 | Can you undo what it does? Name the action that is hardest to undo, and how long you have. | Reversibility |
| 6 | How far does the damage spread beyond the system it acted on? | Spread |
| 7 | What can it do with no person in the loop at all? | Autonomy |
| 8 | Who is on the other end: internal staff, your customers, or the public? | Audience |

### What sets each floor

The questions are open on purpose: the answer is evidence, not a score. But an open question with four one-line classifications beside it is not yet a test, because two teams will read the same agent into two different classifications. The anchors below say what each answer has to reach to set each floor.

Read along a row and take the **highest column any part of your answer reaches**. Then write that classification in the floor column of section 6 of the agent's design document, and the answer itself beside it.

These anchors describe the four starter classifications. If you rename, merge or replace those, rewrite this table with them: it is the part of the test that has to move when the classifications do.

| # | Sets a Routine floor | Sets a Significant floor | Sets a Sensitive floor | Sets a Critical floor |
|---|---|---|---|---|
| 1. Process criticality | Nothing stops. A person does the work by hand instead. | Work queues up and somebody has to catch up afterwards. | A customer-facing or regulated process stalls. | A process the business cannot go a day without stops. |
| 2. Data sensitivity | Only data the person on the other end could already read. | Internal commercial data. Names and work contact details. | Personal data, or data held under a confidentiality obligation. | Special category personal data, payment or credential data, or material non-public information. |
| 3. Regulatory reach | None identified, and a named person looked. | Internal policy or contractual obligations only. | A named regulation reaches the process. | The process is supervised, or a mistake in it is reportable to a regulator. |
| 4. Financial exposure | It moves no money or value. | Within a ceiling a manager can approve as ordinary spend. | Above that ceiling, or the ceiling is per action with no daily limit. | No ceiling, or a ceiling the agent observes itself rather than one the platform enforces. |
| 5. Reversibility | The person who received it can undo it themselves. | Reversible by the team within one working day. | Reversible only with another party's help, or beyond one working day. | Not reversible, or reversible only by telling somebody it happened. |
| 6. Spread | It stays in the system the agent acted on. | Another internal system or team has to correct it. | It reaches a customer, a partner, or a system you do not control. | It reaches many people at once, a public channel, or another agent that acts on it. |
| 7. Autonomy | A person reviews every action before it takes effect. | A person reviews the actions that set a floor above Routine. | It acts alone inside a scope somebody set, and a person sees the result afterwards. | It acts alone, and nobody sees the result unless something alerts. |
| 8. Audience | Internal staff. | Internal staff, and named customers under supervision. | Customers, who are told they are dealing with an agent. | The public, or anybody who reads the output as your company's position. |

Fill in your own two numbers for question 4, per action and per day, and put them in the classification tables in part 1 so that the same numbers govern every agent.

Question 7 does not measure consequence. It is the one row where the anchors describe supervision instead of damage. It is here because it is what turns the other seven into risk: an agent that could do a critical thing, but never does one without a person approving it first, is not the same agent as one that does.

### The rule

Every answer sets a **floor**: the lowest classification the agent can be in given that answer alone. The agent's classification is the **highest floor any single answer sets**.

Averaging is the failure mode this rule exists to stop. An agent that reads only public data, moves no money, and does one thing you cannot undo is not a medium-risk agent with one bad property.

### Lowering a floor

A floor can be lowered by a compensating control, under three limits:

1. Questions 5 and 6 cannot be lowered. A control can stop the agent reaching them. It cannot make the consequence smaller.
2. A control enforced only in the prompt cannot lower a floor.
3. A lowered floor must be named in the sign-off, in the agent's [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md), by the person accepting it.

### When the test runs again

The test is not a one-time gate. Run it again when any of these happens:

| Trigger | Where it comes from |
|---|---|
| A new model version | Stage 3 platform record |
| A new tool, or a widened data scope | Stage 1 design document |
| Monitoring reports behavior outside the declared set | Stage 4 |
| An audit finding against a classification's criteria | Stage 5 |
| A new audience, such as a customer-facing use of an internal agent | Stage 1 design document |

A classification that has never been re-run against what monitoring sees describes the agent you shipped, not the one you are running.

---

## Who owns this standard

| Field | Your answer |
|---|---|
| Owner: the person accountable for keeping these classifications current | |
| Reviewed on a schedule of | |
| Last reviewed | |

## Revision history

| Date | Version | What changed | Why | Who |
|---|---|---|---|---|
| | | | | |

Record the date you last revised this. An audit finding against a classification's criteria, or an agent that fits no classification, both produce a row.
