# Metrics Dashboard
## AI-Powered Collectibles Discovery Engine

**Last Updated:** April 2026  
**Review Cadence:** Weekly (Monday AM standup)  
**Owner:** Product Analytics

---

## North Star Metric

**Qualified Discovery Sessions** — Sessions where a user views ≥ 3 unique items AND spends ≥ 90 seconds browsing, indicating genuine discovery intent vs. accidental traffic.

*Why this?* It captures meaningful engagement without being gamed by page views alone. A user who lands, clicks one item, and leaves is not "discovering."

**Target:** 35% of all logged-in sessions qualify as Qualified Discovery Sessions (baseline: 22%)

---

## Metric Hierarchy

```
NORTH STAR: Qualified Discovery Sessions
│
├── ACQUISITION (How do users enter discovery?)
│   ├── Homepage CTR
│   └── Search-to-result engagement rate
│
├── ENGAGEMENT (Are users discovering?)
│   ├── Items viewed per session
│   ├── "More Like This" CTR
│   └── Return visit rate (7-day)
│
└── CONVERSION (Does discovery drive revenue?)
    ├── View → bid rate
    ├── View → purchase rate
    └── Revenue per discovery session
```

---

## Primary KPIs

### Acquisition Metrics

| Metric | Definition | Baseline | Target | Measurement |
|--------|-----------|---------|--------|-------------|
| Homepage CTR | Clicks on recommended items / homepage sessions | 6.4% | 9.0% | Daily |
| Search CTR | Clicks on search results / searches performed | 18% | 26% | Daily |
| Search abandonment rate | Searches with zero result clicks / total searches | 47% | 35% | Daily |
| Onboarding quiz completion | Users who complete quiz / users shown quiz | N/A | ≥65% | Daily |

### Engagement Metrics

| Metric | Definition | Baseline | Target | Measurement |
|--------|-----------|---------|--------|-------------|
| Items viewed per session | Unique item detail page views per session | 3.2 | 5.0 | Daily |
| Session duration | Avg. minutes per session (logged-in) | 6.4 min | 9.0 min | Daily |
| "More Like This" CTR | Clicks on similarity shelf / similarity shelf impressions | N/A | ≥12% | Daily (post-launch) |
| 7-day return visit rate | Users who return within 7 days / total users | 34% | 42% | Weekly |
| Watchlist additions per session | Avg. items added to watchlist | 0.4 | 0.7 | Daily |

### Conversion Metrics

| Metric | Definition | Baseline | Target | Measurement |
|--------|-----------|---------|--------|-------------|
| View → bid rate | Sessions with ≥1 bid / sessions with ≥1 item view | 4.1% | 4.7% | Daily |
| View → purchase rate | Sessions with purchase / sessions with ≥1 item view | 1.8% | 2.1% | Daily |
| Revenue per session | GMV / total logged-in sessions | $12.40 | $14.50 | Weekly |
| Time to first bid (new users) | Days from signup to first bid placed | 11 days | 8 days | Weekly |

---

## Guardrail Metrics

These must not degrade. If any guardrail is breached, the feature team is paged immediately.

| Guardrail | Threshold | Monitoring |
|-----------|-----------|-----------|
| Recommendation page load time (p95) | < 2.0 seconds | Real-time alert |
| Seller concentration (top seller's share of homepage) | < 30% | Daily |
| New item exposure rate (items < 7 days) | ≥ 10% of recommendation slots | Daily |
| Recommendation diversity (unique categories in a session's recs) | ≥ 3 categories | Daily |

---

## Counter Metrics (watch for negative side effects)

| Counter Metric | Risk | Threshold |
|---------------|------|-----------|
| Recommendation irrelevance report rate | Users flagging bad recs | Alert if > 2% of impressions |
| Filter abandonment rate | Smart filters confusing users | Alert if > 20% |
| Seller listing view inequality (Gini coefficient) | Rich-get-richer in discovery | Alert if Gini > 0.65 |

---

## Segment Breakdowns

All primary metrics should be tracked across these dimensions:

**User Segments:**
- New (< 30 days) vs. Returning (30–180 days) vs. Power (180+ days)
- High-value (lifetime bids > $5K) vs. Mid-value vs. Low-value

**Device:**
- Mobile (iOS/Android) vs. Desktop vs. Tablet

**Category:**
- Watches / Sports Cards / Art / Furniture / Other
- Category-level CTR and conversion may diverge significantly

**Traffic Source:**
- Direct / Email / Organic Search / Paid / Social

---

## Dashboard Layout

### Section 1: Daily Pulse (Top of Dashboard)
- Qualified Discovery Sessions (vs. prior week)
- Homepage CTR sparkline (7-day)
- Search CTR sparkline (7-day)
- Items per session (7-day)

### Section 2: Experiment Tracker
Live table showing all running A/B tests with:
- Experiment name
- Traffic allocation
- Days running
- Primary metric (control vs. treatment with p-value)
- Status (running / significant / concluded)

### Section 3: Funnel Visualization
```
Homepage Visit → Item View → Watchlist/Bid Intent → Bid Placed → Purchase
    100%          38%              14%                   4.1%         1.8%
```
Shows daily drop-off at each stage with WoW change.

### Section 4: Recommendation Quality
- "More Like This" CTR by category
- Similarity shelf position heatmap (which slot gets clicked most)
- Irrelevance flag rate by recommendation source

### Section 5: Seller Fairness
- Top 10 sellers by homepage impression share
- Gini coefficient (listing view distribution)
- New item exposure rate

---

## Alerting

| Alert | Condition | Channel | Owner |
|-------|-----------|---------|-------|
| Homepage CTR drops > 10% WoW | Daily check | Slack #product-alerts | PM |
| Page load p95 > 2s | Real-time | PagerDuty | Eng |
| Seller concentration > 30% | Daily | Slack #seller-trust | PM |
| Search abandonment spike | > 55% on any day | Slack #search | PM |

---

## Reporting Cadence

| Report | Frequency | Audience |
|--------|-----------|---------|
| Daily pulse email | Daily, 9 AM | PM, Eng, Data |
| Weekly metrics review | Monday, 10 AM | Full product team |
| Monthly business review | First Monday of month | Leadership |
| Experiment readout | Per experiment conclusion | Stakeholders |
