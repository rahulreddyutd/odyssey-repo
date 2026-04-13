# User Journey Map
## Consignment Funnel Optimization — Seller Experience

---

## Journey Overview

This map documents the end-to-end experience of a seller submitting an item for consignment auction — from the moment they consider selling through to their item going live.

**Primary Persona:** First-time seller, Marcus D., 48, watches collector who wants to liquidate part of his collection  
**Scenario:** Marcus wants to consign a vintage Heuer chronograph he's decided to sell

---

## Journey Map

### Phase 1: Awareness & Consideration

**What Marcus does:**
- Googles "sell vintage watch auction"
- Lands on our platform's "Sell with Us" marketing page
- Reads commission structure, authentication info, "how it works"
- Creates an account

**Touchpoints:**
- SEO / paid search
- Sell landing page
- Account creation form

**Emotions:** 🤔 Curious → 😐 Cautious ("Is this legit? What's the catch?")

**Pain points (current):**
- Commission is not clearly stated on marketing page — discovered late
- Account creation requires email verification before starting submission (adds a step)

**Opportunities:**
- Surface commission % and estimated payout prominently on marketing page
- Allow "start submission" before email verification to reduce early friction

---

### Phase 2: Starting the Submission

**What Marcus does:**
- Clicks "Submit an Item" from dashboard
- Sees the current: a single long form
- Fills in category ("Watches")
- Attempts to fill in subcategory — confused by taxonomy ("Chronograph" vs. "Vintage Swiss")

**Touchpoints:**
- Seller dashboard
- Submission form — Step 1

**Emotions:** 😐 Cautious → 😕 Confused ("What category does my watch belong in?")

**Pain points (current):**
- Long form is intimidating — no sense of how long it will take
- Category taxonomy requires 3 dropdown clicks and domain knowledge
- No estimated time shown

**Future state (proposed):**
- Visual category grid with photos ("Click the type that matches your item")
- "Step 1 of 6 · About 2 minutes" progress indicator
- Suggested subcategory after primary category selected

**Emotion in future state:** 😊 Engaged ("This feels manageable")

---

### Phase 3: Item Details

**What Marcus does:**
- Fills in make, model, reference number ("Heuer 2447")
- Selects decade ("1970s")
- Inputs condition — currently a text field ("Good condition")

**Touchpoints:**
- Submission form — Step 2 (current) / Steps 1–3 (proposed)

**Emotions:** 😐 Neutral → 😕 Uncertain ("Am I describing condition correctly? What does 'good' mean to them?")

**Pain points (current):**
- Condition is a free-text field — vague, anxiety-inducing
- No examples of what "good vs. very good vs. excellent" looks like for watches

**Future state:**
- Condition assessment: guided quiz with photo examples
  - "Does your item have any scratches on the case?" (Y/N + photo example)
  - "Is the dial original and unrestored?" (Y/N)
- Condition grade auto-populated based on answers
- "Your item grades as: Very Good (VG)" — transparent and educational

**Emotion in future state:** 😊 Confident ("I know exactly what I'm telling them")

---

### Phase 4: Photo Upload

**What Marcus does:**
- Clicks "Upload Photos"
- On mobile: file picker opens — navigates through Camera Roll
- Selects 4 photos
- Third photo fails to upload (large HEIC file) — no clear error message
- Tries again, frustrated
- Eventually uploads 4 of 5 required photos
- Doesn't know which angles are needed — uploads random shots

**Touchpoints:**
- Submission form — photo step
- Mobile OS file picker

**Emotions:** 😤 Frustrated → 😩 Demoralized ("This is too hard, maybe I'll come back later")

**This is a major abandonment risk moment.**

**Pain points (current):**
- File picker doesn't invoke camera directly on mobile
- HEIC format fails silently
- No photo angle guide or checklist
- Upload progress not shown
- No minimum/maximum photo guidance until submission fails

**Future state:**
- Button says "Take Photos" (opens camera directly on mobile)
- Photo guide overlay: "Dial · Case front · Case back · Crown · Bracelet/strap"
- Progress bar per photo upload
- Automatic HEIC → JPEG conversion server-side
- Retry with visual feedback ("Photo 3 failed — tap to retry")
- Checkmarks as each required angle is captured

**Emotion in future state:** 😊 Guided → 😌 Accomplished ("I got all the right shots")

---

### Phase 5: Description

**What Marcus does:**
- Arrives at blank text box: "Describe your item"
- Stares at it
- Types a few words, deletes them
- Checks competitor listings for inspiration
- Writes 3 sentences, worries it's not enough
- Gets distracted, closes tab ("I'll finish this later")

**Touchpoints:**
- Submission form — description step
- Competitor research (off-platform)

**Emotions:** 😰 Anxious → 😩 Defeated ("I don't know what to write")

**This is the highest drop-off step.**

**Pain points (current):**
- Blank canvas with no guidance
- No examples of good descriptions
- Fear of misrepresenting the item
- No word count guidance

**Future state:**
- AI generates draft description based on Steps 1–4
- Description field pre-populated: "Here's a draft based on what you've told us — feel free to edit"
- Draft is specific, professional, and factually accurate to inputs
- "Regenerate" button for variation
- Word count: "142 / recommended 150–400 words"
- "Tip: Add any known history or provenance to help buyers"

**Emotion in future state:** 😲 Surprised ("It already wrote something for me!") → 😊 Confident ("This is better than what I would have written")

---

### Phase 6: Pricing & Terms

**What Marcus does:**
- Arrives at reserve price input
- No guidance on what to enter
- Guesses: "$4,000" (which is 40% above market rate for his reference)
- Reviews commission structure for first time (was in fine print on marketing page)
- Feels uncertain — submits anyway

**Touchpoints:**
- Pricing step
- Commission terms page

**Emotions:** 😕 Uncertain → 😟 Anxious ("Am I asking for the right price? Will it sell?")

**Pain points (current):**
- No price guidance before reserve input
- Commission revealed as surprise (not front-loaded)
- No indication of sale probability at chosen price

**Future state:**
- Price estimation shown first: "Comparable Heuer 2447s have sold for $2,800–$3,600 in the past 12 months"
- Bell curve visualization with comparable sales
- Reserve input shows dynamic probability: "At $3,200 reserve, 74% of similar items sold"
- Commission shown as: "At this price, your estimated payout is $2,688 (after 16% commission)"
- "Confirm & Submit" — clear final action

**Emotion in future state:** 😊 Informed → 😌 Confident ("I know what I'm setting and why")

---

### Phase 7: Post-Submission

**What Marcus does (current):**
- Receives generic confirmation email
- Waits 3–5 business days for authentication review
- No status updates during wait
- Uncertainty: "Is anything happening?"

**Future state:**
- Confirmation page: timeline shown ("What happens next: authentication in 2–4 days")
- Email day 1: "Your item is in queue"
- Email day 2 (if watch): "Our watch specialist is reviewing your Heuer"
- Authentication complete: "Your item has been approved and goes live in 24 hours"
- Seller dashboard shows item status: Submitted → Under Review → Approved → Live

**Emotion in future state:** 😊 Excited → 😌 Trusting ("I know what's happening")

---

## Journey Summary: Emotional Arc

```
Awareness  Consideration  Submission  Photos   Description  Pricing  Post-submit
    
😊 Curious → 😐 Cautious → 😊 Engaged → 😩 Frustrated → 😩 Defeated → 😟 Anxious → 😐 Uncertain
                                                                    [CURRENT — many drop off here]

😊 Curious → 😊 Informed → 😊 Guided → 😊 Guided → 😲 Surprised → 😊 Confident → 😌 Trusting
                                                                    [FUTURE STATE]
```

---

## Opportunity Summary by Phase

| Phase | Current Emotion | Future Emotion | Key Feature |
|-------|----------------|----------------|-------------|
| Starting | Confused | Engaged | Guided step flow |
| Item Details | Uncertain | Confident | Condition guide |
| Photo Upload | Frustrated | Guided | Native camera + guide overlay |
| Description | Defeated | Surprised/Confident | AI description generator |
| Pricing | Anxious | Informed | Price estimation tool |
| Post-submit | Uncertain | Trusting | Status updates + timeline |
