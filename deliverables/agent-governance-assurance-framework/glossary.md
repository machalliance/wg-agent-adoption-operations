# Glossary

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

Risk and compliance work has a large vocabulary. We use plain words instead, so that the people who have to apply a control can understand it. This table gives our word, what it means, and the word that other frameworks use for the same thing.

Where the formal term is already the clearest one, we keep it. Those rows say so in the last column, and they are here because you will meet them throughout the forms.

| We say | It means | Other frameworks say |
|---|---|---|
| agent | A system where an AI model evaluates context and makes decisions that shape what the system does. A model generating or transforming content inside a flow somebody else authored sits below that line and is not an agent. Everything above it is, and the governance this framework asks for rises with how much the agent decides alone. | agentic system, AI agent |
| agent design document | One document that records what one agent does and what it can touch. | system card, model card, design dossier |
| agent login | An account that belongs to one agent and to nothing else, reaching only the tools and the data that this one agent needs. | service identity, non-human identity, workload identity |
| assurance | The record that your checks keep running: where the eval results come from, who read them, when, and what changed because of it. It is separate from the records themselves. | continuous assurance, ongoing monitoring, control testing |
| baseline | The eval results recorded at sign-off. Later results are measured against it, so a change in behavior shows up as a difference somebody can act on. | reference run, golden set, control baseline |
| classification test | The eight questions in your Risk Classifications that place one agent in one classification. Each answer sets a floor, and the highest floor wins. | risk assessment questionnaire, triage assessment |
| drift | Live behavior moving away from what the agent's design document says it does, with nobody having changed the code. | behavioral drift, configuration drift |
| eval | A test that runs against the agent without a person starting it — continuously, on every deploy, or on a schedule — to check that it still behaves the way its design document says. We keep this term, because the people who build agents already use it. | evaluation, offline eval, behavioral test, red-team test |
| floor | The lowest classification an agent can be in, given one answer to the classification test. The agent's classification is the highest floor any single answer sets. | minimum tier, risk floor |
| grant list | The table of tools and data an agent needs, in its design document. Stage 3 grants what is on it and refuses the rest. | entitlements, scope, permission set |
| guardian agent | An agent whose work is watching other agents: what they did, whether it looked normal, and whether to stop them. We keep this term, which is Gartner's. | guardian agent, agent supervision |
| how far the damage spreads | How far a mistake travels beyond the system the agent acted on. | blast radius |
| incident playbook | The second half of the Monitoring and Incident Record: what happens once an alert fires, and who does it. | runbook, incident response plan |
| least privilege | An agent gets the tools and the data its design document lists, and nothing else. We keep this term, because the people who scope permissions already use it. | least privilege, minimum necessary access |
| level | One of three degrees of maturity for a single part of the framework. Level 1 is small and quick. Level 3 is the full model. | maturity model, maturity level |
| level, of a platform | The strongest control, or the most visibility, a platform can provide. Scored once per platform, in a standard. | platform capability, control baseline |
| level, of an agent | What was actually applied to one agent. Recorded in that agent's record. It can be lower than its platform's level and can never be higher. | effective control, applied baseline |
| monitoring plan | The first half of the Monitoring and Incident Record: what you record on every run, what counts as normal, and what starts an alert. | post-market monitoring plan, observability plan |
| outcome | What the agent is for, stated as something you can measure, with one person who owns the number. | business outcome, success metric, KPI |
| platform | Where an agent runs and where its access comes from: the host, whatever issues its login, and whatever grants or refuses its tool calls. Most companies have several, controlled to different degrees, so each is scored on its own. Two agents whose credentials and tool access come from different places are on different platforms. | runtime environment, execution environment, control plane |
| policy as code | Permissions written as rules a machine grants and revokes from, instead of settings a person clicks. It is what separates platform control Level 3 from Level 2. | policy as code, attribute-based access control |
| prompt injection | Content the agent reads talking it into something its instructions did not intend. We keep this term; there is no plainer one that means the same thing. | prompt injection, indirect prompt injection, goal hijack |
| record | A document about one agent. You keep one per agent and revise it when that agent changes. Everything except the four standards is a record. | artifact, per-system documentation |
| replay | Re-running a stored run from its own record to see what happened. Re-running the *agent* is a different thing, and produces a different run. | trace replay, session reconstruction |
| risk classification | A type of agent and the level of risk that it carries, from low to high. Each classification gets stronger controls. Your classifications describe the whole company, not one agent. | risk tier, autonomy level |
| sign-off | A record of who accepted the risk, on what date, and against which version of the design document. | risk acceptance, authorization to operate |
| standard | A document about your whole company. You write it once and it grows. There are four: the Risk Classifications, the Platform Control Levels, the Monitoring Levels and the Audit Log Rules. | policy, control standard |
| the risk that is left | The risk that stays after you add your controls. | residual risk |
| tool call | One action that the agent takes through a tool: a search, a write, a payment, an email. | function call, action invocation |
