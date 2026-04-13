# Product Requirements Document
## Bidding Experience Optimization — Auction Flow Redesign

**Product Area:** Buyer Engagement / Auction Flow  
**Status:** Draft  
**Author:** [Your Name]  
**Last Updated:** April 2026  
**Target Launch:** Q3 2026

---

## 1. Executive Summary

The current bidding experience is the highest-friction moment in our buyer journey. Users drop off due to a multi-step flow, unclear auction state, and lack of urgency signals. This results in suppressed bid volume, lower auction revenue per listing, and frustrated buyers who walk away.

This PRD defines the requirements to redesign the end-to-end bidding experience to be faster, clearer, and more engaging — increasing bid participation and auction-level revenue without degrading trust.

---

## 2. Problem Statement

### Current Bidding Flow (Pain Points)

**Step 1: Item Detail Page**
- Bid button buried below the fold on mobile
- Current price not always updated in real time (requires refresh)
- Auction end time displayed as absolute timestamp ("Ends: Apr 22 at 3:47 PM") rather than relative ("Ends in 2h 14m")

**Step 2: Bid Entry**
- Navigates user away from item page to a separate bid page (context loss)
- No suggested bid increments shown
- No indication of how many other bidders are active

**Step 3: Bid Confirmation**
- Confirmation modal is generic — no emotional acknowledgment
- Users don't know if they're the highest bidder after submitting
- No "set auto-bid" prompt post-bid

**Step 4: Post-Auction**
- Outbid notifications often arrive too late (minutes after being outbid)
- No one-click re-bid from notification

### Evidence

| Metric | Current Benchmark |
|--------|-----------------|
| Bid participation rate (views → bids) | 4.1% |
| Bid completion rate (bid started → submitted) | 68% |
| Avg. bids per active bidder per auction | 1.8 |
| Outbid → re-bid rate | 31% |
| Mobile bid completion rate | 54% (vs. 78% desktop) |

### User Research Findings
- 43% of users who abandon bidding cite "too many steps"
- 29% say they "didn't realize the auction was ending so soon"
- 38% of mobile users say the bid form is "frustrating to use on phone"
- 51% of outbid users say they would have re-bid if notified faster

---

## 3. Goals & Success Metrics

### Primary Goals
1. Increase bid participation rate (views → bids) from 4.1% → 5.0%
2. Increase bid completion rate from 68% → 82%
3. Increase avg. bids per bidder per auction from 1.8 → 2.4
4. Double outbid → re-bid rate from 31% → 55%

### KPI Framework

| Metric | Baseline | Target | Timeline |
|--------|----------|--------|----------|
| Bid participation rate | 4.1% | 5.0% | 90 days |
| Bid completion rate | 68% | 82% | 60 days |
| Avg. bids per bidder per auction | 1.8 | 2.4 | 90 days |
| Outbid re-bid rate | 31% | 55% | 60 days |
| Auction revenue per listing | Indexed at 100 | 115 | 120 days |
| Mobile bid completion rate | 54% | 72% | 90 days |

### Guardrail Metrics
- Bid dispute rate (must not increase — proxy for user confusion)
- Shill bid report rate (social proof messaging must not feel manipulative)
- Average bid amount (urgency must not cause panic underbidding)

---

## 4. Solution Overview

### 4.1 Simplified Bidding UI

**Principles:**
- Bid without leaving the item detail page (modal-based, not page navigation)
- Max 2 taps on mobile to place a bid
- Always-visible current price + time remaining in sticky header

**Redesigned Bid Flow:**

```
[Current State Display]  →  [Bid Input Modal]  →  [Instant Confirmation]
 - Current price              - Suggested amounts    - "You're the highest bidder!"
 - Time remaining             - Custom input         - Set auto-bid prompt  
 - Bid count                  - One-tap submit       - Back to item (1 click)
 - [Bid Now] CTA
```

**Bid Input Modal (new):**
- Appears as a bottom sheet on mobile, centered modal on desktop
- Shows current price + 3 suggested bid increments (min, mid, bold) as chips
- Single "Confirm Bid" button with item thumbnail for reassurance
- "Your max bid" auto-bid field below primary action

**Sticky Bid Bar (mobile):**
- Fixed at bottom of screen while scrolling item detail page
- Shows: Current price | Time remaining | [Bid Now] button
- Updates in real time via WebSocket

---

### 4.2 Real-Time Bid Updates

**What changes:**
- Current price updates without page refresh using WebSocket connection
- Bid count ("X bids") increments in real time
- When user is outbid, a non-intrusive toast notification appears on-page
- Auction end time counts down live ("Ends in 47:23" vs. "Ends at 3:14 PM")

**Technical approach:**
- WebSocket connection established on item detail page load
- Events: `bid_placed`, `auction_ending_soon` (10-min warning), `auction_ended`
- Graceful fallback to polling (30s interval) if WebSocket fails

---

### 4.3 Urgency Triggers

**Countdown Timer:**
- Displayed prominently near bid CTA
- Color shifts: green (> 24h) → amber (< 2h) → red (< 15 min)
- In final 60 seconds: pulsing animation + large font

**Bidder Activity Indicator:**
- Show "X people watching this item" (uses view count, not bidder count — higher number, more honest)
- Show "X bids placed" on item
- Show "Last bid placed N minutes ago"

**Design Guardrails:**
- Activity counts must be real (no inflation)
- "X people watching" cannot say more than actual watchers
- Social proof copy reviewed by Trust & Safety before launch
- No fake urgency ("Only 1 left!" if inventory isn't actually limited)

---

### 4.4 Auto-Bid (Proxy Bidding) Feature

**What it is:**
- User sets a maximum bid they're willing to pay
- System automatically bids on their behalf in minimum increments
- System never reveals the user's max bid to other bidders
- User is notified if outbid beyond their max

**UX Flow:**
1. User opens bid modal
2. Below "Place Bid" action: "Set your max bid (auto-bid)" toggle
3. Toggled ON: single input for max amount, replaces per-bid input
4. Confirmation: "We'll bid up to $X on your behalf. You'll be notified if outbid."
5. Active auto-bid shown with badge on watchlist + item page header

**Auto-bid Nudge:**
- After user's first manual bid, modal shows: "Want us to handle re-bids automatically? Set your max bid →"
- Shown once per session, not repeatedly

**Proxy Bidding Logic:**
```
if (competitor_bid < user_max_bid):
    place_bid(current_price + min_increment)
    notify_user("You're still the highest bidder")
else:
    notify_user("You've been outbid — your max was $X")
    prompt_user("Would you like to increase your max bid?")
```

---

## 5. Current vs. Proposed Flow

See `current-vs-proposed-flow.md` for detailed side-by-side comparison.

---

## 6. User Stories & Acceptance Criteria

### Epic 1: Streamlined Bid Flow

**US-001:** As a mobile buyer, I want to place a bid in under 3 taps so that I don't lose the auction due to friction.

*Acceptance Criteria:*
- [ ] Bid CTA visible without scrolling on mobile item detail page
- [ ] Bid modal appears as bottom sheet (no page navigation)
- [ ] 3 pre-suggested bid amounts shown as tappable chips
- [ ] "Confirm Bid" is the single primary action in modal
- [ ] End-to-end bid placement completes in ≤ 3 taps on mobile

**US-002:** As a buyer watching an item, I want to see the current price update in real time so I know the auction state without refreshing.

*Acceptance Criteria:*
- [ ] Current price updates within 3 seconds of a new bid being placed
- [ ] Bid count updates in real time
- [ ] Page does not reload or flicker on price update
- [ ] Fallback polling (30s) activates if WebSocket connection drops

---

### Epic 2: Urgency & Social Proof

**US-003:** As a buyer considering a bid, I want to see how much time is left in the auction so I can make a timely decision.

*Acceptance Criteria:*
- [ ] Countdown timer shows days/hours/minutes based on time remaining
- [ ] Timer color shifts amber at < 2h, red at < 15min
- [ ] Timer visible in sticky bid bar on mobile

**US-004:** As a buyer, I want to see bidding activity on the item so I understand demand without feeling manipulated.

*Acceptance Criteria:*
- [ ] "X people watching" uses real watcher count only
- [ ] "X bids placed" reflects actual bid count
- [ ] No copy that implies false scarcity
- [ ] Trust & Safety sign-off on all social proof strings

---

### Epic 3: Auto-Bid

**US-005:** As a frequent bidder, I want to set a maximum bid and let the system bid on my behalf so I don't miss auctions when I'm not actively watching.

*Acceptance Criteria:*
- [ ] Auto-bid toggle available in bid modal
- [ ] Max bid field accepts amounts > current price + 1 increment
- [ ] System places bids automatically in minimum increment steps
- [ ] User notified within 60 seconds of being outbid beyond max
- [ ] Auto-bid max is never revealed to other users or publicly
- [ ] User can increase max bid at any time from watchlist or item page

**US-006:** As a first-time bidder, I want to be prompted to set up auto-bid after my first manual bid so I don't have to babysit the auction.

*Acceptance Criteria:*
- [ ] Auto-bid nudge appears after first manual bid in a session
- [ ] Nudge is dismissible ("No thanks, I'll bid manually")
- [ ] Nudge shown maximum once per session per auction

---

## 7. Out of Scope (v1)

- Live video auction experience
- Bidding via SMS/push notification (v2)
- "Snipe bid" scheduled bidding (backlog — evaluate demand)
- Seller reserve price transparency (separate initiative)

---

## 8. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Auto-bid logic bugs (user overpays) | Low | Critical | Extensive QA; hard cap at user's stated max; audit log |
| Social proof feels manipulative | Medium | High | Trust & Safety review; conservative copy ("X watching" not "X competing") |
| WebSocket infrastructure cost | Medium | Medium | Use existing infra if possible; evaluate cost at scale |
| Mobile bottom sheet conflicts with OS gestures | Medium | Low | OS-specific testing; fallback to modal |
| Users confused by auto-bid → dispute rate increase | Medium | Medium | Clear confirmation copy; email confirmation of max bid set |

---

## 9. Phased Rollout

| Phase | Scope | Timeline |
|-------|-------|----------|
| Alpha | Internal QA + 1% of logged-in bidders | Week 1–2 |
| Beta | 10% ramp, mobile + desktop | Week 3–5 |
| A/B Test | 50/50 split: old vs. new flow | Week 6–10 |
| GA | 100% rollout if tests pass | Week 11+ |

---

## 10. Dependencies

- Engineering: WebSocket infrastructure, proxy bidding backend logic
- Design: Mobile bottom sheet component library
- Trust & Safety: Social proof copy review + shill bid monitoring update
- Legal: Auto-bid terms of service language
- Notifications: Outbid push/email pipeline
