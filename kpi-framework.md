# KPI Framework
## Bidding Experience Optimization

---

## Framework Overview

The KPI framework is organized across four layers: **Input Metrics** (leading indicators we control), **Output Metrics** (outcomes we care about), **Revenue Metrics** (business impact), and **Guardrail Metrics** (things we must protect).

---

## Layer 1: Input Metrics (Leading Indicators)

These measure the quality of our interventions. They're early signals of success/failure.

| Metric | Definition | Target | Frequency |
|--------|-----------|--------|-----------|
| Bid CTA visibility rate | % of item page sessions where bid CTA is visible without scrolling | 95% (was: 61%) | Daily |
| Real-time connection rate | % of item page sessions with active WebSocket (vs. fallback polling) | ≥90% | Daily |
| Modal load time (p95) | Time from CTA tap to modal appearing | < 300ms | Daily |
| Suggested bid chip usage rate | % of bids placed using chips vs. manual entry | > 40% | Daily |
| Auto-bid adoption rate | % of bidders who enable auto-bid in a session | > 20% | Weekly |

---

## Layer 2: Output Metrics (Engagement Outcomes)

These measure whether bidders are behaving differently as a result of the redesign.

### Participation
| Metric | Baseline | Target | Description |
|--------|----------|--------|-------------|
| Bid participation rate | 4.1% | 5.0% | Sessions with ≥1 bid / item detail page sessions |
| Bid start rate | ~6% | 9% | Sessions where bid modal opened / item detail sessions |
| Bid completion rate | 68% | 82% | Bids submitted / bid modals opened |
| Mobile bid completion rate | 54% | 72% | Completion rate on mobile devices specifically |

### Depth
| Metric | Baseline | Target | Description |
|--------|----------|--------|-------------|
| Avg. bids per bidder per auction | 1.8 | 2.4 | Total bids / unique bidders in auction |
| Outbid re-bid rate | 31% | 55% | Users who bid again after being outbid |
| Re-bid time (median) | 14 min | 4 min | Time between outbid notification and next bid |
| Auto-bid active rate | N/A | > 25% of auctions | Auctions with at least one auto-bidder |

### Engagement
| Metric | Baseline | Target | Description |
|--------|----------|--------|-------------|
| Avg. time on item page (bidders) | 3.2 min | 5.0 min | Time spent on page for users who bid |
| Watchlist-to-bid conversion | 22% | 30% | Watchlisted items that receive a bid from watcher |
| Return-to-auction rate | 38% | 52% | Bidders who return to check auction before end |

---

## Layer 3: Revenue Metrics (Business Outcomes)

| Metric | Baseline (Indexed) | Target | Description |
|--------|-------------------|--------|-------------|
| Auction revenue per listing | 100 | 115 | GMV per auction — primary revenue driver |
| Average final sale price vs. reserve | 147% | 162% | How far above reserve price auctions close |
| Buy rate (auction → sale) | 84% | 89% | % of auctions that end in a sale (vs. no bid / reserve not met) |
| Revenue per bidder per session | Indexed 100 | 120 | GMV attributed to bidder sessions |
| Take rate impact | Neutral | Neutral | Commission % must not change (structural) |

---

## Layer 4: Guardrail Metrics (Must Protect)

These are monitored daily. Breach = immediate escalation.

| Guardrail | Current | Threshold | Risk |
|-----------|---------|-----------|------|
| Bid dispute rate | 0.8% of bids | < 0.8% (must not increase) | Urgency causing rash decisions |
| Shill bid report rate | 0.2% of auctions | < 0.2% | Social proof appearing manipulative |
| Average bid amount | Indexed 100 | > 95 | Urgency causing panic underbidding |
| Auto-bid error rate | N/A | < 0.01% of auto-bids | Logic bugs causing overpayment |
| Page performance (p95 LCP) | 1.8s | < 2.2s | WebSocket adding load |

---

## Metric Hierarchy (Priority Order)

For decision-making when metrics conflict:

```
1. REVENUE METRICS (lagging — ultimate business goal)
   └── Auction revenue per listing
   
2. OUTPUT METRICS (leading — driver of revenue)
   ├── Bid participation rate  ← Most important leading indicator
   ├── Bid completion rate     ← Friction elimination signal
   └── Outbid re-bid rate     ← Engagement depth signal

3. INPUT METRICS (diagnostic — are our changes working?)
   ├── CTA visibility rate
   ├── Modal load time
   └── Suggested chip usage

4. GUARDRAIL METRICS (constraints — non-negotiable)
   ├── Bid dispute rate
   └── Shill bid report rate
```

---

## Segmentation

All metrics should be broken down across:

**User Type:**
- New bidder (first auction) vs. experienced bidder (5+ auctions)
- Auto-bid user vs. manual bidder

**Device:**
- Mobile (iOS / Android) vs. Desktop vs. Tablet
- *Mobile is highest priority — largest gap in current experience*

**Auction Type:**
- High-value (> $5,000 reserve) vs. mid-value ($500–$5K) vs. entry (<$500)
- Short auctions (< 24h) vs. standard (1–7 days)

**Category:**
- Watches / Sports Cards / Art / Furniture
- *Urgency mechanics may work differently by category price point*

---

## Reporting

| Report | Frequency | Audience | Key Metrics |
|--------|-----------|---------|-------------|
| Bidding daily pulse | Daily 9 AM | PM + Eng | Completion rate, participation rate |
| Mobile experience report | Weekly | Mobile Eng + PM | Mobile completion, CTA visibility |
| Auction health report | Weekly | Revenue + PM | Revenue per listing, buy rate |
| A/B test readout | Per experiment | All stakeholders | Primary metric + guardrails |
| Dispute & trust report | Weekly | Trust & Safety | Dispute rate, shill bid rate |

---

## Impact Estimation (Pre-Launch)

Assumptions for sizing opportunity:

- Monthly item detail page sessions: 2.4M
- Current bid participation: 4.1% = ~98,400 bids/month
- Current avg. bid value: ~$340
- Current monthly GMV from auctions: ~$33.5M

**If bid participation → 5.0%:**
- New bids/month: 120,000 (+22%)
- Additional GMV at same avg. bid: ~$7.5M/month
- At 15% take rate: ~$1.1M additional monthly revenue

**If outbid re-bid rate → 55% (from 31%):**
- Additional competitive bids on existing auctions
- Estimated +8–12% increase in final auction price on contested items
- Estimated additional GMV: ~$3–4M/month

**Conservative combined estimate: +$8–12M monthly GMV**  
*(Subject to A/B test confirmation — treat as directional sizing)*
