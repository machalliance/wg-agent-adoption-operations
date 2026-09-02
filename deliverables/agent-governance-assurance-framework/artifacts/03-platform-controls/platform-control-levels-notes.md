# Notes on the Platform Control Levels

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Platform Control Levels](platform-control-levels.md): where the ladder comes from, what it deliberately leaves out, and what we would like your feedback on. You do not need to read it to use the standard.

---

## Notes on the hard parts

### This ladder is not original, and says so

Three published models already describe how tightly an agent's access is controlled. We compress them into three plain-language steps for people who have not read any of them, and point at one of them for anyone who needs more.

That is the whole contribution of this document. We are not proposing a fourth model, and if you already run a program against any of the work below, use that instead.

### Why we point at CSA and not the others

The standard names one place to go deeper. Sending a reader to three unfamiliar organizations is homework, not help.

[CSA's Agentic AI Identity and Access Management](https://cloudsecurityalliance.org/artifacts/agentic-ai-identity-and-access-management-a-new-approach), published August 2025, is free to download, is written for agents specifically, and comes from a body this framework already cites at stage 2. It covers agent identity, delegation chains, attribute-based authorization, revocation across systems, and credentials that live only for one task.

Two others are worth knowing about. They are in the notes and not the standard, for a reason:

- **[CISA's Zero Trust Maturity Model](https://www.cisa.gov/zero-trust-maturity-model)** scores five pillars independently across four stages. It is free and well established, and it is about zero trust in general rather than agents. We took the shape from it: score each dimension separately instead of collapsing everything into one number.
- **Gartner's workload IAM research** treats an agent as a workload identity that needs an owner, a purpose, an approved access scope, a lifecycle, a credential strategy, an access review, a logging path and a kill switch. That list is close to what our two stage-3 documents already ask for, which we take as corroboration. It is paywalled, which is why it is not the standard's recommended next step.

A [six-stage maturity model for agent identities](https://www.csoonline.com/article/4194548/agentic-ai-identity-a-6-stage-maturity-model-for-non-human-identities.html) published in July 2026 runs from Unrecognized through Visible, Unique, Controlled and Bounded and Monitored to Self-Regulating, and argues that production deployment below its third stage is not defensible to a board or a regulator. Our Level 1 sits at roughly its stage 2 to 3. We record it as corroboration, because it is a single author writing in a trade publication, and our [citation rule](../../references.md) reserves authority for standards bodies and named consortia.

### Why the level describes a platform

An earlier draft made this a single company-wide score. That was wrong, for a reason worth recording.

Companies run agents in several places, and those places are rarely controlled equally well. A team with a well-governed cloud platform and an ungoverned laptop-based coding assistant has no honest single number. Gartner makes the same distinction: agents running under managed cloud identity inherit controls that a local or browser-based agent cannot.

Scoring each agent instead would be worse in the other direction. Twenty agents on one platform would produce twenty identical assessments.

So the platform carries the score, and the agent records what was actually applied to it within that ceiling. That gives two numbers, which is one more than we wanted and one fewer than the truth requires.

### Why "no" beats a claimed level

The self-assessment in part 2 is a list of yes/no questions, because a description invites generous reading.

The stage 3 sign-off rests on the level being true. Somebody accepts residual risk on the understanding that a control exists. A level claimed and not held turns that acceptance into something the person signing did not agree to.

### The gap this research found in our own forms

Gartner's list of what a workload identity needs includes an **access review**: when an agent's permissions get looked at again, and by whom. We had the other seven items across the design document and the platform record. We did not have that one, and it is now a field in the [Platform and Sign-off Record](platform-and-sign-off-record.md).

It matters because an agent's permissions are granted once and then survive every change to what the agent does. Reviewing them is the only thing that catches an agent that has quietly grown.

---

## What this standard is not

**It is not a security architecture.** It says how tightly access is controlled. It does not tell you how to build the controls, and CSA's work does.

**It is not a certification.** [AIUC-1](https://aiuc-1.com/) and [ISO/IEC 42001](https://www.iso.org/standard/81230.html) are things you can certify against. This is a self-assessment that nobody audits, which makes it useful for planning and worthless as evidence.

**It is not a schedule.** Nothing here says you should reach Level 3, or by when. Stage 2 decides which level a given classification of agent requires, and that is a decision about risk, not about maturity for its own sake.

## What we want feedback on

1. **Are three levels enough to be useful?** CSA's work is richer and CISA's has four stages across five pillars. Three may be too coarse to tell you anything you did not already know.
2. **Is the platform-versus-agent split workable?** It gives two numbers per agent. That may be one too many for a form somebody fills in under time pressure.
3. **Is part 5 honest enough?** We tell you when to abandon this document. We would like to know whether anyone reaches that point and actually does.
4. **Is CSA the right single destination?** It was chosen because it is free, agent-specific and already cited here. Tell us if your teams would go somewhere else first.
5. **Does the access review field belong here or in stage 4?** It is currently in the platform record. It is arguably a monitoring activity.

[Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues), particularly if your platform does not fit any of the three levels.
