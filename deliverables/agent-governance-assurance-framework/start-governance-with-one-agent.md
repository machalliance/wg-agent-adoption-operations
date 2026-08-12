# Start Governance with One Agent, Not the Whole Enterprise

*A draft five-layer framework from the MACH Alliance Agent Adoption & Operations Working Group*

Most enterprises with an AI governance policy could not pick one agent in production and
show that its behavior matches it.

The usual approach guarantees that. Agent governance gets scoped as an enterprise program:
one access control standard, covering every agent, agreed by every team that owns one. That
agreement can take longer than the agents take to reach production. Teams ship in the
meantime, on shared logins, with no record of what an agent decided or why.

The MACH Alliance [Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations)
has published a [draft structure](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/agent-governance-assurance-framework)
built the other way round. A team can govern one agent in a sprint, without waiting for a
standard that covers all of them.

## The layers hold each other up

A rule in your policy is true only if the platform enforces it, the agent's design uses it,
someone accountable has accepted it, live behavior confirms it, and the audit record proves
it. Break one of those links and every layer above it is an empty claim. So the draft
organizes the work as five connected layers, rather than five documents that never mention
each other.

| Layer | What you write | What it does |
|---|---|---|
| 1. Policy | Risk Tiers and the Tier Test | Sets the risk tiers, and gives you a test that puts any agent into the correct one |
| 2. Platform controls | Access Control Ladder | Turns each tier into controls you can enforce, one agent at a time |
| 3. Agent design | Agent Design Document | Records one agent: its purpose, its tools, its data, its limits, and why it is in its tier. A named owner accepts the risk that is left and approves the agent before it goes live |
| 4. Live operations | Monitoring Plan and Incident Playbook | Checks live behavior against the design document, and tells you what to do when an alert starts |
| 5. Audit evidence | Audit Log Rules | Keeps locked proof, mapped to SOC 2, ISO 27001 and EU AI Act duties |

Layer 5 feeds back into Layer 1. Audits correct the tiers they were built to satisfy, and
without that return path the tiers stay as first written while the agents keep changing. The
full reasoning is in the [layered model write-up](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/agent-governance-layered-model.md),
which also sets out where the draft leans on existing work instead of restating it,
including [AI TRiSM](https://www.gartner.com/en/articles/ai-governance-trism),
[AIUC-1](https://aiuc-1.com/), the
[NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
and the Cloud Security Alliance's
[agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/),
ISO/IEC 42001, and
[FIDO's agentic authentication work](https://fidoalliance.org/fido-alliance-to-develop-standards-for-trusted-ai-agent-interactions/).

## Plain words, on purpose

Risk and compliance writing is thick with vocabulary, and agent governance is inheriting
all of it. That is a real barrier to use: a control nobody understands is a control nobody
applies.

So the draft says what it means. The risk that is left, not residual risk. How far the
damage spreads, not blast radius. An agent login, not a non-human identity. An agent design
document, not a per-agent design and classification dossier. The README carries a table
that maps each plain term to the formal one other frameworks use, so you can still take
this into a room with an auditor.

## Three ideas doing the heavy lifting

Layer 2 is built as a ladder. Its bottom rung is reachable this sprint, for a single agent:
a login that agent shares with nothing else, credentials limited to only that agent's tools
and data, and a written way to revoke them. Higher rungs tie the credentials to the agent's
risk tier automatically, then to policy as code. The full enterprise model sits at the top
of the ladder instead of at the entrance.

Layer 4's monitoring gets the same treatment, because this is where the gap between what a
framework asks for and what most organizations can do today is widest. A useful first step
is narrow: log every tool call and its arguments, keep inputs and outputs for a fixed
period, and alert on a few coarse signals such as calls to tools outside the agent's
declared set. Full decision records, replay and scheduled tests are the destination, not
the entry price.

Layer 1 needs more than a list of tiers. It needs a test, so someone can walk through a
set of questions and show why a given agent is Tier 2 and not Tier 1 or 3, judged on how
sensitive its data is, how much money it can move, whether you can undo its actions, and
how far the damage spreads. Skip the test and every team declares its own agent low risk,
and now there is a document asserting that the risk was assessed. Tiers also drift. A new
model version or a new tool can push real behavior above what the paperwork claims, which
is why the test has to run again against what monitoring sees.

Layer 3 answers that test with one agent's own details rather than in the abstract, which
is what makes the design document more than a template: it carries the proof of its own
tier, and it is the document a reviewer reads to decide whether the agent is what it claims
to be. Nothing crosses into production on the strength of that claim alone. A named person
accepts the risk that is left and approves the agent to operate, on a recorded date,
against a specific version of the document. That approval is temporary, and the distinction
matters: when live behavior stops matching the description it was granted against, the
approval is not merely old, it is void until someone looks at it again. Without that, the
feedback loop from monitoring only informs.

## Fill this in with us

The structure is public so it can be argued with while arguing is still cheap. Tell us
whether five layers are the right five, whether one is missing, and whether something sits
in the wrong place.

The bigger invitation is the drafting. All five documents still have to be written, and the
group would like the people who will have to operate them in the room while that happens.
If you are scoping permissions for an agent this quarter, or arguing with an auditor about
what an agent's log has to contain, we would love to have you join the group.

Read the [layered model](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/agent-governance-layered-model.md),
then [open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues)
on the part you disagree with. The charter, minutes and deliverables are all in the open,
and the group meets bi-weekly.

Members of the working group will be at
[MACH X: Amsterdam](https://mach-x.machalliance.org/amsterdam/) on September 29 and 30. We
would love to meet with you there.

---

*The Agent Adoption & Operations Working Group is part of the MACH Alliance
[Agent Ecosystem](https://github.com/machalliance/agent-ecosystem) initiative. Its earlier
three-part position paper, [What Changed](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/what-changed-articles),
argues that frameworks are the organizational mechanism for scaling the mental model shift
agentic systems require.*
