# pm-research-squad

Ten brilliant minds. One research pipeline. Zero guesswork.

This is a 10-agent research system for product managers — running a full sprint from
"should we build this?" to a validated Value Analysis Document ready for engineering
and design. With four mandatory PM approval gates, because *you* decide, not the agents.

Built on the [gitagent](https://github.com/open-gitagent/gitagent/) standard.
Distributable as a Claude Code plugin.

---

## Install

```bash
claude plugin marketplace add https://github.com/svignati/pm-research-squad
```

---

## Meet the Squad

These are not chatbots. They are opinionated specialists with centuries of combined expertise
(metaphorically speaking) and strong opinions about what counts as evidence.

| Character | Skill | What they do |
|---|---|---|
| **Leonardo** | `/research-squad` | Orchestrates the full pipeline. Routes files, enforces gates, keeps everyone honest. |
| **Machiavelli** | `/research-squad:value-analysis` | Maps the problem space. Asks whether you're solving the right problem before a single euro is spent on research. Then closes the loop after. |
| **Galileo** | `/research-squad:research-director` | Turns knowledge gaps into research plans. Challenges weak findings. Synthesizes across sources. |
| **Stanislavski** | `/research-squad:interview` | Gets inside your users' heads. Mental models, JTBD, unmet needs — all from depth interviews. Method matters to him. |
| **Pascal** | `/research-squad:survey` | Quantifies uncertainty before you bet. Behavioral segmentation, WTP, prevalence at scale. Always writes the analysis plan *before* designing the survey. |
| **Gutenberg** | `/research-squad:desk-research` | Synthesizes what's already public. Market sizing, regulation, analogous markets. Fastest agent in the squad. |
| **Sun Tzu** | `/research-squad:competitive` | Thinks 10 moves ahead. Teardowns, feature gaps, positioning white space. Never satisfied with surface-level analysis. |
| **Kasparov** | `/research-squad:pricing` | Calculates every move. Finds the price the market will bear, the floor your costs set, and the gap between them. Sacrifice a margin point to win the position. |
| **Vitruvius** | `/research-squad:usability` | Watches people try to use your product and notes exactly where they fail. No opinions. Only observations and severity ratings. |
| **Archimedes** | `/research-squad:internal-data` | Finds the lever in your existing data. Usage patterns, funnels, feature adoption, churn signals — all from what you already have. |

---

## Usage

### Full pipeline

```
/research-squad
Run the Research Squad on project [name]. Input is in /inputs/[filename].md.
```

Leonardo takes over from there — producing a Learning Agenda, routing to specialists,
enforcing four approval gates, and delivering a Value Analysis Document.

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
┌─ STEP 1: Machiavelli — Value Analysis Director
│  Frames problem, maps assumptions, outputs Learning Agenda
│  ◼ Gate 1 — PM approves scope and gap priorities
│
├─ STEP 2: Galileo — Research Director (planning)
│  Converts gaps to methods, generates agent briefs
│  ◼ Gate 2 — PM approves each brief before dispatch
│
├─ STEP 3: Specialist agents (parallel)
│  Stanislavski · Pascal · Gutenberg · Sun Tzu · Kasparov · Vitruvius · Archimedes
│  Lightweight PM check after each finding
│  ◼ Gate 3 — PM reviews evidence base before synthesis
│
├─ STEP 4: Galileo — Research Director (synthesis)
│  Challenges and synthesizes findings, translates to decisions
│  ◼ Gate 4 — PM approves insights and accepts residual risk
│
└─ STEP 5: Machiavelli — Value Analysis Director
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

## Design Principles

- **Four gates are non-negotiable.** The PM decides at each. Nothing advances on the squad's judgment alone.
- **Parallel is default.** Specialists run simultaneously unless a brief explicitly depends on another finding.
- **Files are memory.** If a session stalls, read the last approved artifact and resume from there.
- **Quality surfaces early.** Thin or off-brief outputs are flagged before synthesis — never averaged away.
- **Cheap learning beats expensive learning.** Before recommending primary research, we ask if internal data, analogous markets, or desk research can close the gap first.

---

## Examples

See `knowledge/examples/` for anonymized real examples:
- `example-interview-snapshot.md` — what a completed Stanislavski snapshot looks like
- `example-research-plan.md` — what a completed Galileo planning output looks like

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
