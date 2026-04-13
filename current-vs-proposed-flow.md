# Current vs. Proposed Bidding Flow
## Auction Flow Redesign

---

## Side-by-Side Flow Comparison

### CURRENT FLOW

```
Step 1: Item Detail Page
┌─────────────────────────────────────┐
│  [Item images — full scroll]        │
│  Item title                         │
│  Item description (long)            │
│  Seller info                        │
│  ↕ scroll required                  │
│  ─────────────────────────────────  │
│  Current bid: $2,400                │
│  Ends: April 22 at 3:47 PM EST      │  ← Static timestamp
│  [Place a Bid]  ← below the fold    │  ← No mobile sticky
└─────────────────────────────────────┘
                    ↓
         User navigates to NEW PAGE  ← Context loss

Step 2: Bid Entry Page (Separate Page)
┌─────────────────────────────────────┐
│  ← Back to item                     │
│  Place your bid                     │
│  Current bid: $2,400                │
│  Minimum bid: $2,500                │
│                                     │
│  Your bid: [___________]            │  ← Text input only
│                                     │
│  [Continue]                         │
└─────────────────────────────────────┘
                    ↓

Step 3: Confirmation Page (Third Page)
┌─────────────────────────────────────┐
│  Review your bid                    │
│  Bid amount: $2,500                 │
│  Item: [Name]                       │
│                                     │
│  [Confirm Bid]  [Cancel]            │
└─────────────────────────────────────┘
                    ↓

Step 4: Back to Item (Or Redirect)
┌─────────────────────────────────────┐
│  Bid placed.                        │  ← Generic toast
│  [Item page reloads]                │  ← Requires manual refresh
└─────────────────────────────────────┘
```

**Total taps on mobile: 6–8**  
**Pages navigated: 3**  
**Time to complete: ~45–90 seconds**  
**Mobile completion rate: 54%**

---

### PROPOSED FLOW

```
Step 1: Item Detail Page (Redesigned)
┌─────────────────────────────────────┐
│  [Item images]                      │
│  Item title                         │
│  Item description                   │
│                                     │
│  ═══════════════════════════════    │  ← Sticky top bar
│  Current bid: $2,400 ↑ LIVE        │  ← Real-time WebSocket
│  23 bids · 47 watching              │
│  ⏱ Ends in 2h 14m  ████░ [amber]   │  ← Live countdown
│  ═══════════════════════════════    │
│                                     │
│  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─   │
│  [PLACE BID]  ← Sticky bottom bar  │  ← Always visible mobile
└─────────────────────────────────────┘
                    ↓
     Bottom sheet slides up (NO page navigation)

Step 2: Bid Modal (Bottom Sheet on Mobile)
┌─────────────────────────────────────┐
│  ≡ (drag handle)                    │
│  [Item thumbnail]  Vintage Rolex    │
│                    Current: $2,400  │
│                                     │
│  Quick bids:                        │
│  [$2,500]  [$2,600]  [$2,750]       │  ← Suggested chips
│                                     │
│  Or enter amount: [$______]         │
│                                     │
│  ─────────────────────────────────  │
│  Set your max bid (auto-bid) ○      │  ← Optional toggle
│  ─────────────────────────────────  │
│                                     │
│  [Confirm Bid: $2,500]              │  ← Single primary CTA
└─────────────────────────────────────┘
                    ↓
            Instant in-modal response

Step 3: Confirmation (Same Modal, Animated State)
┌─────────────────────────────────────┐
│  ✓  You're the highest bidder!      │  ← Emotional confirmation
│     $2,500 on Vintage Rolex GMT     │
│                                     │
│  We'll notify you if outbid.        │
│                                     │
│  Want us to auto-bid up to $___ ?   │  ← Auto-bid nudge (1x)
│  [Set Max Bid]  [No thanks]         │
│                                     │
│  [Back to Item]                     │
└─────────────────────────────────────┘
                    ↓

Step 4: Item Page (Unchanged, Live State)
┌─────────────────────────────────────┐
│  Current bid: $2,500 (YOU) ✓        │  ← Instant update, no refresh
│  ⏱ Ends in 2h 13m                  │
│  [Increase Bid]                     │
└─────────────────────────────────────┘
```

**Total taps on mobile: 3**  
**Pages navigated: 0 (modal only)**  
**Time to complete: ~15–20 seconds**  
**Mobile completion rate target: 72%**

---

## Drop-off Analysis

### Current Funnel
```
View Item Detail Page         → 100%
Scroll to find Bid button     →  74%  (-26% never find button)
Click "Place a Bid"           →  52%  (-22% bounce from page)
Complete Bid Entry form       →  38%  (-14% abandon on separate page)
Confirm bid                   →  28%  (-10% abandon on confirm page)
Bid successfully placed       →  28%
```
**Overall conversion: 28%** (of users who view item and click bid)

### Proposed Funnel (Projected)
```
View Item Detail Page         → 100%
See sticky [Bid Now] bar      → 100%  (always visible)
Tap "Place Bid"               →  68%  (improved discoverability)
Select amount + confirm       →  59%  (1 step vs. 2)
Bid successfully placed       →  59%
```
**Projected conversion: 59%** (+111% relative improvement)  
*Note: These are directional projections — actual results measured via A/B test*

---

## Key UX Changes Summary

| Element | Current | Proposed | Why |
|---------|---------|---------|-----|
| Bid CTA location | Below fold | Sticky bottom bar (mobile) | Always accessible |
| Bid entry | Separate page | Bottom sheet modal | No context loss |
| Suggested amounts | None | 3 tappable chips | Reduces cognitive load |
| Price updates | Manual refresh | Real-time WebSocket | Auction state clarity |
| Time display | Absolute timestamp | Live countdown | Urgency awareness |
| Bid confirmation | Generic "Bid placed" | "You're the highest bidder!" | Emotional engagement |
| Auto-bid | Separate flow | Integrated nudge in modal | Natural discovery |
| Outbid notification | Delayed (minutes) | Near real-time (< 60s) | Re-bid opportunity |

---

## Mobile vs. Desktop Considerations

### Mobile (priority platform for bidding)
- Bottom sheet is native-feeling (matches iOS/Android patterns)
- Sticky bid bar stays fixed above browser chrome
- Countdown timer larger font on mobile (48px vs. 32px desktop)
- Suggested bid chips are 44px tall minimum (WCAG touch target)

### Desktop
- Bid modal appears centered
- Countdown timer shown in sidebar
- Social proof ("X watching") more prominent in sidebar
- More Like This shelf visible alongside bid UI without scroll

---

## Error States & Edge Cases

| Scenario | Current Behavior | Proposed Behavior |
|---------|-----------------|------------------|
| User bid too low (< minimum) | Error on separate page | Inline error in modal, auto-fill minimum |
| Auction ends while modal open | User submits, gets error page | Modal updates live ("Auction ended — you were [X]") |
| Network error during bid | Generic error page | In-modal error with retry button |
| User already highest bidder | Unclear state | Modal shows "You're already leading — increase bid?" |
| Auto-bid max exceeded | Email notification only | Push + in-app + email, one-tap re-bid |
