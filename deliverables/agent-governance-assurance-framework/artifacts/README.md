# The forms

*A working document of the MACH Alliance Agent Adoption & Operations Working Group. September 2026 Draft, for discussion.*

These are the fill-in documents for the [Agent Governance and Assurance Framework](../README.md). Each stage has a form, and the reasoning behind it sits in a separate notes file so you can fill one in without reading an essay first.

Each form is either a **standard**, which describes your whole company and is written once, or a **record**, which describes one agent. [The five stages](five-stages.md) explains why they are kept apart, and the reasoning behind each stage.

## Start here

Pick one agent you already run, or are about to. Then work down this list. The first pass does not need to be perfect.

| Order | Stage | Fill in | Kind |
|---|---|---|---|
| 1 | 1. Agent design | [Agent Design Document](01-agent-design/agent-design-document.md) | Record |
| 2 | 2. Policy | [Risk Classifications](02-policy/risk-classifications.md) — just the one classification your agent belongs to | Standard |
| 3 | 1. Agent design | Section 6 of the design document, now that you have a classification to argue for | Record |
| 4 | 3. Platform controls | [Platform Control Levels](03-platform-controls/platform-control-levels.md) — score the platform you run on | Standard |
| 5 | 4. Live operations | [Monitoring Levels](04-live-operations/monitoring-levels.md) — score the same platform | Standard |
| 6 | 4. Live operations | [Monitoring and Incident Record](04-live-operations/monitoring-and-incident-record.md) | Record |
| 7 | 3. Platform controls | [Platform and Sign-off Record](03-platform-controls/platform-and-sign-off-record.md), then get it signed. **This row is the gate** | Record |
| 8 | 5. Audit and assurance | [Audit Log Rules](05-audit-and-assurance/audit-log-rules.md) — what agents add to the records policy you already have, settled once. **Needs somebody outside your team** | Standard |
| 9 | 5. Audit and assurance | [Audit and Assurance Record](05-audit-and-assurance/audit-and-assurance-record.md) | Record |

**Row 7 is the gate.** Nothing reaches production until it is signed. Rows 1 to 6 are what the person signing it reads. Rows 8 and 9 are what keeps the agent defensible once it is live.

The sign-off comes after the monitoring rows even though it belongs to stage 3, because section C of that record asks how the monitoring level applied compares with the one the classification requires. Nobody can answer that before the monitoring record exists.

**Row 8 is the only one that needs a person who is not on your team.** Their calendar sets when it lands, not your effort, so ask for that meeting on the first day and work the rest of the list while you wait for it.

The per-agent records are also a single workbook, [agent-governance-forms.xlsx](agent-governance-forms.xlsx), for teams who would rather fill them in there. The standards are not in it, because a policy you write once for the whole company is not a spreadsheet.

Stage 1 comes before stage 2 in practice even though the classification is stage 2's, because you cannot classify an agent until somebody has written down what it does. Expect to go back to section 6 once.

## Everything here

| Stage | Standard | Record | Notes |
|---|---|---|---|
| 1. Agent design | — | [Agent Design Document](01-agent-design/agent-design-document.md) | [Notes](01-agent-design/agent-design-document-notes.md) |
| 2. Policy | [Risk Classifications](02-policy/risk-classifications.md) | Section 6 of the design document | [Notes](02-policy/risk-classifications-notes.md) |
| 3. Platform controls | [Platform Control Levels](03-platform-controls/platform-control-levels.md) | [Platform and Sign-off Record](03-platform-controls/platform-and-sign-off-record.md) | [Standard](03-platform-controls/platform-control-levels-notes.md) · [Record](03-platform-controls/platform-and-sign-off-record-notes.md) |
| 4. Live operations | [Monitoring Levels](04-live-operations/monitoring-levels.md) | [Monitoring and Incident Record](04-live-operations/monitoring-and-incident-record.md) | [Standard](04-live-operations/monitoring-levels-notes.md) · [Record](04-live-operations/monitoring-and-incident-record-notes.md) |
| 5. Audit and assurance | [Audit Log Rules](05-audit-and-assurance/audit-log-rules.md) | [Audit and Assurance Record](05-audit-and-assurance/audit-and-assurance-record.md) | [Standard](05-audit-and-assurance/audit-log-rules-notes.md) · [Record](05-audit-and-assurance/audit-and-assurance-record-notes.md) |
