# Experimentation Plan
## AI-Powered Collectibles Discovery Engine

**Owner:** Product & Data Science  
**Review Cadence:** Bi-weekly experiment review  
**Statistical Framework:** Frequentist A/B testing (95% confidence threshold)

---

## Experiment Governance

### Decision Framework
All experiments follow this decision criteria:
1. **Primary metric** must show statistically significant lift (p < 0.05)
2. **Guardrail metrics** must not degrade beyond -2% (relative)
3. **Minimum sample size** calculated per experiment before launch
4. **Minimum runtime:** 2 weeks to capture weekly seasonality patterns

### Guardrail Metrics (for all experiments)
- Page load time (p95 < 2s for recommendation modules)
- Seller fairness index (no single seller > 30% of homepage impressions)
- New item exposure rate (items < 7 days old = ≥ 10% of recommendation slots)
- Revenue per session (must not decline more than 2%)

---

## Experiment 1: Generic vs. Personalized Homepage

**Hypothesis:** Showing personalized recommendations on the homepage will increase CTR and session depth compared to the current curated/static experience.

**Experiment Design:**
- **Control (A):** Current homepage — editorially curated, same for all users
- **Treatment (B):** Personalized homepage — "Recommended for You" feed based on behavioral signals

**Audience:** Logged-in users with ≥ 3 prior interactions (excludes new users to avoid cold-start noise)

**Traffic Split:** 50/50

**Sample Size Calculation:**
- Baseline homepage CTR: 6.4%
- Minimum detectable effect (MDE): 15% relative lift → target 7.4%
- Power: 80%, Significance: 95%
- Required sample per variant: ~28,000 unique visitors
- Estimated runtime at current traffic: 3 weeks

**Primary Metric:** Homepage CTR (clicks on recommended items / homepage impressions)

**Secondary Metrics:**
- Items viewed per session
- Bid participation rate (session)
- Return visit rate (7-day)

**Guardrail Metrics:** Page load time, seller fairness index

**Expected Outcome:** +25–40% CTR lift based on comparable marketplace benchmarks

**Rollback Trigger:** If homepage CTR drops > 5% in treatment at 1-week interim check → pause and investigate

---

## Experiment 2: Ranking Algorithm — Popularity vs. Relevance vs. Hybrid

**Hypothesis:** A hybrid ranking algorithm that balances popularity signals with personalized relevance will outperform both pure popularity and pure relevance ranking on conversion metrics.

**Experiment Design:**
- **Control (A):** Popularity-based ranking (bids + views weighted by recency)
- **Treatment B:** Pure relevance ranking (cosine similarity to user preference vector)
- **Treatment C:** Hybrid ranking (70% relevance + 30% popularity + 10% freshness)

**Note:** 3-arm test — allocate 34%/33%/33% traffic

**Audience:** All logged-in users who perform a search

**Sample Size Calculation:**
- Baseline search CTR: 18%
- MDE: 20% relative lift
- Required sample per variant: ~22,000 search sessions
- Estimated runtime: 2.5 weeks

**Primary Metric:** Search result CTR (clicks on result / search sessions)

**Secondary Metrics:**
- View → bid conversion from search
- Search abandonment rate
- Avg. position of first click (lower = better)

**Pre-analysis Plan:**
- Segment by user tenure (new < 90 days vs. established)
- Segment by category (watches vs. cards vs. furniture — different popularity dynamics)

**Expected Outcome:** Hybrid (Treatment C) wins on conversion; pure relevance may win on CTR but lose on revenue

---

## Experiment 3: "More Like This" Placement

**Hypothesis:** Showing a "More Like This" shelf on item detail pages will increase session depth and reduce exit rates, compared to no similarity shelf.

**Experiment Design:**
- **Control (A):** Current item page — no similarity shelf
- **Treatment B:** "More Like This" shelf with 6 items (below item description)
- **Treatment C:** "More Like This" shelf with 6 items (sticky side rail on desktop)

**Audience:** All users who view an item detail page

**Primary Metric:** Items viewed per session (session depth)

**Secondary Metrics:**
- Exit rate from item detail page
- Bid participation in recommended items
- Revenue attributable to "More Like This" clicks

**Expected Outcome:** Treatment B wins on mobile, Treatment C wins on desktop — recommend device-segmented rollout

---

## Experiment 4: Onboarding Quiz for New Users

**Hypothesis:** Showing a short category-preference quiz during onboarding will improve recommendation quality and reduce time-to-first-bid for new users, compared to showing generic trending content.

**Experiment Design:**
- **Control (A):** New users see trending items on homepage
- **Treatment (B):** New users see category quiz → personalized homepage seeded from quiz answers

**Audience:** New users (first visit, account < 7 days)

**Primary Metric:** Time to first bid (days from signup)

**Secondary Metrics:**
- 7-day retention rate
- Homepage CTR for new users
- Items viewed in first session

**Expected Outcome:** 20% reduction in time-to-first-bid; 15% lift in 7-day retention

**Risk:** Quiz drop-off may reduce funnel entry rate — measure quiz completion rate as a guardrail (target > 65% completion)

---

## Experiment 5: Intent Chips in Search (Transparency Test)

**Hypothesis:** Showing parsed intent chips below the search bar ("I found: Watches · Vintage · Under $5,000") increases user trust in search results and reduces search refinement cycles.

**Experiment Design:**
- **Control (A):** Search results only, no intent display
- **Treatment (B):** Parsed intent chips shown below search bar; user can remove chips to refine

**Primary Metric:** Search refinement rate (users who modify query after initial search — lower is better if results are correct)

**Secondary Metrics:**
- Search-to-click rate
- User satisfaction (post-search survey, 5% sample)

---

## Experiment Roadmap

| Experiment | Priority | Start | End | Status |
|-----------|----------|-------|-----|--------|
| E1: Generic vs. Personalized Homepage | P0 | Week 1 | Week 4 | Planned |
| E2: Ranking Algorithm (3-arm) | P0 | Week 1 | Week 4 | Planned |
| E3: "More Like This" Placement | P1 | Week 3 | Week 6 | Planned |
| E4: New User Quiz | P1 | Week 5 | Week 8 | Planned |
| E5: Intent Chips | P2 | Week 7 | Week 10 | Backlog |

---

## Measurement & Reporting

### Weekly Experiment Dashboard
Each experiment tracked via:
- Daily metric snapshot (CTR, conversion, session depth)
- Statistical significance tracker (p-value, confidence interval)
- Segment breakdown (mobile vs. desktop, new vs. returning, category)

### Decision Log
All experiment decisions (ship/kill/iterate) logged with:
- Final metric results
- Statistical confidence level
- Business impact estimate
- Decision rationale

### Learnings Repository
Every completed experiment feeds a central learnings doc with:
- What we tested
- What we found
- What we shipped
- What surprised us
