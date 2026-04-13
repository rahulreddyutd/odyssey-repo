# A/B Testing Plan
## Bidding Experience Optimization

---

## Testing Philosophy

We test atomically (one change at a time) where possible, but may run interaction experiments when features are deeply coupled (e.g., real-time updates + countdown timer are always tested together since they share WebSocket infrastructure).

**Framework:** Frequentist A/B testing  
**Significance threshold:** p < 0.05 (95% confidence)  
**Power:** 80%  
**Minimum runtime:** 14 days per experiment (to capture weekly patterns in auction behavior)  
**Experiment platform:** Internal experimentation tooling with assignment at user-ID level

---

## Experiment 1: Countdown Timer vs. Static End Time

**The question:** Does showing a live countdown ("Ends in 2h 14m") instead of an absolute timestamp ("Ends Apr 22 at 3:47 PM") increase bid urgency and participation?

**Hypothesis:** A live countdown creates temporal loss aversion, increasing the likelihood that browsing users convert to bidders — especially in the final hours of an auction.

**Variants:**
- **Control (A):** Static absolute end time ("Ends: April 22, 3:47 PM EST")
- **Treatment (B):** Live countdown ("⏱ Ends in 2h 14m") with color shift at < 2h (amber) and < 15min (red)

**Audience:** All users who view an item detail page

**Sample size:**
- Baseline bid participation: 4.1%
- MDE: 15% relative lift → 4.7%
- Sample per variant: ~25,000 item detail page sessions
- Estimated runtime at current traffic: 2 weeks

**Primary metric:** Bid participation rate (item page sessions → ≥1 bid)

**Secondary metrics:**
- Avg. bids per auction (does urgency increase depth, not just participation?)
- Bids placed in final 2h of auction (specific urgency zone)
- Avg. session duration on item page

**Guardrail:** Bid dispute rate must not increase (urgency ≠ regret)

**Segmentation to watch:**
- Effect likely stronger on auctions ending within 6 hours — pre-segment this
- Mobile vs. desktop (countdown may be more impactful on mobile where clock isn't shown)

**Expected outcome:** +10–20% bid participation lift in final 2h window

---

## Experiment 2: Auto-Bid Default Setting

**The question:** Should auto-bid be OFF by default (user opts in) or ON by default (user opts out)?

**Hypothesis:** Auto-bid ON as default will increase the percentage of auctions with an auto-bidder, raising final auction prices and revenue — but may cause trust issues if users don't understand what they opted into.

**Variants:**
- **Control (A):** Auto-bid toggle OFF by default in bid modal
- **Treatment (B):** Auto-bid toggle ON by default in bid modal (with prominent "What's this?" link)
- **Treatment (C):** Auto-bid toggle OFF with a persistent nudge prompt ("Tip: Set a max bid and we'll handle re-bids for you")

**Audience:** All users who open the bid modal  
**Traffic split:** 34% / 33% / 33%

**Primary metric:** Auto-bid adoption rate (% of bidding sessions with auto-bid active)

**Secondary metrics:**
- Auction revenue per listing (auto-bid → higher final prices)
- Bid dispute rate (proxy for regret from unexpected auto-bids)
- User support contacts about auto-bid (direct signal of confusion)

**Guardrail:** Bid dispute rate is a hard guardrail — if Treatment B increases disputes > 0.8% baseline, kill immediately

**Ethical note:** Treatment B (ON by default) must not default users into spending beyond intent. The max bid field must be prominently labeled with "Maximum amount you'll pay" and confirmation must clearly state the amount. Trust & Safety must sign off before launch.

**Expected outcome:** Treatment B wins on adoption and revenue; Treatment C is the safer win if B causes disputes

---

## Experiment 3: Social Proof Messaging Impact

**The question:** Which social proof message, if any, meaningfully increases bid participation without feeling manipulative?

**Variants:**
- **Control (A):** No social proof copy (current state)
- **Treatment B:** "X people watching" (watcher count)
- **Treatment C:** "X bids placed" (bid count)
- **Treatment D:** "X people watching · Y bids placed" (both)

**Audience:** All item detail page sessions

**Primary metric:** Bid participation rate

**Secondary metrics:**
- Bid depth (bids per bidder in auction)
- Shill bid report rate (key trust guardrail)
- User satisfaction survey (shown to 3% sample at end of session)

**Integrity requirements:**
- All counts must be real — zero tolerance for inflated numbers
- "X people watching" = actual real-time watcher count
- Counts below a threshold (< 3) should not be shown (avoid "1 person watching")
- Trust & Safety pre-approved copy variants before test launches

**Expected outcome:** Treatment C ("X bids placed") likely wins — it signals competitive demand without implying surveillance of other users

---

## Experiment 4: Simplified Bid Modal — Step Count

**The question:** Does reducing the bid flow to a single-step modal (vs. current 3-page flow) increase bid completion rates?

**Variants:**
- **Control (A):** Current 3-page flow (item page → bid entry page → confirmation page)
- **Treatment (B):** New single bottom-sheet modal with inline confirmation state

**Note:** This is the highest-impact experiment and should be prioritized as Experiment #1 in the roadmap. It tests the core flow redesign.

**Audience:** All users who click "Place a Bid" (mobile-first analysis)

**Primary metric:** Bid completion rate (bid modal/page opened → bid submitted)

**Secondary metric:** Mobile bid completion rate (isolated)

**Sample size:**
- Baseline completion rate: 68% (54% mobile)
- MDE: 15% relative lift → 78% overall (62% mobile)
- Required: ~5,000 bid flow starts per variant
- Estimated runtime: 1.5 weeks at current bid volume

**Expected outcome:** +18–25% relative lift in completion rate; mobile effect likely 2x

---

## Experiment 5: Outbid Notification Speed

**The question:** Does reducing outbid notification latency from ~10 minutes to < 60 seconds significantly increase re-bid rates?

**Variants:**
- **Control (A):** Current outbid notification (email, average 8–12 min delay)
- **Treatment B:** Near-real-time push + in-app notification (< 60 seconds)
- **Treatment C:** Near-real-time push + in-app + one-tap "Re-bid to $X" CTA in notification

**Primary metric:** Outbid re-bid rate (users who bid again after being outbid)

**Secondary metrics:**
- Re-bid speed (time between outbid notification and next bid)
- Auction revenue on auctions with competitive bidding (multiple bidders)

**Expected outcome:** Treatment C wins significantly — combining speed + convenience of one-tap re-bid

---

## Experiment Roadmap

| # | Experiment | Priority | Est. Runtime | Start | Status |
|---|-----------|----------|-------------|-------|--------|
| 1 | Simplified Bid Modal (4) | P0 | 2 weeks | Week 1 | Planned |
| 2 | Countdown Timer (1) | P0 | 2 weeks | Week 1 | Planned |
| 3 | Outbid Notification Speed (5) | P1 | 2 weeks | Week 3 | Planned |
| 4 | Social Proof Messaging (3) | P1 | 3 weeks | Week 4 | Planned |
| 5 | Auto-Bid Default (2) | P2 | 3 weeks | Week 6 | Backlog |

*Note: Experiments 1 and 2 can run concurrently on different randomization units (user-ID for modal, session-ID for timer) — verify no interaction effect.*

---

## Statistical Notes

### Multiple Testing Correction
Running concurrent experiments requires care:
- Use Bonferroni correction when looking at the same metric across multiple running tests
- Primary metrics isolated to each experiment — secondary metrics may overlap

### Novelty Effect
New UI elements often see inflated initial engagement. Plan for:
- 2-week minimum runtime regardless of early significance
- Monitor week 1 vs. week 2 metrics separately to detect novelty decay

### Network Effects Consideration
Auction dynamics create network effects (one bidder's behavior affects another's). Ideally:
- Randomize at the auction level, not user level, for experiments that affect bid depth
- This is complex — document limitation in experiment pre-registration

---

## Experiment Template

For each new experiment, complete this before launch:

```
Experiment Name:
Hypothesis:
Control description:
Treatment description(s):
Audience + exclusions:
Traffic split:
Primary metric:
Secondary metrics:
Guardrail metrics:
Sample size calculation:
Estimated runtime:
Pre-analysis plan (segments):
Rollback criteria:
Decision framework:
```
