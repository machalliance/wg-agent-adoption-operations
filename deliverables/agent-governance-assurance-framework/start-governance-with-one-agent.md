# Start Governance with One Agent, Not the Whole Enterprise

*A draft five-stage framework from the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft.*

Most enterprises we have talked to have an AI governance policy. Few could pick one agent in production and show that its behavior matches it.

The usual approach guarantees that. Agent governance gets scoped as an enterprise program: one platform standard, covering every agent, agreed by every team that owns one. That agreement can take longer than the agents take to reach production. Teams ship in the meantime, on shared logins, with no record of what an agent decided or why.

The MACH Alliance [Agent Adoption & Operations Working Group](https://github.com/machalliance/wg-agent-adoption-operations) has published a [draft structure](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/agent-governance-assurance-framework) built the other way around. A team can govern one agent in a sprint, without waiting for a standard that covers all of them.

## The stages hold each other up

A rule in your policy is true only if some agent's design applies it, the platform holds that agent to it, somebody named has accepted what is left, live behavior confirms it, and the record proves it. Break one of those links and everything resting on it is an empty claim. So the draft organizes the work as five connected stages, and not five documents that never mention each other.

| Stage | What you write | What it does |
|---|---|---|
| 1. Agent design | Agent Design Document | Records one agent: the outcome it is for, its purpose, the tools and the data it needs, its limits, and its classification |
| 2. Policy | Risk Classifications and the Classification Test | Holds your classifications of agent types and the risk each one carries, and gives you a test that places an agent in one of them |
| 3. Platform controls | Platform Control Levels, and a Platform and Sign-off Record per agent | Stands the agent up on a platform that holds it to the limits its design declares, and runs your evals against that setup. A named person then signs off before it goes live |
| 4. Live operations | Monitoring Levels, and a Monitoring and Incident Record per agent | Keeps those evals running against the live agent, and says what happens when one fails |
| 5. Audit and assurance | Audit Log Rules, and an Audit and Assurance Record per agent | Says what agents add to the records policy you already have, keeps proof of what the agent did, and proves that somebody is still reading the evals |

The table names four standards, and none of them is a policy you sit down and write. Two are assessments: score the platform your agent runs on against three short definitions, once, on each ladder. One is a conversation with whoever already owns your records policy, about what an agent adds to it. Only the risk classifications ask you to author anything, and the first pass is one row, for the one classification your agent belongs to. The set grows later, as you build agents it does not describe.

None of the five documents is finished when it is written. Each keeps reporting that something earlier needs work, which is the part most governance programs leave out. The full reasoning is in [the five stages](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/artifacts/five-stages.md). [What we reference and cite](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/references.md) sets out where the draft leans on existing work instead of restating it, including [AI TRiSM](https://www.gartner.com/en/articles/ai-governance-trism), [AIUC-1](https://aiuc-1.com/), the [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) and the Cloud Security Alliance's [agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/), ISO/IEC 42001, and [FIDO's agentic authentication work](https://fidoalliance.org/fido-alliance-to-develop-standards-for-trusted-ai-agent-interactions/).

## Plain words, on purpose

Risk and compliance writing is thick with vocabulary, and agent governance is inheriting all of it. That is a real barrier to use: a control nobody understands is a control nobody applies.

So the draft says what it means. The risk that is left, not residual risk. How far the damage spreads, not blast radius. An agent login, not a non-human identity. A risk classification, not a risk tier. The [glossary](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/glossary.md) maps each plain term to the formal one other frameworks use, so you can still take this into a room with an auditor.

Where the formal term is the clearer one, the draft keeps it. Least privilege stays least privilege, and an eval stays an eval. The people who scope an agent's permissions and the people who test its behavior already use those words, and replacing them would cost more than it explains.

## The parts that carry the weight

Stage 1 is one document per agent, and it comes first because nobody can judge an agent's risk from its name. It opens with the outcome the agent is for, how that outcome is measured, and who owns the number. Without that, there is no way to tell whether the agent is working, and no evidence on which to switch it off. It then lists the tools and the data the agent needs, which is where stage 3 gets its scope, and it closes by arguing for the agent's classification. That last part is what a reviewer reads to decide whether the agent is what it claims to be.

Stage 2 is the one stage that is not about a single agent. It describes the whole company: which kinds of agent you build, what each kind is allowed to do, and the controls that come with it. Rank the kinds by what the process is worth, what data the agent can reach, which regulations apply, how much money it can move, whether the action can be undone, and how far the damage spreads. It also needs the Classification Test, so somebody can walk through a set of questions and show why a given agent sits in one classification rather than the one above it. Skip the test and every team declares its own agent low risk.

None of that has to exist in full before you ship. You need the one classification your first agent belongs to, and the set grows as you build agents it does not yet describe. Classifications also drift. A new model version or a new tool can push real behavior above what the paperwork claims, which is why the test has to run again against what monitoring sees.

Stage 3 has three levels, and every one of them enforces least privilege. The difference between them is who sets the permissions, and what stops them drifting. Level 1 is reachable this sprint, for a single agent: an agent login it shares with nothing else, credentials covering only what the design document lists, and a written way to revoke it all. The model version and the host go on the agent's platform record, which is what the evals then run against. At Level 2 the agent's classification sets a ceiling that no engineer can grant past. At Level 3 policy as code grants and revokes the permissions, and checks continuously that they still match the classification. The full company-wide model is Level 3, which puts it at the end of the road and not at the start. A company can run on Level 1 for a long time.

Then run your evals against the platform you actually stood up, because an eval that passed against a different model version tells you about that model version. Nothing reaches production on the strength of a document: one named person signs off on the agent as a whole, on a recorded date, against a specific version of the design document, with the eval results in front of them. That sign-off is temporary. When live behavior stops matching the description it was granted against, it is void until somebody looks at it again. Without that, monitoring only informs.

Stage 4's monitoring has its own three levels, because this is where the gap between what a framework asks for and what most companies can do today is widest. They are a second climb, and they run independently of the first: an agent whose permissions are enforced in code can still be watched by nothing more than a log. Level 1 is narrow: log every tool call and its arguments, keep inputs and outputs for a fixed period, and alert on a few coarse signals such as calls to tools outside the agent's declared set. Level 2 stores run records and alerts on drift from the design document. Level 3 replays a run and tests it against known failure modes. Level 2 is where the evals start running without anybody remembering to start them, which is why the step from Level 1 costs more than storage.

Stage 5 does not write you a records policy, because you have one. It says what agents add to it: the record is free text rather than fields, re-running an agent does not reproduce the run, the model and tools move underneath the record, the identity in the log is the agent's rather than the person's, and four of the records outlive the agent. Retention periods and which regimes reach you belong to whoever owns them, and the stage points at where log evidence usually already sits instead of mapping it for you.

It then asks for two records. The first is the one an auditor already recognizes: what the agent did, which decisions it took, and who signed off. The second is the assurance record — where the eval results come from, whether they are still arriving, and what somebody concluded from reading them. The first shows what the agent did. The second shows that somebody is still checking, on a date after the sign-off, and it is the one that usually does not exist. Evals that run continuously make that harder rather than easier: a monthly schedule fails by stopping, which is visible, while a continuous one fails quietly, with green results nobody reads and an eval set that stops growing while the agent changes. So the record holds the reviews and not the runs, and it is what carries corrections back to the classifications and the designs.

## Fill this in with us

The structure is public so it can be argued with while arguing is still cheap. Tell us whether five stages are the right five, whether one is missing, and whether something sits in the wrong place.

The bigger invitation is the drafting. There is now a form for each of the five stages, with the reasoning behind it kept in a separate document so you can fill one in without reading an essay first.

They are drafts, and will improve with community application and feedback. That is the gap we are asking you to help us close.

If you are scoping permissions for an agent this quarter, or working out with your records team what an agent's log has to contain, take the relevant form, fill it in for a real agent, and tell us where it broke.

Read [the five stages](https://github.com/machalliance/wg-agent-adoption-operations/blob/main/deliverables/agent-governance-assurance-framework/artifacts/five-stages.md), take one of [the forms](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/agent-governance-assurance-framework/artifacts), then [open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues) on the part you believe can be improved.

Members of the working group will be at [MACH X: Amsterdam](https://mach-x.machalliance.org/amsterdam/) on September 29 and 30. We would love to meet with you there.

---

*The Agent Adoption & Operations Working Group is part of the MACH Alliance [Agent Ecosystem](https://agentecosystem.org) initiative. Its earlier three-part position paper, [What Changed](https://github.com/machalliance/wg-agent-adoption-operations/tree/main/deliverables/what-changed-articles), argues that frameworks are the organizational mechanism for scaling the mental model shift agentic systems require.*
