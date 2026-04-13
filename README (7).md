# Consignment Funnel Optimization — Seller Experience

> **Role:** Product Manager  
> **Domain:** Seller Experience · Supply Growth · AI Tooling  
> **Status:** Portfolio case study

---

## The Problem

A collectibles auction marketplace's primary supply channel — seller consignment submissions — was losing 66% of potential sellers mid-funnel. Only 34% of sellers who started a submission ever completed it. The platform was acquiring seller interest but not converting it.

The impact was direct: suppressed inventory supply, buyer dissatisfaction in niche categories, and millions in monthly GMV left on the table.

---

## My Role

Led product discovery, funnel analysis, and full requirements definition for the consignment experience redesign. Worked with design, ML, data engineering, and the authentication operations team.

---

## The Solution

A redesigned consignment funnel addressing the top 5 abandonment drivers:

| Feature | Problem It Solves | Abandonment It Targets |
|---------|-----------------|----------------------|
| **Step-by-step guided flow** | "Too long / overwhelming" | 41% of dropouts |
| **AI description generator** | "Didn't know what to write" | 29% of dropouts |
| **Price estimation tool** | "Uncertain about realistic price" | 24% of dropouts |
| **Save draft + recovery email** | "Got interrupted, forgot to come back" | 19% of dropouts |
| **Native camera (mobile)** | "Photo upload didn't work on phone" | 16% of dropouts |

---

## Key Documents

| Document | Description |
|----------|-------------|
| [`PRD.md`](PRD.md) | Full product requirements — problem, all 4 features, user stories, risks |
| [`funnel-analysis.md`](funnel-analysis.md) | Stage-by-stage drop-off data, segment analysis, root cause findings |
| [`user-journey-map.md`](user-journey-map.md) | Full emotional journey map — current vs. future state, phase by phase |
| [`experiment-roadmap.md`](experiment-roadmap.md) | 5 experiments with hypotheses, sample sizes, and expected outcomes |
| [`impact-estimation.md`](impact-estimation.md) | Conservative / base / optimistic scenarios; ROI analysis |

---

## Funnel Baseline

| Stage | Completion |
|-------|-----------|
| Start → Basic info | 78% |
| Basic info → Images | 61% |
| Images → Description | 44% |
| Description → Submit | 34% |
| Submit → Listed | 26% |

**Mobile is the critical gap:** 24% overall completion on mobile vs. 41% on desktop.

---

## Target Metrics

| Metric | Baseline | Target |
|--------|----------|--------|
| Submission completion rate | 34% | 55% |
| Time to submit | 24 min | 12 min |
| Seller 30-day retention | 28% | 42% |
| Listings per seller/quarter | 1.4 | 2.1 |
| Auth rejection rate | 24% | ≤18% |

**Estimated revenue impact (base case):** +$9.6M monthly GMV / +$1.49M monthly commission revenue

---

## Key Product Decisions & Tradeoffs

**Decision: AI description is pre-populated (opt-out, not opt-in)**  
An opt-in AI draft would be ignored by most sellers — blank-canvas anxiety makes it unlikely they'd click "Generate." Pre-populating the field with a draft removes the inertia. Sellers who want to write their own can clear the field or edit inline. Early testing on seller surveys showed strong preference for pre-populated.

**Decision: Show price range, not point estimate**  
A single number ($4,127) implies false precision and anchors sellers at that number even when it's wrong. A range ($3,800–$5,200) communicates uncertainty honestly and gives sellers agency. Design principle: build trust through transparency, not authority.

**Decision: Keep authentication gate**  
The simpler submission form could have led to removing or weakening the authentication review step. We explicitly chose not to — authentication is our brand trust differentiator. The goal is to make the pre-auth experience better, not to bypass the auth process.

**Decision: Expire drafts after 90 days (not forever)**  
Keeping drafts indefinitely creates operational complexity and misleading pipeline data. 90-day expiration with a 7-day warning email balances seller convenience with system hygiene.

---

## The AI Description Feature: Design Depth

The AI description generator was the most complex feature to get right:

- **Inputs:** Category, brand, era, condition grade, condition notes, uploaded photos (analyzed for markings/damage), optional seller free-text
- **Guardrail:** AI cannot assert condition facts beyond what seller provided (no hallucination of "mint" if seller said "good")
- **Human in the loop:** Authentication specialist reviews AI description against photos before listing goes live
- **Seller accountability:** Explicit disclaimer that seller is responsible for accuracy

This balances automation efficiency with the trust requirements of a high-value goods marketplace.

---

## What I'd Do Differently

- Instrument photo quality score earlier — adding a photo quality signal (not just "photos uploaded" but "photos are in focus and well-lit") would help identify if upload completion is translating to listing quality
- Talk to authentication specialists earlier in the process — they had critical insight into which funnel fields were actually used in their review, and which fields we collected but rarely used
