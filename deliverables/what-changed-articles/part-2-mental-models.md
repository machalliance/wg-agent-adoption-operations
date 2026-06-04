# What changed (Part 2 of 3): The mental models we carry

*A three-part position paper from the MACH Alliance Agent Adoption & Operations Working Group*

> **Series — *What changed: A new mental model for the age of AI agents*** \
> Part 1 · What actually changed | Part 2 · The mental models we carry | Part 3 · Moving through the shift

---

*Previously in this series — Part 1 described what actually changed: modern AI is generative and probabilistic rather than deterministic, and agents now take actions rather than only making suggestions. This part turns to why that change is so hard to absorb.*

---

## The mental models we carry, and why they fail

Humans reach for familiar patterns when something new shows up. That is efficient and mostly harmless. With agentic AI, it is creating a widespread and costly misalignment. Thus, three mental models dominate how people currently make sense of AI. 

The first is the **tool model**. A tool does what you direct it to do. It is deterministic, scoped, and fully under human control. When people think of AI agents as slightly smarter calculators, they tend not to ask the governance questions that matter. Who is responsible for the agent's decisions? What happens when it encounters an ambiguous situation? What limits its authority to act? What does "wrong" mean?

The second is the **search engine model**. A search engine retrieves and presents information. It does not make decisions, take actions, or carry context between queries. People who map AI agents onto this model focus on output quality (e.g., Is the answer accurate?) while underestimating the significance of the system's ability to act. People also tend to underrate the importance of understanding how it arrived at an answer, not just what the answer says.

The third is the **traditional software model**. Enterprise software is built for auditability and predictability. Requirements are specified. Behavior is tested. Deviations are bugs. Governance frameworks and operational procedures were designed for systems where a defined rule produced a defined outcome. AI agents behave probabilistically and contextually. Governance built for deterministic software will miss the failure modes that matter most with agents or arguably worse, will define failure modes that aren't in fact failures.

---

## The individual click: seeing problems differently

Among people who work extensively with AI agents, a common experience gets described with notable consistency. At some point, something shifts. Before the shift, you use AI to assist with tasks you already know how to do. After it, you approach problems differently from the outset: not "how do I do this, and can AI help?" but "how does this problem look if I think it through with AI?"

The shift is hard to describe precisely because it is not about a new fact learned. It is a change in perception, closer to how a skilled reader sees a sentence differently than a beginning reader does.

What does this look like in practice? 

As an example: before the shift, you encounter a complex dataset and think you need to build a spreadsheet to run some analysis. It's about knowing the right formulas, how to use pivot tables, and how to format the output for easy consumption.

After the shift, you work through the analysis in partnership with an agent. It builds and executes the code, you evaluate the outputs and redirect, and you iterate together. You start to see yourself as an orchestrator and evaluator of an AI system that *does the work* instead of as the entity that executes the work.

Another example is when you need to research an unfamiliar domain. Instead of queuing up reading, you engage an agent to reason across source material and surface contradictions. You see yourself as the evaluator of research and synthesis that an AI performed, not as the entity that does the research and synthesizes the information.

These are not trivially different approaches. They represent a different theory of where judgment lives in a workflow. 

In the pre-shift model, human judgment organizes the work and AI assists with execution. In the post-shift model, the boundary between judgment and execution is fluid. The human provides direction and evaluation while the agent handles a much wider range of cognitive and operational work. Importantly, the loop between them is continuous.

But, what produces the shift? That's the key to unlocking individual and organizational change.

It's achieved through sustained, reflective exposure to AI on real problems. It's not achieved through awareness and not through one-time experimentation. Reading about AI capabilities does not produce it. Using AI on work that actually matters, long enough to develop genuine intuition about where it performs, where it fails, and how to work with it effectively is what does it.

It's also worth being clear about what the shift is not. It is not blind trust of the AI. People who have made the shift tend to be clearer-eyed about where AI agents make mistakes, where they require supervision, and where they should not be given authority to act. 

What changes is how the problem space looks. What questions get asked at the start, what work feels tractable, and what kinds of help feel natural to seek? Anyone who has spent real time with AI agents will recognize the change. The harder problem is that most enterprise processes and governance structures were built by people who have not gone through it yet.

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

*Next in this series — Part 3: the specific barriers that hold the shift back, how organizations move through it, and why governance frameworks are the mechanism for scaling it.*

---

## Sources

4. National Institute of Standards and Technology. "AI Risk Management Framework (AI RMF 1.0)." January 2023. https://www.nist.gov/itl/ai-risk-management-framework
5. European Parliament and Council of the European Union. "Regulation (EU) 2024/1689 Laying Down Harmonised Rules on Artificial Intelligence (Artificial Intelligence Act)." August 2024.

---

*This position paper is published by the MACH Alliance Agent Adoption & Operations Working Group, part of the MACH Alliance Agent Ecosystem initiative. Working group membership, charter, and deliverables are maintained at [github.com/machalliance/wg-agent-adoption-operations](https://github.com/machalliance/wg-agent-adoption-operations).*
