# Output Format Standard

Every file produced by the Research Squad must begin with a standard header block.
This makes files traceable, resumable across sessions, and machine-readable.

---

## Standard Header Block

```
---
produced_by: [canonical agent name]
consumed_by: [canonical agent name or role]
project: [project name]
date: [YYYY-MM-DD]
status: draft | approved
---
```

**Rules:**
- `status: draft` on delivery from any specialist or director
- `status: approved` only after explicit PM approval at a gate
- The orchestrator updates `status` to `approved` after gate confirmation
- Never advance a file to the next agent without `status: approved` in the input

---

## Canonical Agent Names

Use these exact strings in `produced_by` and `consumed_by`:

| Agent | Canonical name |
|---|---|
| Orchestrator | `research-squad-orchestrator` |
| Research Director | `research-director` |
| Strategy Director | `strategy-director` |
| Interview Agent | `interview-agent` |
| Survey Agent | `survey-agent` |
| Desk Research Agent | `desk-research-agent` |
| Competitive Intelligence Agent | `competitive-intelligence-agent` |
| Pricing Agent | `pricing-agent` |
| Usability Agent | `usability-agent` |
| Internal Data Agent | `internal-data-agent` |

---

## File Naming Convention

```
/outputs/[project-name]/
  01-learning-agenda.md                    ← Strategy Director → Research Director
  02-research-plan.md                      ← Research Director → Specialists
  03-agent-briefs/
    interview-brief.md                     ← Research Director → Interview Agent
    survey-brief.md                        ← Research Director → Survey Agent
    [agent]-brief.md                       ← Research Director → [Agent]
  04-research-outputs/
    interview-findings.md                  ← Interview Agent → Research Director
    survey-findings.md                     ← Survey Agent → Research Director
    [agent]-findings.md                    ← [Agent] → Research Director
  05-research-summary.md                   ← Research Director → Strategy Director
  06-value-analysis.md                     ← Strategy Director → Engineering/Design
```

The numeric prefix enforces sequence. Files at the same prefix level can be
produced in parallel.

---

## Input Folder

Drop raw inputs here before activating the orchestrator:

```
/inputs/
  [project-name]-brief.md
  [project-name]-strategy.md
```

The orchestrator reads from `/inputs/` and writes all outputs to `/outputs/[project-name]/`.
