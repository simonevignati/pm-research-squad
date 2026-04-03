# pm-research-squad

A 10-agent research system for product managers. Runs a full research pipeline
from a problem statement to a validated Value Analysis Document — with four
mandatory PM approval gates at every critical decision point.

Built on the [gitagent](https://github.com/open-gitagent/gitagent/) standard.
Distributable as a Claude Code plugin.

---

## Install

```bash
claude plugin marketplace add https://github.com/svignati/pm-research-squad
```

---

## Usage

### Full pipeline

```
/research-squad
Run the Research Squad on project [name]. Input is in /inputs/[filename].md.
```

The orchestrator takes over from there — producing a Learning Agenda, routing to
specialists, enforcing four approval gates, and delivering a Value Analysis Document.

### Individual specialists

Each agent can run standalone without the full pipeline:

```
/research-squad:interview
[paste raw interview notes or provide file path]
```

```
/research-squad:competitive
Brief: Analyze [Competitor X]'s pricing and positioning for [product area].
Decision: selecting our pricing model for Q2.
Scope: pricing page, onboarding flow, positioning copy.
```

```
/research-squad:value-analysis
[paste strategy doc or problem statement]
```

```
/research-squad:pricing
Product: [name]
Cost structure: [paste data or provide file path]
Question: What pricing model fits this product?
```

---

## The Pipeline

```
INPUT (strategy doc, brief, or problem statement)
     ↓
┌─ STEP 1: Value Analysis Director
│  Frames problem, maps assumptions, outputs Learning Agenda
│  ◼ Gate 1 — PM approves scope and gap priorities
│
├─ STEP 2: Research Director (planning)
│  Converts gaps to methods, generates agent briefs
│  ◼ Gate 2 — PM approves each brief before dispatch
│
├─ STEP 3: Specialist agents (parallel)
│  Interview · Survey · Desk Research · Competitive · Pricing · Usability · Internal Data
│  Lightweight PM check after each finding
│  ◼ Gate 3 — PM reviews evidence base before synthesis
│
├─ STEP 4: Research Director (synthesis)
│  Challenges and synthesizes findings, translates to decisions
│  ◼ Gate 4 — PM approves insights and accepts residual risk
│
└─ STEP 5: Value Analysis Director
   Translates approved summary into Value Analysis Document
   (read-only — decisions made at Gate 4)
```

Output files per project:
```
/outputs/[project-name]/
  01-learning-agenda.md
  02-research-plan.md
  03-agent-briefs/[agent]-brief.md
  04-research-outputs/[agent]-findings.md
  05-research-summary.md
  06-value-analysis.md
```

---

## Agent Handoff Protocol

Every output file produced by an agent begins with a standard header block:

```
---
produced_by: [agent-name]
consumed_by: [next agent or role]
project: [project name]
date: [date]
status: draft
---
```

This header is not cosmetic. It is the handoff contract between agents:

- **`produced_by`** — identifies which agent generated the file and is accountable for its quality
- **`consumed_by`** — tells the next agent in the pipeline exactly what to do with this file
- **`status`** — agents will not consume a file until the PM has changed it from `draft` to `approved`

The PM approval gates are enforced through `status`. No agent reads a file marked `draft`. This means the pipeline cannot skip a gate accidentally — the PM is a required participant at every transition, not an optional reviewer at the end.

When a session is interrupted or resumed, any agent can reconstruct its position by reading the last approved artifact in the output folder.

---

## The 10 Agents

| Character | Skill | Role |
|---|---|---|
| **Leonardo** | `/research-squad` | Full orchestrated pipeline |
| **Machiavelli** | `/research-squad:value-analysis` | Problem framing → Learning Agenda; Research Summary → Value Analysis Document |
| **Galileo** | `/research-squad:research-director` | Research planning + synthesis |
| **Oprah** | `/research-squad:interview` | Qualitative depth, mental models, JTBD, OST |
| **Florence Nightingale** | `/research-squad:survey` | Prevalence, segmentation, WTP at scale |
| **Gutenberg** | `/research-squad:desk-research` | Market sizing, regulation, analogous markets |
| **Sun Tzu** | `/research-squad:competitive` | Competitor teardowns, feature gaps, white space |
| **Kasparov** | `/research-squad:pricing` | Pricing models, cost structure, WTP, competitor benchmarks |
| **Vitruvius** | `/research-squad:usability` | Task completion, friction mapping, UI comprehension |
| **Archimedes** | `/research-squad:internal-data` | Usage patterns, funnel, feature adoption, churn signals |

---

## Design Principles

- **Four gates are non-negotiable.** The PM decides at each. Nothing advances on the squad's judgment.
- **Parallel is default.** Specialists run simultaneously unless a brief explicitly depends on another finding.
- **Files are memory.** If a session stalls, read the last approved artifact and resume from there.
- **Quality surfaces early.** Thin or off-brief outputs are flagged before synthesis — never averaged away.
- **Cheap learning beats expensive learning.** Before recommending primary research, we ask if internal data, analogous markets, or desk research can close the gap first.

---

## Examples

See `knowledge/examples/` for anonymized real examples:
- `example-interview-snapshot.md` — what a completed Interview Agent snapshot looks like
- `example-research-plan.md` — what a completed Research Director planning output looks like

See `templates/` for blank output templates for each pipeline stage.

---

## gitagent Compatibility

This repo follows the [gitagent](https://github.com/open-gitagent/gitagent/) standard.
Export to other frameworks:

```bash
gitagent export --format system-prompt   # single system prompt
gitagent export --format openai-agents   # OpenAI Agents SDK
gitagent export --format crewai          # CrewAI
```

---

## License

MIT
