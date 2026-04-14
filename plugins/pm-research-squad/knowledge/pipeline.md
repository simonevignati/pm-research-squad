# Research Squad Pipeline

## Overview

The Research Squad runs a 5-step pipeline from a raw input (strategy doc, problem statement, or brief) to a validated Value Analysis Document ready for engineering and design.

Four PM-approval gates are mandatory. The pipeline never auto-advances.

---

## The 5 Steps

| Step | Agent | Output file | Gate |
|---|---|---|---|
| 1 | Strategy Director (Mode 1) | `01-learning-agenda.md` | ◼ Gate 1 |
| 2 | Research Director (planning) | `02-research-plan.md` + `03-agent-briefs/` | ◼ Gate 2 |
| 3 | Specialist agents (parallel) | `04-research-outputs/[agent]-findings.md` | Lightweight check per agent |
| 3.5 | — | — | ◼ Gate 3 |
| 4 | Research Director (synthesis) | `05-research-summary.md` | ◼ Gate 4 |
| 5 | Strategy Director (Mode 2) | `06-value-analysis.md` | Read only |

---

## The 4 Gates

### Gate 1 — Learning Agenda
**You decide:** Scope and priority of knowledge gaps.
**The orchestrator shows you:** Full Learning Agenda + its own critique (underspecified gaps, missing hypotheses, cheaper alternatives).
**You approve, edit, or descope gaps before research begins.**

### Gate 2 — Research Plan and Briefs
**You decide:** Research methods and brief quality.
**The orchestrator shows you:** Dispatch summary table + all agent briefs with one-line summaries.
**The orchestrator flags automatically:** Briefs without success criteria, method mismatches, sequencing bottlenecks.
**You approve each brief individually. Unapproved briefs are not dispatched.**

### Gate 3 — Pre-Synthesis Check
**You decide:** Whether the evidence base is strong enough to synthesize.
**The orchestrator shows you:** Findings dashboard (agent / gap / confidence / flags), open gaps, contradictions.
**You can commission corrective research before synthesis runs.**

### Gate 4 — Research Summary
**You decide:** Insight quality and which open gaps to accept as residual risk.
**The orchestrator shows you:** Full Research Summary + its critique (overstated confidence, weak evidence, recommendations not grounded in findings).
**After approval, the Value Analysis Document is produced. No more decisions.**

---

## File Output Structure

```
/outputs/[project-name]/
  01-learning-agenda.md
  02-research-plan.md
  03-agent-briefs/
    [agent]-brief.md
  04-research-outputs/
    [agent]-findings.md
  05-research-summary.md
  06-value-analysis.md
```

---

## Specialist Agent Roster

| Skill | Best for |
|---|---|
| `/research-squad:interview` | Mental models, decision logic, unmet needs, JTBD |
| `/research-squad:survey` | Prevalence, segmentation, WTP at scale |
| `/research-squad:desk-research` | Market sizing, regulation, analogous markets |
| `/research-squad:competitive` | Competitor teardowns, feature gaps, white space |
| `/research-squad:pricing` | Pricing models, cost structure, WTP, competitor pricing |
| `/research-squad:usability` | Task completion, friction mapping, UI comprehension |
| `/research-squad:internal-data` | Usage patterns, funnel, feature adoption, churn signals |
| `/research-squad:research-director` | Research planning, synthesis (activated by orchestrator) |
| `/research-squad:value-analysis` | Learning Agenda, Value Analysis Document (activated by orchestrator) |

---

## Using Specialists Standalone

Specialists can run without the full pipeline. Examples:

```
/research-squad:interview
[paste raw interview notes here]
```

```
/research-squad:competitive
Brief: Analyze [Competitor X]'s payment link pricing and positioning.
Decision this informs: our own pricing model selection for Q2.
Surfaces to analyze: payment links, invoicing, pricing page.
```

```
/research-squad:pricing
Product: [product name]
Cost structure: [paste cost data or file path]
Question: What pricing model maximizes activation without sacrificing margin?
```

---

## Design Principles

- **Gates are real decisions, not rubber stamps.** The orchestrator surfaces problems proactively.
- **Parallel is default.** Specialists run simultaneously unless a brief explicitly depends on another finding.
- **Files are memory.** If a session stalls, read the last approved artifact and resume.
- **Quality surfaces early.** Thin or off-brief outputs are flagged before synthesis — never averaged away.
- **Simplicity over comprehensiveness.** The goal is to close the gaps that block confident decisions, not to answer every possible question.
