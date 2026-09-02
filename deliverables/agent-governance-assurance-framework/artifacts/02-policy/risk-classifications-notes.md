# Notes on the Risk Classifications

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

This document explains the [Risk Classifications and the Classification Test](risk-classifications.md): why the criteria are what they are, why the test works the way it does, and what we would like your feedback on. You do not need to read it to use the standard.

---

## Notes on the hard parts

### Why the starter classifications are filled in

An empty template gets adopted and never completed. A filled-in one gets argued with, and the argument is what we want: a team that renames "sensitive" or moves a control between classifications has understood the criteria well enough to disagree with them.

The four we ship are consequence classifications. They are deliberately coarse. Most companies will end up with four to six classifications, and the ones that end up with twelve have usually built a matrix, not a policy.

### Why classifications describe types, not agents

Every other artifact in this framework is one document per agent. This one is not, and the reason is that controls are expensive to design and cheap to reuse. If each agent carried its own bespoke control set, nothing would ever get enforced in a platform, because a platform enforces rules that apply to a class of things.

So the classification is the unit a platform can act on. Stage 3 Level 2 exists precisely because a classification can set a ceiling that an engineer cannot grant past, and that only works if the classification is a durable type and not a per-agent judgment.

### Why the criteria are consequence, not autonomy

Six of the eight questions measure what happens when the agent is wrong. Question 7 asks how much of that happens with nobody watching, and question 8 asks who is on the receiving end.

That is deliberate, and it is where we differ from the autonomy scales in circulation, including the four levels in the [Cloud Security Alliance's agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/) for the NIST AI RMF. Autonomy is a property of the design. Consequence is a property of the systems the agent touches. A fully autonomous agent that files internal tickets needs less governance than a closely supervised one that issues refunds, and an autonomy scale ranks those the wrong way round.

Record the autonomy level too, in the [Platform and Sign-off Record](../03-platform-controls/platform-and-sign-off-record.md), beside the platform control level. It is useful for deciding how closely to watch an agent, which is a different question from how much control it needs.

### Why the highest floor wins

The alternative is a weighted score, and a weighted score is how a critical property gets averaged away by seven reassuring ones.

The rule is blunt on purpose. It also makes the test cheap to run: nobody has to agree on weights, and a reviewer only has to check the single row that set the floor.

The cost of the rule is that it over-classifies. An agent with one critical answer and seven routine ones gets critical controls it mostly does not need. We think that is the right error to make, and we would like to hear from anyone who has run this and found it unworkable.

### Why the compensating-control escape hatch is narrow

Without a hatch, the rule is unusable: a control that genuinely removes an exposure should be able to move an agent down.

With a wide hatch, the rule is decorative: every team names its system prompt and drops a classification. The three limits exist to stop that. Limit 2 is the one that bites, because "we told the model not to" is the most common control in production today and it is not a control.

### Why the reclassification triggers are a table

Because the most common failure of a governance program is not a wrong classification. It is a correct classification that nobody revisited after the model changed.

The triggers name which stage detects each one, so the loop back from stage 4 and stage 5 has somewhere specific to land.

---

## Where this comes from

| Part | Who else asks for it |
|---|---|
| Classifications as company-wide types | [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) GV.1.6 requires an inventory of AI systems resourced according to risk priority, which presupposes a scheme to prioritize against. [Gartner AI TRiSM](https://www.gartner.com/en/articles/ai-governance-trism) treats governance, runtime enforcement and information governance as one program instead of per-project work. |
| The criteria | The [Cloud Security Alliance's agentic profile](https://labs.cloudsecurityalliance.org/agentic/agentic-nist-ai-rmf-profile-v1/) requires that the authority an agent holds, the tools it reaches, and the timing of authority review all be tracked per agent. [AIUC-1](https://aiuc-1.com/) certifies against requirements spanning data and privacy, security, safety, reliability, accountability and society, which is a longer version of the same list. |
| Consequence over autonomy | Google's [approach for secure AI agents](https://research.google/pubs/an-introduction-to-googles-approach-for-secure-ai-agents/) ties the strength of a control to whether an action is critical or irreversible, not to how autonomous the agent is. AWS [AGENTREL02-BP05](https://docs.aws.amazon.com/wellarchitected/latest/agentic-ai-lens/agentrel02-bp05.html) matches the level of human review to the risk and reversibility of each action. |
| A test with recorded reasons | OWASP's governance maturity model, in [State of Agentic AI Security and Governance v2.01](https://genai.owasp.org/resource/state-of-agentic-ai-security-and-governance/), puts published policy and named accountability at Level 2 and machine-readable enforcement at Level 3. A classification without a test cannot reach either. |
| Classification setting a platform ceiling | [Amazon Bedrock AgentCore Gateway](https://aws.amazon.com/blogs/machine-learning/govern-ai-agent-tool-access-with-amazon-bedrock-agentcore-gateway/) governs tool access on a Connect, Control, Catalog, Harden progression, and AgentCore Policy expresses the ceiling in [Cedar](https://aws.amazon.com/blogs/machine-learning/control-agent-behaviors-and-cost-beyond-a-single-action-new-capabilities-in-amazon-bedrock-agentcore/). [Microsoft Entra Agent ID](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview) applies directory governance to agent identities the same way. |
| Reclassification triggers | The CSA profile's runtime records and autonomy checks are what feed stage 4 back into this stage. AIUC-1 refreshes quarterly, not annually, on the same reasoning. |

## What this standard is not

**It is not a risk register.** A risk register lists things that might go wrong and who owns them. This lists kinds of agent and the controls that follow. If you keep a register, an agent's classification is an input to it.

**It is not a maturity model.** The platform control levels and monitoring levels in stage 3 and stage 4 are maturity: they describe how good your enforcement is. Classifications describe how much enforcement an agent needs. A company at platform control Level 1 can still classify an agent as critical, and the honest result is an agent it should not yet be running.

**It is not a substitute for a legal assessment.** Question 3 asks which regulations reach the process. It does not tell you the answer, and this document is not the place to find it.

## What we want feedback on

1. **Are four classifications the right number to ship?** Too few forces everything into "sensitive". Too many is a matrix nobody applies.
2. **Are the starter criteria in the right classifications?** Specifically whether "reaches personal data" belongs at sensitive, which is where most privacy functions would put it, or lower, which is where most engineering teams behave as though it sits.
3. **Are the floor anchors set at the right places?** They are what stops two teams classifying the same agent differently, and they are also where we have guessed most. Question 4 is left for you to put numbers on.
4. **Does the highest-floor rule over-classify in practice?** We think over-classifying is the right error. Tell us if it made the framework unusable for you.
5. **Is limit 2 on the escape hatch too strict?** It rules out prompt-level controls entirely. There may be cases where a prompt-level control plus strong monitoring is genuinely equivalent.
6. **Should the platform control level and monitoring level be requirements of a classification at all?** Putting them here means a classification can demand maturity a company does not have. The alternative is to record the gap and let the sign-off carry it.

If you have run the test on a real agent and it produced the wrong answer, that is the most useful thing you can send us. [Open an issue](https://github.com/machalliance/wg-agent-adoption-operations/issues).
