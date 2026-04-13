# AI-Powered Collectibles Discovery Engine

> **Role:** Product Manager  
> **Domain:** Buyer Experience · AI/ML · Personalization  
> **Status:** Portfolio case study

---

## The Problem

Collectors on a high-end auction marketplace struggled to discover relevant items. Search was keyword-only. The homepage was identical for every user. There was no way to find items similar to ones you loved. High-intent buyers with niche interests — rare watches, pre-war baseball cards, mid-century art — got zero personalization despite years of browsing history.

**Result:** 47% search abandonment. 6.4% homepage CTR. 3.2 pages viewed per session.

---

## My Role

Led end-to-end product discovery, strategy, and requirements definition for an AI-powered recommendation and discovery system. Worked cross-functionally with ML engineering, design, data science, and seller trust.

---

## The Solution

An AI-powered discovery engine with four integrated components:

| Component | What It Does |
|-----------|-------------|
| **Personalized Homepage** | Dynamic "Recommended for You" feed replacing static editorial content |
| **Smart Filters** | AI-suggested filter chips that adapt to search context + price trend data |
| **Similarity Engine** | "More Like This" shelf using vector embeddings — find items like what you love |
| **Intent-Aware Search** | Natural language parsing: "rare vintage watches under $5k" → structured filters |

---

## Key Documents

| Document | Description |
|----------|-------------|
| [`PRD.md`](PRD.md) | Full product requirements — problem, solution, user stories, tech architecture, risks |
| [`user-personas.md`](user-personas.md) | 3 detailed personas: The Focused Collector, Casual Browser, Gift Buyer |
| [`experimentation-plan.md`](experimentation-plan.md) | 5 A/B experiments with sample size calculations and hypothesis frameworks |
| [`metrics-dashboard.md`](metrics-dashboard.md) | North star, KPI hierarchy, guardrail metrics, alerting structure |

---

## Target Metrics

| Metric | Baseline | Target |
|--------|----------|--------|
| Homepage CTR | 6.4% | 9.0% (+41%) |
| Search abandonment | 47% | 35% (-26%) |
| Pages per session | 3.2 | 5.0 (+56%) |
| View → bid conversion | 4.1% | 4.7% (+15%) |

---

## Key Product Decisions & Tradeoffs

**Decision: Hybrid ranking over pure relevance**  
Pure relevance ranking risks "echo chambers" — showing users only what they already like. A hybrid (70% relevance + 20% popularity + 10% freshness) introduces healthy serendipity while maintaining personalization quality.

**Decision: Category quiz for new users over pure cold start**  
ML-based cold start requires data we don't have yet. A 6-question category quiz seeds the personalization model immediately and outperforms generic trending in early engagement metrics.

**Decision: Slot caps on sellers for homepage**  
Unconstrained recommendation could flood homepage with popular sellers, suppressing smaller sellers and new inventory. Capping any single seller at 30% of homepage slots balances personalization quality with marketplace fairness.

---

## Experimentation Approach

Five experiments mapped to distinct hypotheses:
1. **Generic vs. personalized homepage** — core personalization value test
2. **Ranking algorithm (3-arm)** — popularity vs. relevance vs. hybrid
3. **"More Like This" placement** — below fold vs. sticky rail
4. **New user quiz** — impact on time-to-first-bid
5. **Intent chips in search** — transparency vs. no-transparency

All experiments use frequentist testing (95% confidence, 80% power) with pre-registered guardrail metrics.

---

## What I'd Do Differently

- Start with seller-side insights earlier: recommendation quality is only as good as listing quality. A parallel initiative to improve listing metadata would compound the value of the similarity engine.
- Build explicit feedback loops: a "Not for me" signal on recommendations is low-effort and high-value for model accuracy.
