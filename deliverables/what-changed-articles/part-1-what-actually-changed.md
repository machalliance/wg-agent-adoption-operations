# What changed (Part 1 of 3): What actually changed

*A three-part position paper from the MACH Alliance Agent Adoption & Operations Working Group*

> **Series — *What changed: A new mental model for the age of AI agents*** \
> Part 1 · What actually changed | Part 2 · The mental models we carry | Part 3 · Moving through the shift

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

The first is that AI output is generative and probabilistic, not deterministic. Traditional software executes defined logic and produces predictable outputs given known inputs. AI systems generate from patterns and probability. The same input can produce different results across runs, and the system can produce things it was never explicitly programmed for. That is *not* a flaw, but rather it is the point. 

The second is that modern agents take actions, not just produce suggestions. Earlier AI systems offered outputs that humans then acted upon (e.g., a recommendation, a draft, a classification). Agentic systems act. They initiate requests, modify data, trigger processes, and interact with other systems on behalf of the organizations that deploy them. Actions have consequences that suggestions do not, specifically, because they remove the human accountability layer.

Together, these two features are what make this moment different from previous enterprise technology shifts. They are also what make existing mental models unreliable.

---

*Next in this series — Part 2: the three mental models most people use to make sense of AI agents, and why each one fails.*

---

## Sources

1. McKinsey & Company. "The State of AI: Agents, Innovation, and Transformation." November 2025. https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai
2. Stanford Institute for Human-Centered AI. "The 2025 AI Index Report." April 2025. https://hai.stanford.edu/ai-index/2025-ai-index-report

---

*This position paper is published by the MACH Alliance Agent Adoption & Operations Working Group, part of the MACH Alliance Agent Ecosystem initiative. Working group membership, charter, and deliverables are maintained at [github.com/machalliance/wg-agent-adoption-operations](https://github.com/machalliance/wg-agent-adoption-operations).*
