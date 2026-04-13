# Product Strategy
## Bidding Experience Optimization

---

## Strategic Context

Auctions are the beating heart of a collectibles marketplace. Every dollar of revenue flows through a successful bid. Yet the bidding experience — the most critical user moment — has been neglected in favor of discovery and supply features. This creates an asymmetry: we acquire users and inventory well, but convert poorly at the moment of transaction.

This strategy document frames why we're investing now, what winning looks like, and how this initiative fits into the broader marketplace strategy.

---

## Why Now?

Three signals converge to make this the right moment:

**1. Mobile is the new primary device for bidding, but the experience hasn't caught up.**
56% of auction traffic is now mobile. Mobile bid completion rate (54%) lags desktop (78%) by 24 points. Competitors who've invested in mobile-native bidding are closing this gap faster than we are.

**2. Competing platforms are winning on UX, not on inventory.**
User research shows that collectors with accounts on multiple platforms choose where to bid based on experience, not selection. Friction is a competitive vulnerability.

**3. Bidding depth is the largest untapped revenue lever.**
Auctions with 3+ active bidders produce 2.4x the GMV of auctions with 1–2 bidders. We currently average 1.8 bids per bidder per auction. Moving this to 2.4 would add more revenue than acquiring 30% more new users.

---

## Strategic Bets

This initiative is grounded in three strategic bets:

**Bet 1: Friction is the primary conversion barrier — not intent.**
We believe most users who open the bid modal intend to bid. The 32% who drop out between modal open and bid submission are lost to friction, not cold feet. Fixing the flow converts existing intent.

**Bet 2: Urgency is underleveraged.**
Collectors are by nature competitive. The right urgency signals (countdowns, real-time updates, activity indicators) accelerate the bid decision without manufacturing false scarcity. We're currently showing none of these.

**Bet 3: Auto-bid is a long-term engagement driver, not just a convenience feature.**
Users who set auto-bids are more engaged, have higher 30-day return rates, and bid in more categories. Auto-bid converts casual bidders into committed participants. This compounds over time.

---

## Positioning

**Internal positioning:** The Bidding Experience Optimization initiative is not a redesign for its own sake. It is a revenue optimization initiative targeting our highest-leverage conversion moment.

**User positioning:** "Bidding should feel as fast as deciding." Collectors know what they want. The platform should get out of the way.

---

## Success Definition

**At 6 months post-launch, we declare success if:**
- Bid participation rate is ≥ 5.0% (from 4.1%)
- Bid completion rate is ≥ 80% (from 68%)
- Auction revenue per listing has increased ≥ 12% (indexed)
- Mobile and desktop completion rates have converged to within 10 points

**At 12 months:**
- Auto-bid is active on ≥ 35% of auctions
- Outbid re-bid rate is ≥ 50% (from 31%)
- Avg. bids per bidder per auction is ≥ 2.4 (from 1.8)

---

## Competitive Landscape

| Platform | Bid UX Strengths | Our Advantage |
|---------|-----------------|---------------|
| Sotheby's Online | Trusted brand, clean UI | We have broader category depth, faster auction cadence |
| Goldin (sports cards) | Category-specialized, mobile-first | We win on cross-category discovery |
| eBay Auctions | Scale, familiarity | We win on curation, trust, and collector community |
| Heritage Auctions | Deep specialist expertise | We win on UX velocity — Heritage is slow and complex |

**Key insight:** No competitor has nailed mobile bidding + real-time updates + auto-bid together. This is a genuine whitespace opportunity.

---

## Principles Guiding Design Decisions

1. **Speed over completeness.** Every additional step loses users. If we can collect information later, we don't collect it during bidding.

2. **Transparency builds trust.** Real-time prices, real social proof, honest urgency. We never inflate numbers or manufacture scarcity.

3. **Mobile first, always.** Every design decision is made for a 6-inch screen first. Desktop is the adaptation.

4. **Urgency, not anxiety.** We help users make faster decisions about things they already want. We don't push users toward decisions they'll regret.

---

## Roadmap (12-Month View)

### Q3 2026 (v1 Launch)
- Simplified bid modal (bottom sheet, suggested amounts)
- Real-time price updates via WebSocket
- Live countdown timer with color shift
- "You're the highest bidder" confirmation state
- Auto-bid in modal with post-bid nudge
- Near-real-time outbid notifications

### Q4 2026 (v2)
- One-tap re-bid from outbid notification
- Bid history view (see all your active auctions)
- Auto-bid management dashboard
- Watchlist → bid conversion optimization

### Q1 2027 (v3)
- Bidding from search results (without entering item detail page)
- "Auction room" experience for high-value auctions (live-ish feel)
- SMS bidding via text (evaluate demand first)

---

## Stakeholder Alignment

| Stakeholder | Their Concern | How We Address It |
|-------------|--------------|------------------|
| Revenue team | Does this increase GMV? | Impact model shows $8–12M/month additional GMV in base case |
| Trust & Safety | Does social proof feel manipulative? | All counts are real; copy reviewed pre-launch; guardrails on dispute rate |
| Engineering | WebSocket infrastructure cost? | Evaluate at scale; polling fallback included |
| Legal | Auto-bid terms of service? | Legal reviews T&C language before launch |
| Sellers | Does faster bidding mean lower final prices? | Auto-bid drives competition up; urgency increases bid depth |

---

## Risks

**Biggest risk:** Auto-bid logic error causes a user to be charged more than their stated max. This would be a critical trust and legal incident.
**Mitigation:** Auto-bid has an absolute hard cap at user's stated max (enforced server-side, not client-side). Extensive QA. Full audit log. Legal review of T&C.

**Second biggest risk:** Urgency signals increase bid dispute rate (users feel pressured into bids they regret).
**Mitigation:** Guardrail monitoring on dispute rate from Day 1. Rollback trigger if dispute rate increases > 0.5 points.
