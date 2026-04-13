# Bidding Experience Optimization

> **Role:** Product Manager  
> **Domain:** Buyer Engagement · Auction UX · Growth  
> **Status:** Portfolio case study

---

## The Problem

The bidding flow on a high-end collectibles auction platform was the highest-friction moment in the buyer journey. A 3-page navigation away from the item, no suggested bid amounts, no real-time price updates, and a generic confirmation experience led to:

- **46% mobile bid abandonment** (54% completion vs. 78% on desktop)
- **32% drop-off** between opening the bid flow and submitting
- **31% outbid re-bid rate** — meaning most users who were outbid simply left

This was a direct revenue problem. More bids → more competition → higher final prices → more GMV.

---

## My Role

Led the end-to-end redesign of the auction bidding experience — from user research through requirements, flow design, A/B testing strategy, and stakeholder alignment.

---

## The Solution

A redesigned end-to-end bidding experience across four areas:

| Component | Change |
|-----------|--------|
| **Simplified UI** | 3-page flow → single bottom-sheet modal; 3 taps on mobile vs. 8 |
| **Real-time updates** | WebSocket-powered live price + bid count; no refresh needed |
| **Urgency triggers** | Live countdown timer with color shifts; real (non-inflated) social proof |
| **Auto-bid** | Proxy bidding integrated directly into bid modal with post-bid nudge |

---

## Key Documents

| Document | Description |
|----------|-------------|
| [`PRD.md`](PRD(1).md) | Full product requirements — problem, solution, user stories, risks, rollout plan |
| [`current-vs-proposed-flow.md`](current-vs-proposed-flow.md) | Side-by-side ASCII flow diagrams; drop-off analysis; UX change table |
| [`kpi-framework.md`](kpi-framework.md) | 4-layer KPI framework: inputs, outputs, revenue, guardrails + impact model |
| [`ab-testing-plan.md`](ab-testing-plan.md) | 5 experiments with hypotheses, sample sizes, and ethical guardrails |
| [`product-strategy.md`](product-strategy.md) | Strategic context, competitive landscape, 12-month roadmap |

---

## Target Metrics

| Metric | Baseline | Target |
|--------|----------|--------|
| Bid participation rate | 4.1% | 5.0% (+22%) |
| Bid completion rate | 68% | 82% (+21%) |
| Mobile completion rate | 54% | 72% (+33%) |
| Avg. bids/bidder/auction | 1.8 | 2.4 (+33%) |
| Outbid re-bid rate | 31% | 55% (+77%) |

**Estimated revenue impact (base case):** +$8–12M monthly GMV

---

## Key Product Decisions & Tradeoffs

**Decision: Modal over page navigation**  
Navigating users to a separate bid page creates context loss and adds multiple taps. A bottom-sheet modal keeps users on the item page, maintains context, and reduces step count from 8 taps → 3 on mobile. Tradeoff: added complexity in form state management.

**Decision: Suggested bid chips over free-text entry only**  
Free text forces users to calculate "what's an appropriate increment?" Suggested chips (min, mid, bold) remove this cognitive load. Tradeoff: some users may feel nudged toward higher bids — mitigated by always showing minimum first.

**Decision: Auto-bid opt-in (not opt-out) default — initially**  
Auto-bid ON as default would drive higher adoption and auction revenue, but risks trust issues if users don't understand what they signed up for. Starting with opt-in + clear nudge after first bid is the safer path. Revisit after measuring adoption.

**Decision: Real watcher counts only for social proof**  
It would be simple to show inflated "X people viewing this" numbers. We explicitly don't. All social proof metrics are real counts, reviewed by Trust & Safety, and the feature is killed if dispute rates increase.

---

## The Ethical Constraint I'm Proud Of

The social proof and urgency features required an explicit "no false scarcity" design principle — signed off with Trust & Safety before a line of code was written. Every count is real. The design makes this fast; it doesn't make it manipulative.

---

## What I'd Do Differently

- Instrument "bid intent signals" earlier (e.g., how long a user hovers on the bid CTA) to better understand drop-off before the modal even opens
- Run the mobile-specific experiments before desktop — the mobile gap was the larger opportunity
