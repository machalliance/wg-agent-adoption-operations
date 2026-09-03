# Notes on the Monitoring Levels

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Monitoring Levels](monitoring-levels.md): why the levels are drawn where they are, and what we would like your feedback on. You do not need to read it to use the standard.

---

## Notes on the hard parts

### Why monitoring gets its own ladder

Stage 3 already has levels, and adding a second set risks turning the framework into a set of scores instead of a way of working.

We kept them separate because they fail independently. Enforcing permissions in code tells you nothing about whether anyone would notice the agent behaving oddly inside those permissions. The combination we see most often is strong control and weak visibility: the platform team solved access because access is a solved problem elsewhere in the company, and nobody owns the question of whether the agent is doing a good job.

Two numbers make that combination visible on the record. One number would average it away.

### Why the line between Level 1 and Level 2 is where it is

Level 1 tells you what happened when you go looking. Level 2 tells you without being asked, and that is the expensive step.

Storing full run records is a cost decision somebody can approve in an afternoon. Getting evals onto a schedule that survives a busy quarter is an ownership decision, and it is where most monitoring programs stall: the traces exist, the evals exist, and nothing runs them.

### Why Level 3 mentions stage 5

Because replay and tamper-resistance are the same investment, and it is wasteful to make it twice.

Once you can reconstruct a run exactly, you are most of the way to a record an auditor accepts. The remaining work is that the operating team must not be able to alter it. We put that requirement here so that a team building replay does not have to rebuild it later for a different reader. It is the only stage 5 requirement that appears anywhere else in the framework.

### Why the level describes a platform

We took this from the [Platform Control Levels](../03-platform-controls/platform-control-levels.md), which made the same choice for the same reason.

What your observability stack collects is a property of the stack. Scoring it per agent would produce forty answers to a question with one answer, and scoring it per company would be wrong for every team that runs agents somewhere else.

### Why two destinations in part 4 rather than one

The stage 3 standard points at a single deeper source. This one cannot, because the stage has two unrelated halves.

What to record is a data-shape problem, and OpenTelemetry's conventions are the answer. What to watch for is a threat-modeling problem, and OWASP's list is the answer. Neither covers the other. Sending readers to one and letting them assume it covers both would be worse than admitting the split exists.

OpenTelemetry's agent spans are still marked experimental, and their attributes moved out of the main semantic-conventions repository into a dedicated one during 2026. Check the current status and location before wiring anything to them.

### The gap this raised in our own forms

Writing this standard showed that the record was asking for one monitoring level where there are two: the platform's and the agent's. The record now asks for both, in the same shape stage 3 uses.

It also showed that nothing in the framework asked who owns a standard. A standard nobody owns does not get revised, and an unrevised standard is the thing every agent is judged against. There is now an owner block on all four standards.

---

## Where this comes from

| Part | Who else asks for it |
|---|---|
| Levels 1 to 3 | AWS [AGENTOPS05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops05.html) for tracing and anomaly detection, and [AGENTOPS06](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops06.html) for evaluation frameworks, because agent behavior is stochastic and deterministic testing alone will not do. |
| Observability as a first principle | Google's [approach for secure AI agents](https://research.google/pubs/an-introduction-to-googles-approach-for-secure-ai-agents/) makes it one of three: an agent's actions and planning must be observable. |
| What a trace should contain | The [OpenTelemetry GenAI semantic conventions](https://opentelemetry.io/blog/2026/genai-observability/) define span names, attributes, metrics and events for model calls, tool executions, agent runs, retrieval and memory. [Vercel](https://vercel.com/i/ai-agent-observability) and [LangSmith](https://docs.langchain.com/langsmith/observability) both argue for the same minimum set. |
| Production traces becoming tests | [LangSmith](https://www.langchain.com/resources/agent-observability) turns production failures into regression datasets, which is the Level 3 requirement stated as a practice. |
| Maturity as two axes | OWASP's [State of Agentic AI Security and Governance v2.01](https://genai.owasp.org/resource/state-of-agentic-ai-security-and-governance/) pairs an adoption tier with a governance maturity level. |
| Products that do this for you | [Gartner's guardian agents](https://www.gartner.com/en/newsroom/press-releases/2026-04-28-gartner-identifies-six-steps-to-manage-artificial-intelligence-agent-sprawl) are agents that supervise other agents, for visibility, continuous assurance and runtime enforcement. |

## What this standard is not

**It is not an observability strategy.** It says nothing about which tools to buy or how to instrument them. It says what has to be true, so that the level on a sign-off means something.

**It is not stage 5.** Level 3 requires records the operating team cannot alter, which is the one stage 5 concern borrowed early because it is the same investment as replay. Retention and legal hold are set by your records policy, and the [Audit Log Rules](../05-audit-and-assurance/audit-log-rules.md) say what agents add to it.

## What we want feedback on

1. **Is the Level 1 to Level 2 boundary in the right place?** We put the eval that runs without a person at Level 2. It may be the single most valuable thing in the ladder and belong at Level 1.
2. **Is the platform-versus-agent split worth two numbers here as well?** It is consistent with stage 3. It is also more form-filling.
3. **Does Level 3 borrow too much from stage 5?** Tamper-resistance may not belong in a monitoring ladder at all.
4. **Are two deeper destinations one too many?** Splitting the reader between OpenTelemetry and OWASP may just mean they go to neither.
5. **Does anybody run at Level 3 today?** We would like to see one.

[Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues) with the level you are actually on and what is stopping the next one.
