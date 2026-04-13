# Impact Estimation
## Consignment Funnel Optimization — Seller Experience

---

## Methodology

This document estimates the business impact of the Consignment Funnel Optimization initiative. We use a bottom-up model grounded in current funnel data, with conservative, base, and optimistic scenarios.

All GMV figures are directional estimates. Actual impact will be measured via controlled A/B tests.

---

## Baseline Metrics

| Metric | Current Value |
|--------|--------------|
| Monthly seller sessions starting submission | 12,400 |
| Submission completion rate | 34% |
| Monthly completed submissions | 4,216 |
| Authentication approval rate | 76% |
| Monthly items listed | 3,204 |
| Avg. GMV per listing (across all categories) | $4,850 |
| Monthly total GMV (consignment) | $15.5M |
| Platform commission rate (avg.) | 15.5% |
| Monthly commission revenue | $2.4M |

---

## Impact Model

### Driver 1: Submission Completion Rate Improvement

Our primary intervention target. Moving from 34% → 55% completion rate.

**Conservative case (34% → 45%):**
```
Submissions/month:  12,400 × 45% = 5,580 (vs. 4,216 baseline)
Additional submissions: +1,364/month
Additional listings (at 76% auth): +1,037/month
Additional GMV: 1,037 × $4,850 = $5.0M/month
Additional revenue: $5.0M × 15.5% = $775K/month
```

**Base case (34% → 55%):**
```
Submissions/month: 12,400 × 55% = 6,820
Additional submissions: +2,604/month
Additional listings: +1,979/month
Additional GMV: 1,979 × $4,850 = $9.6M/month
Additional revenue: $9.6M × 15.5% = $1.49M/month
```

**Optimistic case (34% → 62%):**
```
Submissions/month: 12,400 × 62% = 7,688
Additional submissions: +3,472/month
Additional listings: +2,639/month
Additional GMV: 2,639 × $4,850 = $12.8M/month
Additional revenue: $12.8M × 15.5% = $1.98M/month
```

---

### Driver 2: Seller Retention Improvement

Moving 30-day seller retention from 28% → 42%.

Better first-time experience drives sellers to return with more items.

**Base case (28% → 42%):**
- Monthly new sellers completing submission: ~1,800 (estimating 43% are first-timers)
- Additional retained sellers: 1,800 × (42% - 28%) = +252 retained sellers/month
- Retained sellers submit avg. 1.4 additional items in first 90 days
- Additional listings from retention improvement: 252 × 1.4 = +353 additional listings/month
- Additional GMV: 353 × $4,850 = $1.7M/month
- Additional revenue: $1.7M × 15.5% = $264K/month

---

### Driver 3: Price Accuracy Improvement (Price Tool)

Improved reserve price setting leads to higher sell-through rates.

**Current state:** 
- 22% of listed items have reserves set above market rate (don't sell)
- Auth cost wasted, seller dissatisfied

**Projected improvement with price tool:**
- Reserve-above-market rate: 22% → 13% (conservative estimate based on tool nudging sellers toward market range)
- Additional auctions that clear: 3,204 listings × (22% - 13%) = +288 items sold/month
- Avg. additional GMV: 288 × $4,850 = $1.4M/month
- Additional revenue: $1.4M × 15.5% = $217K/month

---

## Consolidated Impact Summary

| Scenario | Additional Monthly GMV | Additional Monthly Revenue |
|----------|----------------------|---------------------------|
| Conservative | $7.1M | $1.1M |
| Base | $12.7M | $1.97M |
| Optimistic | $16.9M | $2.6M |

**Base case annualized: +$152M GMV / +$23.6M revenue**

---

## Investment Estimate

| Resource | Estimate |
|---------|----------|
| Engineering (3 FTEs × 3 months) | ~$450K fully-loaded |
| ML/AI model development | ~$150K |
| Design (1 FTE × 3 months) | ~$90K |
| Data science (0.5 FTE × 4 months) | ~$80K |
| QA + testing | ~$60K |
| **Total investment estimate** | **~$830K** |

---

## ROI Analysis

| Scenario | Annual Revenue Impact | Investment | Payback Period | 12-Month ROI |
|----------|----------------------|-----------|---------------|-------------|
| Conservative | $13.2M | $830K | < 1 month | 15.9x |
| Base | $23.6M | $830K | < 1 month | 28.4x |
| Optimistic | $31.2M | $830K | < 1 month | 37.6x |

**Even the conservative case delivers a strong positive return within the first month of launch.**

---

## Non-Revenue Impact

### Authentication Team Efficiency
- Fewer low-quality submissions (AI description reduces misrepresentation)
- Estimated: auth rejection rate drops from 24% → 18%
- Auth cost savings: ~$35K/month (fewer specialist review cycles)

### Buyer Experience
- More supply in niche categories reduces "no results" pages
- Estimated: 15% increase in category inventory depth where funnel improves most (Watches, Art)
- Indirect buyer conversion improvement: unmeasured but positive

### Seller NPS
- Current seller NPS (post-submission): +12
- Target: +28
- High-NPS sellers are more likely to return and refer other sellers (word-of-mouth supply acquisition)

---

## Risks to Impact Model

| Risk | Probability | Impact on Model | Mitigation |
|------|------------|----------------|-----------|
| AI description quality below threshold | Medium | -30% base case | Iterative model improvement; human fallback |
| Price tool anchors sellers too conservatively | Low | -10% base case | Show ranges, not point estimates; emphasize upside |
| Increased completions include lower-quality items | Medium | -15% GMV/listing assumption | Authentication maintains quality gate |
| Engineering timeline slips by 2 months | Medium | 2-month delay on revenue realization | Phased launch — ship save draft + guided flow first |

---

## Measurement Plan

### 90-Day Post-Launch Targets

| Metric | Baseline | 90-Day Target | Measurement Method |
|--------|----------|---------------|--------------------|
| Submission completion rate | 34% | 50–55% | Direct funnel measurement |
| Time to submit (avg.) | 24 min | 14 min | Session timing |
| Seller 30-day retention | 28% | 38%+ | Cohort retention analysis |
| Monthly items listed | 3,204 | 4,500+ | Listing volume |
| Auth rejection rate | 24% | ≤18% | Auth team tracking |
| Additional monthly GMV | $15.5M | $21–24M | Revenue dashboard |

### 180-Day Post-Launch Targets

| Metric | Target |
|--------|--------|
| Submission completion rate | 55%+ |
| Seller 30-day retention | 42% |
| Listings per active seller | 2.1 |
| Monthly GMV | $25M+ |
