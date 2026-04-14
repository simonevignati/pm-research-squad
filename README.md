# pm-research-squad

An 11-agent research system for product managers. Runs a full research pipeline from a problem statement to a validated Value Analysis Document — with four mandatory PM approval gates at every critical decision point.

Built on the [gitagent](https://github.com/open-gitagent/gitagent/) standard. Distributable as a Claude Code plugin.

---

## Install

```bash
claude plugin marketplace add https://github.com/simonevignati/pm-research-squad
```

---

## The Pipeline

You give the squad one thing: a problem statement or strategy doc. Leonardo (the orchestrator) takes over from there — activating agents in sequence, routing files between them, and enforcing four approval gates. He never does research himself. He moves the pipeline.

```
INPUT (strategy doc, brief, or problem statement)
     ↓
┌─ STEP 1: Machiavelli — Strategy Director
│  Stress-tests your problem framing in conversation (Phase 0)
│  Maps assumptions, outputs Learning Agenda
│  ◼ Gate 1 — PM approves scope and gap priorities
│
├─ STEP 2: Galileo — Research Director (planning)
│  Converts gaps to methods, generates agent briefs
│  ◼ Gate 2 — PM approves each brief before dispatch
│
├─ STEP 3: Specialist agents (parallel)
│  Oprah · Florence Nightingale · Gutenberg · Sun Tzu
│  Kasparov · Vitruvius · Archimedes · Nielsen
│  Lightweight PM check after each finding
│  ◼ Gate 3 — PM reviews evidence base before synthesis
│
├─ STEP 4: Galileo — Research Director (synthesis)
│  Challenges findings, surfaces contradictions, translates to decisions
│  ◼ Gate 4 — PM approves insights and accepts residual risk
│
└─ STEP 5: Machiavelli — Strategy Director (Mode 2)
   Translates approved summary into Value Analysis Document
   (read-only — decisions made at Gate 4)
```

---

## The Workflow, Step by Step

**Step 1 — Machiavelli (Strategy Director)**

Before producing any output, Machiavelli engages you in a mandatory conversational stress test (Phase 0). He asks four probes in sequence:
1. What decision does this research need to unlock?
2. What is the riskiest assumption, if wrong, that makes the whole program pointless?
3. What is the strongest argument against doing this at all?
4. What do you already know that doesn't need researching?

He challenges weak answers. He will not accept vague decisions or thin counter-arguments. Once the framing is sharp, he maps every assumption baked into the brief, classifies each by type and confidence, and produces a **Learning Agenda**: the ranked list of what you don't know, what decision each gap is blocking, and what the cost of being wrong is. Maximum 6 gaps — ruthlessly prioritized.

**◼ Gate 1 — you approve the Learning Agenda**
You can add gaps, remove them, reprioritize. Nothing moves until you say yes.

**Step 2 — Galileo (Research Director, planning mode)**

Takes the Learning Agenda and converts each gap into the right research method. He asks: survey or interview? Desk research or competitive analysis? He flags mismatches before dispatching — a qualitative gap sent to the survey agent is a waste of everyone's time. Outputs a **Research Plan** + one brief per specialist agent, each with explicit success criteria.

**◼ Gate 2 — you approve each brief**
You see exactly what each specialist will be asked to do before they run. You can modify or drop workstreams.

**Step 3 — Specialists run in parallel**

Each specialist gets their brief and produces findings. After each one completes, Leonardo gives you a 3-line summary: main finding, confidence level, red flags. Lightweight check — "solid enough, or flag it?" Flagged outputs still pass to Galileo, who will challenge them independently during synthesis.

**◼ Gate 3 — pre-synthesis check**
Leonardo shows you a findings dashboard: all workstreams, confidence levels, contradictions, open gaps. You decide if the evidence base is good enough to synthesize, or if you need more research first.

**Step 4 — Galileo (Research Director, synthesis mode)**

Challenges every finding before accepting it. Enforces confidence calibration — every insight gets a label (High / Medium / Low) with the evidence behind it. When two agents contradict each other, Galileo surfaces it explicitly and never averages contradictions into consensus. Organizes findings by theme, not by source. Tags each insight as confirmed / refuted / new signal / still open. A refuted hypothesis is treated as a finding, not a failure. Outputs a **Research Summary**.

**◼ Gate 4 — you approve the Research Summary**
Last decision point. You accept residual risk or commission more research.

**Step 5 — Machiavelli (Strategy Director, Mode 2)**

Translates the approved summary into a **Value Analysis Document** — the handoff to engineering and design. Every field evidence-based. Section 5 captures everything that remains a gap. Read-only artifact — no more decisions.

---

## The 11 Agents

| Character | Skill | Role | Strength |
|---|---|---|---|
| **Leonardo** | `/research-squad` | Orchestrator | Moves the pipeline, enforces gates, never does research |
| **Machiavelli** | `/research-squad:value-analysis` | Strategy Director | Problem framing stress test, assumption mapping, Learning Agenda → Value Analysis Doc |
| **Galileo** | `/research-squad:research-director` | Research Director | Method selection, contradiction surfacing, synthesis with confidence calibration |
| **Oprah** | `/research-squad:interview` | Qualitative depth | Reforge hierarchy of insight, OST framework, persona archetypes, Notion logging via MCP |
| **Florence Nightingale** | `/research-squad:survey` | Quantitative measurement | Analysis plan before survey design, Van Westendorp WTP, behavioral segmentation |
| **Gutenberg** | `/research-squad:desk-research` | Public data synthesis | Perplexity dispatch architecture with 5 prompt templates, source quality tiers |
| **Sun Tzu** | `/research-squad:competitive` | Competitive intelligence | Competitor teardowns, Reforge acquisition/retention lens, white space analysis |
| **Kasparov** | `/research-squad:pricing` | Pricing strategy | 10-model taxonomy, cost structure ingestion before any recommendation, fintech-specialized |
| **Vitruvius** | `/research-squad:usability` | Usability testing | Task completion, friction severity scale, scenario-based test design |
| **Archimedes** | `/research-squad:internal-data` | Internal data analysis | Behavioral segmentation, absence signals, instrumentation gap detection |
| **Nielsen** | `/research-squad:voc` | Voice of Customer | App Store / Google Play / Trustpilot sentiment, verbatim quotes, market breakdowns |

---

## Agent Capabilities and Integrations

### Oprah — Interview Agent
**What makes her exceptional:** Goes three levels deep on every topic — past surface answers to behavioral patterns, motivations, and mental models. Won't accept a rationalization as a finding.
**Output:** Per-interview snapshot + persona card + OST opportunity entries + cross-interview synthesis
**Integrations:**
- **Notion MCP** — logs every interview immediately after the session: interview record, persona registry update, opportunity table entries. Never batches. If MCP is unavailable, writes to file and flags for manual sync.

### Florence Nightingale — Survey Agent
**What makes her strong:** Writes the analysis plan before the survey runs. If she cannot state what a conclusive answer looks like, the questions aren't specific enough.
**Output:** Survey instrument + analysis plan + findings report
**Integrations:** None — outputs survey instruments for distribution via your own tooling (Typeform, Google Forms, etc.)
> **Known limitation:** Claude Code is synchronous. Florence designs the survey and analyzes results when you paste them back — but cannot distribute, wait for responses, or collect asynchronously. Plan for this in your timeline.

### Gutenberg — Desk Research Agent
**What makes him strong:** Two-mode architecture. Direct Research for known sources. Perplexity Dispatch for synthesis questions — with 5 battle-tested prompt templates (market sizing, regulatory landscape, competitive, technology benchmarking, analogous markets).
**Output:** Research brief + Perplexity prompts ready to paste + source quality log + gap assessment
**Integrations:**
- **WebFetch / WebSearch** — for Direct Research mode, navigates to primary sources directly
- **Perplexity (via prompt dispatch)** — produces ready-to-paste prompts; you run them and paste results back

### Sun Tzu — Competitive Intelligence Agent
**What makes him useful:** Analyzes jobs, not features. Maps competitor sequencing to reveal strategic bets. Identifies white space and classifies it: genuine opportunity, graveyard, or uncertain.
**Output:** Competitor landscape map + feature benchmarking matrix + UX teardown + white space analysis
**Integrations:**
- **WebFetch** — navigates competitor pricing pages, product pages, press releases directly

### Kasparov — Pricing Agent
**What makes him exceptional:** Cost structure before everything — will not produce a pricing recommendation without it. Evaluates all 10 pricing model archetypes before recommending one. Deep fintech specialization (interchange, MDR, scheme fees, PayFac margin stacks).
**Output:** Cost structure summary + pricing model evaluation with 5-dimension scoring + WTP analysis + competitor benchmark
**Integrations:** None — works with cost data you provide

### Nielsen — VoC Agent
**What makes him fast:** Mines existing public reviews without primary research. Best used at the start of a sprint for directional signal before interviews are recruited or surveys designed.
**Output:** Theme-ranked findings + verbatim quote bank + market breakdown (DE/IT/FR/ES/NL) + confidence assessment
**Integrations:**
- **Python via Bash** — loads and filters review data from `~/work/voc/raw/` (App Store, Google Play, Trustpilot JSON files collected weekly across 5 markets). Filters by keyword, market, source, and time window. Deduplicates by review ID.
- **Review data pipeline** — expects weekly collection runs at `~/work/voc/raw/` in the format `YYYY-MM-DD-{source}.json`

---

## Usage

### Full pipeline

```
/research-squad
Run the Research Squad on project [name]. Input is in /inputs/[filename].md.
```

### Individual specialists

Each agent runs standalone without the full pipeline:

```
/research-squad:value-analysis
[paste strategy doc or problem statement]
```

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
/research-squad:pricing
Product: [name]
Cost structure: [paste data or provide file path]
Question: What pricing model fits this product?
```

```
/research-squad:voc
Topic: [what you want to understand from public reviews]
Markets: [DE / IT / FR / ES / NL — or all]
Time window: [days back, or all time]
```

---

## File Structure

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

Every output file begins with a standard handoff header:

```
---
produced_by: [agent-name]
consumed_by: [next agent or role]
project: [project name]
date: [YYYY-MM-DD]
status: draft | approved
---
```

The `status` field enforces the gates. An agent will not consume a file marked `draft`. The pipeline cannot skip a gate accidentally — the PM is a required participant at every transition, not an optional reviewer at the end.

---

## Design Principles

- **Four gates are non-negotiable.** The PM decides at each. Nothing advances on the squad's judgment.
- **Phase 0 is mandatory.** Machiavelli stress-tests your problem framing before any research is designed. Garbage in, garbage out — caught early.
- **Parallel is default.** Specialists run simultaneously unless a brief explicitly depends on another finding.
- **Contradictions are surfaced, never averaged.** Galileo flags every conflict between agents as an explicit PM decision.
- **Files are memory.** If a session stalls, read the last approved artifact and resume from there.
- **Confidence is calibrated.** Every insight has a label and the evidence behind it. Weak evidence cannot drive strong conclusions.
- **Cheap learning beats expensive learning.** Internal data and desk research before primary research. Always.

---

## Known Limitations

- **Synchronous constraint:** Claude Code cannot run async operations. Agents that require waiting (survey distribution and collection, scheduling interviews) need external tooling. The squad designs the instruments — you run the fieldwork.
- **Token consumption:** Running the full pipeline is not cheap. Running specialist agents standalone is significantly more efficient for targeted questions.
- **Agent maturity varies:** Oprah, Kasparov, Gutenberg, and Florence Nightingale are production-ready. Vitruvius and Archimedes are v0.1 — functional but thinner. Machiavelli and Galileo have been substantially upgraded but haven't been run end-to-end yet.

---

## Pipeline Summary

| Step | Agent | Gate | What you decide |
|---|---|---|---|
| 1 | Machiavelli (Mode 1) | ◼ Gate 1 | Learning Agenda scope and priorities |
| 2 | Galileo (planning) | ◼ Gate 2 | Research methods and brief quality |
| 3 | Specialist agents | Lightweight check per agent | Flag weak outputs before synthesis |
| 3.5 | — | ◼ Gate 3 | Evidence base quality before synthesis |
| 4 | Galileo (synthesis) | ◼ Gate 4 | Insight quality and open gaps |
| 5 | Machiavelli (Mode 2) | — | Read only — final hand-off artifact |

---

## gitagent Compatibility

This repo follows the [gitagent](https://github.com/open-gitagent/gitagent/) standard.

```bash
gitagent export --format system-prompt   # single system prompt
gitagent export --format openai-agents   # OpenAI Agents SDK
gitagent export --format crewai          # CrewAI
```

---

## License

MIT
