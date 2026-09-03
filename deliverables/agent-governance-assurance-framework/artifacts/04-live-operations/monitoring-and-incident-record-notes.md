# Notes on the Monitoring and Incident Record

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Monitoring and Incident Record](monitoring-and-incident-record.md): the three monitoring levels, why the sections are ordered as they are, and what we would like your feedback on. You do not need to read it to fill the form in.

---

## The three monitoring levels

They are defined in the [Monitoring Levels](monitoring-levels.md), which also explains why they climb separately from the platform control levels and why the level describes a platform rather than an agent.

## Notes on the hard parts

### Why what runs the evals is the load the section carries

An eval that a person has to remember to run is not assurance, because the remembering is the first thing dropped in a busy quarter.

This is why section B asks what starts the evals, and then asks how you would find out if they stopped. Whatever runs them, a scheduler that died and a continuous job that quietly stopped both look the same from outside: everything is green because nothing is running.

### Why section C asks which alerts are actually implemented

Because the answer is usually "two of the seven", and a document that does not ask will happily record all seven.

Asking it moves the gap into the sign-off, where a named person either accepts it or funds it.

### Why section E lists failure modes explicitly

Most teams already have an incident process, and it is built for software that fails deterministically: a service is down, a query is slow, a deploy broke a page. Agents fail differently. They succeed at every individual step and produce a wrong outcome. They are talked into things by content they read. They quietly get used for work nobody designed them for.

The list is a checklist, because we are after coverage rather than narrative. Eleven rows with six honest "not covered" answers tell you more than eleven rows of untested prose.

The list is drawn from [OWASP's Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/), which is the closest thing to an agreed taxonomy of how these systems fail. If you want a threat model instead of a playbook, start there.

### Why "who can change these records" is in section A

Stage 5 needs records that an auditor will accept, and a log the operating team can edit is not one. Asking the question here, while you are choosing where logs go, is much cheaper than discovering it during an audit.

### Guardian agents

A group of products is emerging to do parts of this work: agents that supervise other agents, for visibility, continuous assurance and runtime enforcement. [Gartner calls them guardian agents](https://www.gartner.com/en/newsroom/press-releases/2026-04-28-gartner-identifies-six-steps-to-manage-artificial-intelligence-agent-sprawl).

Whether you buy one or build it, this stage is where it sits. This form is what tells you whether it covers what you need, and its last row in section E is there because a supervising agent is another agent, with its own failure modes and its own need for a record like this one.

---

## Where each section comes from

| Section | Who else asks for it |
|---|---|
| A. What you record | AWS [AGENTOPS05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops05.html) asks for tracing, anomaly detection and operational dashboards. Google's [approach for secure AI agents](https://research.google/pubs/an-introduction-to-googles-approach-for-secure-ai-agents/) makes observability one of three principles: an agent's actions and planning must be observable. [Vercel](https://vercel.com/i/ai-agent-observability) and [LangSmith](https://docs.langchain.com/langsmith/observability) both argue for capturing tool calls, inputs, outputs and metadata as the minimum useful trace. |
| B. Evals that run without a person | AWS [AGENTOPS06](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentops06.html) establishes testing and evaluation frameworks because agent behavior is stochastic. [LangSmith](https://www.langchain.com/resources/agent-observability) turns production traces into regression datasets, which is the mechanism this section is asking you to schedule. [AIUC-1](https://aiuc-1.com/) pairs a governance audit with recurring adversarial testing, not one annual review. |
| C. Normal, and what alerts | OWASP's governance maturity model puts real-time anomaly detection and working kill switches at its Level 3. AWS [AGENTSEC07](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentsec07.html) is about protecting human oversight and detecting rogue agents. |
| D. What an alert starts | AWS [AGENTSEC04](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentsec04.html) pairs guardrails with human-in-the-loop for critical decisions. [Anthropic's framework](https://www.anthropic.com/news/our-framework-for-developing-safe-and-trustworthy-agents) puts keeping humans in control first, and treats the ability to stop and redirect an agent as part of that. |
| E. Failure modes | [OWASP Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/): goal hijack, tool misuse, identity and privilege abuse, supply chain, unexpected code execution, memory and context poisoning, insecure inter-agent communication, cascading failures, human-agent trust exploitation, and rogue agents. |
| The three levels | OWASP's [State of Agentic AI Security and Governance v2.01](https://genai.owasp.org/resource/state-of-agentic-ai-security-and-governance/) pairs an adoption tier with a governance maturity level, which is the same two-axis idea as our platform control levels and monitoring levels. |

## What this record is not

**It is not your observability stack.** The tools are yours: OpenTelemetry, whatever backend you already run, a guardian agent, or a vendor platform. This is the document that says what you decided to watch and what you decided to do about it. It should be readable by somebody who cannot log into any of those tools.

**It is not a substitute for the design document.** Section D points at section 5 of the design document for how the agent is stopped, instead of restating it. Two documents describing the same kill switch will disagree within a quarter.

**It is not stage 5.** The records this section produces are for operators: debugging, triage, understanding what happened. Turning them into evidence an auditor accepts is a separate job with different requirements, and it is in the [Audit and Assurance Record](../05-audit-and-assurance/audit-and-assurance-record.md).

## What we want feedback on

1. **Is section E the right list?** It is OWASP's taxonomy turned into a playbook checklist. Tell us which rows are missing, and which are unanswerable in practice.
2. **Is "which alerts are actually implemented" a question teams will answer honestly?** It is the most useful question in the form and the easiest to fudge.
3. **Should monitoring level be a requirement of a classification, or a recorded fact?** Stage 2 currently makes it a requirement, which means a classification can demand maturity a company does not have.
4. **Where should cost belong?** We put runaway cost in section E as a failure mode and cost signals in section C. It may be a financial control rather than a governance one.
5. **Does the split between this and stage 5 hold?** The line we drew is operator versus auditor. It may be the wrong line, or one nobody can maintain in a single logging pipeline.

Section E in particular is a list we expect to be wrong within a year. [Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues).
