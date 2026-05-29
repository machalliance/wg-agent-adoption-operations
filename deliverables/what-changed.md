# What changed: A new mental model for the age of AI agents

*A position paper from the MACH Alliance Agent Adoption & Operations Working Group*

---

## Introduction

Something significant happened in the past two to three years, and most organizations have not yet fully reckoned with it. Artificial intelligence moved from a specialized capability available to a narrow technical community to a general-purpose system accessible to almost anyone. The speed of that shift was startling. But the more consequential change is qualitative, not quantitative, and it is easy to miss if you are not looking for it.

Enterprises are not missing AI. According to McKinsey's 2025 State of AI survey, 88 percent of organizations report regular AI use across at least one business function, and two-thirds deploy it across multiple functions. Yet only about one-third report scaling AI enterprise-wide, and just 6 percent qualify as high performers generating substantial, measurable business value. [1]

The gap between deployment and value is not primarily a technology problem. Organizations largely have access to the same capabilities. The gap is a comprehension problem. It's a mismatch between how AI agents actually work and the mental models most individuals and organizations use to make sense of them.

This paper argues that the comprehension gap is the main reason enterprises get stuck. It examines what changed, why the change is hard to absorb, and what it looks like when individuals and organizations genuinely "get it". The governance frameworks, operating models, and operational standards this working group is building rest on that foundation. They are to be designed for a world where the comprehension problem has been taken seriously, not assumed away.

---

## What actually changed

For most of AI's commercial history, systems were narrow and task-specific. A system that recommended products had no capacity to process a customer complaint. A fraud detection model had no ability to query a database or draft a response. Narrow systems were powerful within their domains, but they operated in isolation and required explicit human orchestration at every transition.

That boundary has dissolved. Modern AI systems reason across domains, integrate information from diverse sources, and take actions in the world. They call APIs, execute code, search the web, interact with enterprise systems, send messages, and trigger workflows. 

They do not just respond to questions. They can pursue goals across multi-step sequences and adapt their approach based on intermediate results.

The capability acceleration has been hard to track in real time. Stanford HAI's 2025 AI Index found that AI systems could solve 4.4 percent of professional software engineering problems in 2023. By 2024, that figure was 71.7 percent (a 67-point increase in a single year). On the GPQA benchmark, designed to test expert-level scientific reasoning, AI performance improved nearly 49 percentage points in the same period. In some software engineering contexts, agentic AI systems began outperforming humans given comparable time constraints. [2]

Two features of this shift matter most for how organizations need to think and operate. 

The first is that AI output is generative and probablistic, not deterministic. Traditional software executes defined logic and produces predictable outputs given known inputs. AI systems generate from patterns and probability. The same input can produce different results across runs, and the system can produce things it was never explicitly programmed for. That is *not* a flaw, but rather it is the point. 

The second is that modern agents take actions, not just produce suggestions. Earlier AI systems offered outputs that humans then acted upon (e.g., a recommendation, a draft, a classification). Agentic systems act. They initiate requests, modify data, trigger processes, and interact with other systems on behalf of the organizations that deploy them. Actions have consequences that suggestions do not, specifically, because they remove the human accountability layer.

Together, these two features are what make this moment different from previous enterprise technology shifts. They are also what make existing mental models unreliable.

---

## The mental models we carry, and why they fail

Humans reach for familiar patterns when something new shows up. That is efficient and mostly harmless. With agentic AI, it is creating a widespread and costly misalignment. Thus, three mental models dominate how people currently make sense of AI. 

The first is the **tool model**. A tool does what you direct it to do. It is deterministic, scoped, and fully under human control. When people think of AI agents as slightly smarter calculators, they tend not to ask the governance questions that matter. Who is responsible for the agent's decisions? What happens when it encounters an ambiguous situation? What limits its authority to act? What does "wrong" mean?

The second is the **search engine model**. A search engine retrieves and presents information. It does not make decisions, take actions, or carry context between queries. People who map AI agents onto this model focus on output quality (e.g., Is the answer accurate?) while underestimating the significance of the system's ability to act. People also tend to underrate the importance of understanding how it arrived at an answer, not just what the answer says.

The third is the **traditional software model**. Enterprise software is built for auditability and predictability. Requirements are specified. Behavior is tested. Deviations are bugs. Governance frameworks and operational procedures were designed for systems where a defined rule produced a defined outcome. AI agents behave probabilistically and contextually. Governance built for deterministic software will miss the failure modes that matter most with agents or argubaly worse, will define failure modes that aren't in fact failures.

---

## The individual click: seeing problems differently

Among people who work extensively with AI agents, a common experience gets described with notable consistency. At some point, something shifts. Before the shift, you use AI to assist with tasks you already know how to do. After it, you approach problems differently from the outset: not "how do I do this, and can AI help?" but "how does this problem look if I think it through with AI?"

The shift is hard to describe precisely because it is not about a new fact learned. It is a change in perception, closer to how a skilled reader sees a sentence differently than a beginning reader does.

What does this looks like in practice? 

As an example: before the shift, you encounter a complex dataset and think you need to build a spreadsheet to run some analysis. It's about knowing the right formulas, how to use pivot tables, and how to format the output for easy consumption.

After the shift, you work through the analysis in partnership with an agent. It builds and executes the code, you evaluate the outputs and redirect, and you iterate together. You start to see yourself as an orchestrator and evaluator of an AI system that *does the work* instead of as the entity that executes the work.

Another example is when you need to research an unfamiliar domain. Instead of queuing up reading, you engage an agent to reason across source material and surface contradictions. You see yourself as the evaluator of research and synthesis that an AI performed, not as the entity that does the research and synthesizes the information.

These are not trivially different approaches. They represent a different theory of where judgment lives in a workflow. 

In the pre-shift model, human judgment organizes the work and AI assists with execution. In the post-shift model, the boundary between judgment and execution is fluid. The human provides direction and evaluation while the agent handles a much wider range of cognitive and operational work. Importantly, the loop between them is continuous.

But, what produces the shift? That's the key to unlocking individual and organizational change.

It's achieved through sustained, reflective exposure to AI on real problems. It's not acheived through awareness and not through one-time experimentation. Reading about AI capabilities does not produce it. Using AI on work that actually matters, long enough to develop genuine intuition about where it performs, where it fails, and how to work with it effectively is what does it.

It's also worth being clear about what the shift is not. It is not blind trust of the AI. People who have made the shift tend to be clearer-eyed about where AI agents make mistakes, where they require supervision, and where they should not be given authority to act. 

What changes is how the problem space looks. What questions get asked at the start, what work feels tractable, and what kinds of help feel natural to seek? Anyone who has spent real time with AI agents will recognize the change. The harder problem is that most enterprise processes and governance structures were built by people who have not gone through it it yet.

---

## The organizational equivalent

What does an organization look like when it has made this shift collectively?

The honest answer is that very few have. Most are at an earlier stage: enough individual practitioners have made the shift that AI adoption is spreading internally, but the organization's structures, governance, roles, and operating models were designed for a pre-agentic world. The result is capability without accountability. Agents act in the enterprise without clear ownership, oversight structures, or operational governance. And, that is if agents are given the ability to act at all!

An organization that has made the shift will have solved a specific set of concrete problems. There is shared vocabulary for what agents can and cannot do, not invented independently by each team. Governance conversations happen before deployment. The question "are we ready to operate this agent?" is asked before launch, not raised reactively after something goes wrong. 

Accountability is clear. Someone owns each agent in production, someone monitors its behavior, someone has the authority to shut it down. These sound obvious. Most organizations deploying agents today cannot answer them.

Two failure modes are common. In the first, an organization deploys agents in an environment of enthusiasm without building the operational capability to supervise them. Agents take actions, produce unexpected negative results, and the organization lacks the observability, accountability structures, or incident response processes to understand what happened or prevent recurrence. This erodes trust in AI broadly and likely stalls progress.

In the second, an organization imposes legacy governance frameworks on AI agents, treating them like traditional software or like human employees, and finds that neither the frameworks nor the agents function as intended. Agents get locked down to the point of uselessness, or governance requirements designed for traditional, deterministic systems produce false confidence when applied to probabilistic ones.

Governments and standards bodies have landed on similar conclusions. The EU AI Act (Regulation (EU) 2024/1689), which entered into force in August 2024, establishes binding requirements for how organizations deploy AI systems: human oversight, automatic logging, risk management procedures, and transparency obligations for high-risk systems. [5] The NIST AI Risk Management Framework, released in January 2023, structures AI governance around four core functions: Govern, Map, Measure, and Manage. These frame AI systems as a category that requires its own accountability architecture, not an extension of existing software governance. [4] 

Neither document treats AI agents as a slightly more capable version of previous systems. Both treat them as a different kind of system that needs different kinds of oversight.

---

## Why the shift is hard: specific barriers

The mental model shift does not happen automatically, even with direct exposure to AI. Naming the specific barriers helps organizations address them rather than waiting for them to resolve on their own.

At the individual level, the most well-documented barrier is automation bias. Research by Parasuraman and Manzey, published in Human Factors in 2010 and now with over a thousand citations, established that people operating alongside automated systems systematically over-rely on those systems, even after gaining experience with them. Critically, this is not overcome by simple practice. It is a structural feature of how human attention works in multi-task environments. [3] The individual click carries a risk: the shift in how problems are perceived can shade into insufficient oversight of what agents actually do.

Other individual barriers include:
- Personal willingness to adopt AI based on biases about the tech
- Bandwidth and cognitive capacity to learn the new technology
- Confusion or overwhelm caused by market messages and news about AI

The second individual barrier is early-failure dismissal. Someone tries AI on a problem, gets a poor result, and concludes the technology is unreliable. This is usually less a judgment about capability than about fit. AI agents perform very differently across problem types, and a bad early experience with one kind of task predicts little about performance on others. Organizations that do not create structured, guided exposure to AI risk allowing early failures to calcify into resistance that is hard to reverse.

At the organizational level, the most significant barrier is framing AI adoption as a technology evaluation rather than an organizational capability build. Technology evaluations have an endpoint: you assess a tool, decide whether to adopt it, then deploy it. Capability development does not have such an endpoint. You build the skills, processes, structures, and operating models that allow a new kind of work to be done well over time. AI adoption structured as a technology evaluation tends to produce pilots. Structured as capability development, it creates the environment to produce sustained value.

A related barrier is leadership-team misalignment. In many organizations, the people most excited about AI's potential are driving faster and broader adoption, while risk, legal, compliance, and operations teams are applying legacy frameworks that were not designed for probabilistic, agentic systems. Neither instinct is wrong. The challenge is that they are operating on different mental models, and the resulting friction produces neither sufficient governance nor sufficient adoption.

---

## Moving through the shift

The frameworks, operating models, and checklists this working group is developing help organizations move through the shift at scale. Before those frameworks, below are some orienting principles.

For individuals, sustained exposure on real problems matters more than training or awareness. Demonstration sessions raise awareness, but they do not produce "the click". People need to use AI agents on work that actually matters to them, long enough to develop genuine intuition. They need more than just access to the tools. They need deliberate practice on meaningful work. Organizations that want to accelerate individual adoption need to create the conditions for that exposure.

Teams need to do this together. Shared exposure creates shared vocabulary, and shared vocabulary is what makes governance conversations concrete rather than abstract. Teams that have worked through real problems with AI can discuss its capabilities and limitations specifically. Teams that have not tend to talk past each other at a level of generality that makes it hard to agree on anything actionable.

For organizations, the reframe that matters most is that AI adoption is not a technology evaluation. It is instead an operational capability to be developed. Technology evaluations have an end date. Capability development does not. Organizations that invest in roles, monitoring infrastructure, and shared process alongside agent deployment compound their returns. Those that treat it as a deployment project tend to hit a ceiling where governance failures create enough friction that adoption stalls.

---

## Why frameworks are the organizational mechanism

The individual mental model shift is necessary. It is not enough.

A single practitioner who has internalized the generative, agentic nature of AI cannot, by doing so alone, produce accountable, well-governed AI deployment across an enterprise. The insight needs to be institutionalized. It needs to be encoded into processes, roles, shared vocabulary, and operational structures that persist beyond any individual and function without requiring every person involved to have had "the click" independently.

This is what governance frameworks, operating models, and readiness standards do. They are not bureaucratic overhead imposed on AI. They are the organizational mechanism for scaling the mental model shift. A governance framework that asks "who owns this agent in production, and how is its behavior monitored?" is asking the questions that an individual who has made the shift would ask. And, it asks them systematically, before deployment, for every agent, regardless of which team built it.

The six proposed deliverables from this working group reflect this logic directly:

1. The *Enterprise Agent Adoption Framework* gives organizations a structured path from experimentation to scaled operational capability, preventing the pilot stagnation that results when adoption outpaces operational readiness.
2. The *Enterprise Agent Operating Model* defines roles, ownership, and accountability across the organization, ensuring that agents in production have owners, not just builders.
3. The *Agent Governance Framework* encodes the judgment calls that individuals with the right mental model make intuitively: when agents should act autonomously, when they should escalate, and how authority boundaries get defined.
4. The *Agent Production Readiness Checklist* asks the organizational equivalent of the shift question ("Are we ready to operate this?") before deployment, not after failures.
5. The *Agent Operations Playbook* provides the operational structures for monitoring, incident response, and lifecycle management that agents require as long-lived production systems.
6. The *Agent Observability Model* addresses the specific challenge of understanding what a probabilistic, goal-pursuing system actually did and why, which is a different problem from debugging deterministic software.

Together, these give organizations a way to operate in the post-shift world even before everyone has had the individual "click". They distribute the insight.

---

## Conclusion

The mental models that enterprises use to make sense of AI agents are being established now in how organizations structure pilots, in how governance conversations get framed, in what roles get created, in what questions leaders learn to ask. Once those models are set, they are difficult to revise.

Organizations that do this work now will have a different kind of advantage: not better access to AI capabilities, but genuine operational maturity. They will know how to govern agents at scale because they built the structures for it early, not just because it seemed like the right thing to do in retrospect.

Organizations that delay, or that try to manage agentic AI with frameworks designed for different kinds of systems, will encounter a version of the ceiling that already shows up in the data: widespread deployment, limited value, and a growing gap between what AI agents could do and what the organization can safely permit.

The deliverables this working group is building are practical instruments (shared vocabulary, operational frameworks, governance guidance) for helping more organizations make the shift faster and more safely. That work has to start somewhere. It starts with being honest about what changed.

---

*This position paper is published by the MACH Alliance Agent Adoption & Operations Working Group, part of the MACH Alliance Agent Ecosystem initiative. Working group membership, charter, and deliverables are maintained at [github.com/machalliance/wg-agent-adoption-operations](https://github.com/machalliance/wg-agent-adoption-operations).*

---

## Sources

1. McKinsey & Company. "The State of AI: Agents, Innovation, and Transformation." November 2025. https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai
2. Stanford Institute for Human-Centered AI. "The 2025 AI Index Report." April 2025. https://hai.stanford.edu/ai-index/2025-ai-index-report
3. Parasuraman, R., & Manzey, D. H. "Complacency and Bias in Human Use of Automation: An Attentional Integration." *Human Factors: The Journal of the Human Factors and Ergonomics Society*, 52(3), 381–410. June 2010. https://journals.sagepub.com/doi/10.1177/0018720810376055
4. National Institute of Standards and Technology. "AI Risk Management Framework (AI RMF 1.0)." January 2023. https://www.nist.gov/itl/ai-risk-management-framework
5. European Parliament and Council of the European Union. "Regulation (EU) 2024/1689 Laying Down Harmonised Rules on Artificial Intelligence (Artificial Intelligence Act)." August 2024.
