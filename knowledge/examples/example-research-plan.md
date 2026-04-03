---
produced_by: research-director
consumed_by: interview-agent, survey-agent, desk-research-agent
project: example-project
date: 2026-03-19
status: approved
---

# Research Plan
**Learning Agenda reference:** Learning Agenda — example-project, 2026-03-15
**Date:** 2026-03-19
**Research objective:** Determine whether [Product] should add card payment acceptance
to its invoicing product, and if so, for which customer segment and at what price.

---

## Research Workstreams

### Workstream 1: Demand signal — do service businesses want card acceptance on invoices?
**Knowledge gap:** We do not know if service businesses (consulting, freelance, professional
services) want to collect card payments on invoices, or whether they are content with
bank transfer.
**Method:** Survey (quantitative prevalence + behavioral frequency)
**Supporting method(s):** In-depth interviews (mental models, workarounds)
**Rationale:** Survey gives us prevalence at scale. Interviews give us the why behind
the numbers — which segments are blocked by fee sensitivity vs. client expectation.
**Success criteria:** Can state with ≥70% confidence the % of active invoicers who
currently receive any card payment, and whether that % differs by business type.
**Dispatch to:** survey-agent (primary), interview-agent (supporting)
**Sequencing:** Parallel. Interview guide informed by survey questions but not dependent
on survey results.
**Priority:** Critical

---

### Workstream 2: Fee sensitivity — what do users actually pay vs. what they perceive?
**Knowledge gap:** We assume fee sensitivity is the primary adoption blocker. We don't
know if this is accurate, or whether other factors (payer UX, client preference,
trust) are more important.
**Method:** In-depth interviews
**Rationale:** Fee sensitivity is a mental model question — not directly measurable
by survey. Need to hear how users frame the cost/benefit tradeoff in their own words.
**Success criteria:** Identify the top 3 reasons service businesses do not currently
accept cards on invoices. Determine whether fee is cited spontaneously or only when
prompted.
**Dispatch to:** interview-agent
**Sequencing:** Parallel with WS1
**Priority:** Critical

---

### Workstream 3: Competitor landscape — how do others price card acceptance for SMBs?
**Knowledge gap:** We lack a current benchmark of what competitors charge for SMB
card acceptance, and how they position the fee (flat rate vs. %, per-transaction vs.
subscription).
**Method:** Competitive intelligence + desk research
**Rationale:** Competitor pricing is publicly available; no primary research needed.
Positions our pricing relative to the market before we design pricing options.
**Success criteria:** Pricing table with ≥5 direct or adjacent competitors, with
model type, rate, and segment-fit assessment for each.
**Dispatch to:** competitive-intelligence-agent, desk-research-agent
**Sequencing:** Parallel. Results feed pricing-agent in WS4.
**Priority:** Important

---

### Workstream 4: Pricing model — what pricing model fits this product?
**Knowledge gap:** We have not evaluated pricing models for card acceptance. We need
a recommendation with margin floor, WTP range, and activation impact before deciding
what to charge.
**Method:** Pricing analysis
**Supporting method(s):** WTP questions embedded in survey (WS1)
**Rationale:** Pricing is a product decision. Need to evaluate full taxonomy, not just
pick a % rate.
**Success criteria:** A recommended pricing model with worked example, margin floor,
WTP range from survey data, and top-line metric impact table.
**Dispatch to:** pricing-agent
**Sequencing:** After WS3 (needs competitor benchmark as input)
**Priority:** Critical

---

## Dispatch Summary

| Workstream | Agent | Priority | Dependency | Estimated time |
|---|---|---|---|---|
| WS1 — Demand signal | survey-agent | Critical | None | 2 weeks |
| WS2 — Fee sensitivity | interview-agent | Critical | None | 2 weeks (5 interviews min) |
| WS3 — Competitor pricing | competitive-intelligence-agent + desk-research-agent | Important | None | 3 days |
| WS4 — Pricing model | pricing-agent | Critical | After WS3 | 2 days after WS3 |

---

## Interview Recruitment

**Target profiles:**
- Profile A: Service business (consulting, freelance, professional services),
  active invoicer (10+ invoices/month), no current card acceptance
- Profile B: Service business, currently accepts card in at least one channel,
  uses [Product] for invoicing
- Profile C: Mixed revenue (service + e-commerce or retail), invoices and
  sells products

**Recruitment pool:** Survey respondents who indicated willingness to be interviewed.
**Target N:** 6-8 interviews across profiles (minimum 2 per profile).
**Minimum before synthesis:** 5 completed interviews.

---

## Survey Behavioral Segments

Primary segment cut:
- Active invoicers (5+ invoices/month, last 30 days)
- Occasional invoicers (1-4 invoices/month)
- Dormant invoicers (no invoice in last 60 days)

Secondary cuts:
- Business type (service / product / mixed)
- Geography (where relevant to regulatory or competitive differences)
- Plan tier (if correlated with payment volume)
