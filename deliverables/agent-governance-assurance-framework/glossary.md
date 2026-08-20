# Glossary

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

Risk and compliance work has a large vocabulary. We use plain words instead, so that the people who have to apply a control can understand it. This table gives our word, what it means, and the word that other frameworks use for the same thing.

| We say | It means | Other frameworks say |
|---|---|---|
| agent design document | One document that records what one agent does and what it can touch. | system card, model card, design dossier |
| agent login | An account that belongs to one agent and to nothing else, reaching only the tools and the data that this one agent needs. | service identity, non-human identity, workload identity |
| assurance | The record that your checks keep running: which evals ran, when, what they found, and what you did about it. It is separate from the records themselves. | continuous assurance, ongoing monitoring, control testing |
| eval | A test that you run against the agent, on a schedule and without a person starting it, to check that it still behaves the way its design document says. We keep this term, because the people who build agents already use it. | evaluation, offline eval, behavioral test, red-team test |
| how far the damage spreads | How far a mistake travels beyond the system the agent acted on. | blast radius |
| level | One of three degrees of maturity for a single part of the framework. Level 1 is small and quick. Level 3 is the full model. | maturity model, maturity level |
| outcome | What the agent is for, stated as something you can measure, with one person who owns the number. | business outcome, success metric, KPI |
| risk classification | A type of agent and the level of risk that it carries, from low to high. Each classification gets stronger controls. Your classifications describe the whole company, not one agent. | risk tier, autonomy level |
| sign-off | A record of who accepted the risk, on what date, and against which version of the design document. | risk acceptance, authorization to operate |
| the risk that is left | The risk that stays after you add your controls. | residual risk |
| tool call | One action that the agent takes through a tool: a search, a write, a payment, an email. | function call, action invocation |
