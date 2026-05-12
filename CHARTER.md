# Agent Adoption & Operations Working Group Charter

## Purpose

Many organizations can pilot agents that retrieve information, generate content, or automate parts of a workflow. Success in moving to the next level, running dozens or hundreds of agents, depends on establishing the organizational readiness to be effective and responsible.

This working group focuses on what organizations need to get started and advance from experimentation to managing more complex deployments. Lean, iterative engineering delivery practices that are proven[^dora] to predict enterprise technology success apply to agentic operations too. This includes the climate for learning, fast flow, operating models, reliability practices, and cross-functional coordination required to introduce agents safely into real business workflows.

A separate working group is focused on [enterprise agentic architecture](https://github.com/machalliance/wg-enterprise-agent-architecture). This group is focused on how to adopt, operate, supervise, and scale agents across the enterprise.

The goal is guidance that helps organizations find their position on the continuum of agentic adoption and then know what can be done to move their organization forward.

### 1. Get Started
- Assess organization readiness for lean, iterative delivery
- Provide a vocabulary to identify common types of AI solutions and deployments
- Introduce what changes are required of enterprises due to the nature of probabalistic (AI) solutions, which are different than the consistent, deterministic systems enterprises have scoped, deployed, and run for decades

### 2. Deliver and Deploy
- Adopt agents in a controlled and business-aligned way
- Establish governance, oversight, and accountability as agents take on greater responsibility

### 3. Operations
- Operate agent-driven systems reliably across enterprise platforms and workflows
- Define the roles, processes, and guardrails needed for effective human supervision
- Scale adoption across teams without creating fragmented or unmanaged systems
- Build the operational maturity to sustain value and manage risk over time

## Example Questions

Examples below illustrate the types of challenges this working group seeks to examine and address.

- What adoption patterns help organizations introduce agents into real workflows while maintaining trust, accountability, and clear human oversight?
- In practice, who owns and operates an agent once it is deployed in production, and how is accountability maintained?
- How should enterprises define and enforce permission models for agents interacting with enterprise platforms and APIs?
- What guardrails have proven effective for controlling agent autonomy while still enabling meaningful automation?
- What telemetry or execution data should be captured to understand how an agent made a decision or completed a task?
- How should teams detect, investigate, and resolve unexpected agent behavior across complex enterprise environments?

## Proposed Artifacts

The following is a proposed set of artifacts the working group may develop to support the adoption and operation of enterprise multi-agent systems.

### 1. Enterprise Agent Adoption Framework

A framework describing how organizations adopt agents over time from experimentation to controlled production use and eventually scaled operational capability. It defines adoption stages, readiness conditions, and the organizational capabilities required at each stage to prevent fragmented or unmanaged deployments.

### 2. Enterprise Agent Operating Model

A reference model defining roles, ownership, and responsibilities for agent-driven systems across business teams, product organizations, and platform and operations teams. It establishes how agents are introduced, supervised, and managed as long-lived operational systems, with clear accountability for development, monitoring, governance, and lifecycle management.

### 3. Agent Governance Framework

Guidance for defining guardrails around agent autonomy, including approval thresholds, permission boundaries, escalation mechanisms, and oversight policies. It helps organizations determine when agents can act independently and how risk is managed as agent capabilities expand.


### 4. Agent Production Readiness Checklist

A checklist used to evaluate whether a specific agent is ready for production deployment. It assesses safeguards such as authority boundaries, monitoring, fallback mechanisms, testing, and operational ownership to ensure agents meet minimum reliability and safety standards before launch.


### 5. Agent Operations Playbook

A guide for operating agent systems in production environments. It outlines operational ownership, monitoring practices, lifecycle management, incident response, and optimization workflows required to maintain reliable agent-driven systems.

*Example:* When an agent produces an unexpected outcome, the on-call team follows the playbook to triage the alert, review decision traces, apply a remediation, and complete a post-incident review.

### 6. Agent Observability Model

A reference model describing how agent behavior should be monitored and understood. It defines patterns for capturing decision traces, tool usage, execution paths, and system interactions to support transparency, debugging, and operational insight.

*Example:* For a given agent run, an operator can inspect the decision path, tool invocations, inputs and outputs, and the prompt context that led to a specific action.

## Who This Working Group Serves

This working group supports organizations introducing or scaling AI agents in enterprise environments.

Primary audiences include:

**Business and Digital Leaders**
Leaders responsible for organizational readiness, operational change, risk management, and AI adoption.

**AI Platform and Operations Teams**
Technical teams responsible for deploying, monitoring, and operating AI systems in production.

**Enterprise Architecture and Technology Strategy**
Architects designing secure, observable, and reliable systems as agent-driven automation expands.


[^dora]: Org Capabilities (Fast Flow, Fast Feedback, Climate for Learning) predict Engineering Performance (Software Delivery, Reliability) predicts Org Outcomes (Org Performance, Well-being) https://dora.dev/research/ and application to AI https://dora.dev/ai/
