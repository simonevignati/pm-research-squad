---
produced_by: interview-agent
consumed_by: research-director
project: example-project
date: 2026-03-27
status: approved
---

# Interview Snapshot
**Respondent code:** R-01
**Date:** 2026-03-27
**Duration:** 52 min
**Research project:** example-project
**Brief reference:** Interview Brief — Profile A, 2026-03-20
**Interviewer:** [PM]

---

## Persona Identified

**Persona code:** P-01 (New)
**Job title:** Solo founder, IT consulting + e-commerce, 3 years in business
**JTBD:** When I finish a project for a client, I want to get paid without having
to chase them, so I can keep my cash flow predictable and focus on the next job.
**Behavioral archetype:** Pragmatic adopter — uses [Product] for invoicing only.
Manages payment collection separately, via bank transfer and occasional cash.
**Key behavioral signal:** Actively routes clients toward bank transfer to avoid
commission fees, even when the client would prefer to pay by card.
**Tools in ecosystem:** [Product] for invoicing, bank app for monitoring,
WhatsApp for payment chasing, spreadsheet for reconciliation, e-commerce platform
for online orders.
**Decision trigger:** Missed payment over 30 days. Triggers a manual follow-up
sequence (WhatsApp → email → phone).
**Switching barrier:** The invoicing history and client list built up over 3 years.
Switching would mean recreating records from scratch.

State: New persona

---

## The Most Important Thing This Person Told You

R-01 has two revenue streams — consulting and e-commerce — with fundamentally
different payment behaviors. On consulting: he invoices via [Product] but actively
avoids card acceptance because he perceives the commission as a margin leak,
not a business enablement cost. On e-commerce: he accepts cards because there
is no alternative. He has never connected these two experiences. When probed, he
estimated the time he spends on payment chasing at 3-4 hours per month, but had
never priced that time. This is the core opportunity: the cost of not accepting
cards is invisible to him. The commission is visible. A pricing or messaging
intervention that surfaces the hidden cost could shift his calculus.

---

## The Biggest Surprise

R-01 knows exactly how much he loses in late payments (he quoted a specific number
from memory). But he has never thought about what he spends to recover them. When
asked, he paused for 15 seconds. This asymmetry — precise loss visibility,
zero cost-of-chasing visibility — was not anticipated and appears across multiple
respondents. It suggests a product framing opportunity: show the cost of the
alternative, not just the cost of the feature.

---

## Workarounds Identified

**Workaround 1: WhatsApp payment chasing**
- What he does: After 30 days overdue, sends a WhatsApp message before any formal reminder
- Tool: Personal WhatsApp
- Point in workflow: After invoice due date passes without payment
- Why: "Clients respond faster to WhatsApp than to email. It feels personal.
  A formal reminder damages the relationship."

**Workaround 2: Bank transfer guidance in invoice footer**
- What he does: Adds IBAN and explicit wording ("preferred payment method: bank transfer")
  to every invoice
- Tool: [Product] invoice template customization
- Point in workflow: Invoice creation
- Why: "I lose 1.5-2% on card. On a €5,000 project that's €75-100. For a big client
  I just tell them to use bank transfer."

**Workaround 3: Separate e-commerce reconciliation spreadsheet**
- What he does: Manually exports e-commerce orders weekly and reconciles against [Product] invoices
- Tool: Excel
- Point in workflow: Weekly bookkeeping
- Why: "The two systems don't talk to each other. I need to know what I've billed
  vs. what I've actually collected, but there's no single view."

---

## Verbatim Quote Bank

**Quote R-01-Q-01:**
> "I don't use card on consulting because the client will pay eventually — it's just
> a matter of when. For e-commerce I have no choice, but there I just build the fee
> into the price anyway."

**Context:** Topic 2 (payment collection workflow), probe on why card acceptance
differs between his two businesses.
**What it reveals:** Price sensitivity to card fees is real but context-dependent.
When the client relationship is long-term and trust-based, bank transfer feels safe.
Card acceptance is associated with transactional, lower-trust contexts.
**OST use:** O-01 (cost of card acceptance perceived as margin leak, not enablement cost)

---

**Quote R-01-Q-02:**
> "I spend maybe 3-4 hours a month chasing. But I never thought about how much that
> costs me. I just do it."

**Context:** Topic 2, probe on time spent on payment recovery.
**What it reveals:** The hidden cost of the status quo is not visible to the user.
Comparison between "fee I pay" and "time I lose" has never been made consciously.
**OST use:** O-02 (invisible cost of alternative vs. visible cost of card acceptance)

---

**Quote R-01-Q-03:**
> "If I could send a link and the client pays immediately — even if I pay a fee — I
> think for smaller amounts I would do it. For a €200 repair job, yes. For a €5,000
> project, I don't know."

**Context:** Topic 3 (concept reaction), unprompted after hearing a description of
payment links.
**What it reveals:** WTP for card acceptance is amount-dependent. Small transactions:
fee is tolerable. Large transactions: fee is material enough to consider alternatives.
**OST use:** O-03 (tiered WTP by transaction size — potential for threshold-based pricing)

---

**Quote R-01-Q-04:**
> "My clients are not going to download an app to pay me. If I send them a link and
> they can just tap their card, that works. But it has to be that simple."
**Context:** Topic 3, probe on what would make card acceptance feel worth using.
**What it reveals:** Payer UX friction is a blocker. The value of payment links is
zero if the payer experience adds steps or requires account creation.
**OST use:** O-04 (payer UX must be zero-friction — no account, no app, no registration)

---

## Opportunities Surfaced

- **O-01** — Card acceptance perceived as margin leak, not time-saving tool
- **O-02** — Cost of payment chasing is invisible; makes fee comparison asymmetric
- **O-03** — WTP for card acceptance varies by transaction size; may support tiered pricing
- **O-04** — Payer UX is a primary adoption blocker; zero-friction is non-negotiable
- **O-05** — No unified view of billed vs. collected across revenue streams

---

## Mental Model Delta

Going in: assumed fee sensitivity was the primary blocker for card acceptance among
service businesses.

Coming out: fee sensitivity is real but secondary. The primary issue is that
R-01's mental model frames card acceptance as a cost, not a time-recovery tool.
The comparison he makes is "fee vs. zero" — not "fee vs. 3-4 hours of chasing."
The frame needs to shift before the price argument is even heard.

Additionally: the e-commerce / consulting split was not anticipated. Same user,
same product, completely different payment behavior. Segment definition may need
to account for mixed-revenue-stream founders separately from pure-service businesses.

---

## Open Threads

- Does the "invisible chasing cost" pattern hold across service businesses with
  longer-term client relationships? Test in next 3 interviews.
- Is €200 a meaningful threshold for card acceptance WTP, or was it specific to
  this respondent's business model?
- How many users have this consulting + e-commerce dual revenue structure?
  Internal data could answer this without more interviews.
