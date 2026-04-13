# Product Requirements Document
## Consignment Funnel Optimization — Seller Experience

**Product Area:** Seller Experience / Supply Growth  
**Status:** Draft  
**Author:** Rahul Reddy Puchakayala 
**Last Updated:** April 2026  
**Target Launch:** Q3 2026

---

## 1. Executive Summary

The consignment (seller submission) funnel is our primary supply acquisition channel. Today, only ~34% of sellers who start the submission process complete it. This means we're losing 2 out of 3 potential sellers at the top of the funnel — suppressing inventory supply and directly impacting buyer experience and revenue.

This PRD defines the requirements to redesign the consignment funnel to increase submission completion rates, reduce time-to-submit, and improve seller confidence through AI assistance and better price transparency.

---

## 2. Problem Statement

### The Consignment Process Today

Sellers who want to list items for auction must:
1. Create an account
2. Fill out an item submission form (category, title, description, condition, images, provenance)
3. Wait 2–5 business days for authentication review
4. Agree to commission terms
5. Item goes live for auction

### Current Funnel Metrics

| Funnel Stage | Completion Rate | Drop-off |
|-------------|----------------|---------|
| Start submission | 100% | — |
| Complete basic info (cat, title) | 78% | -22% |
| Upload images | 61% | -17% |
| Write description | 44% | -17% |
| Submit for review | 34% | -10% |
| Approved & listed | 26% | -8% (auth rejection) |

**Overall completion: 34% (start → submit)**  
**Overall listing rate: 26% (start → live auction)**

### Root Causes (from seller exit surveys)

- **"Too long / too complicated"** — 41% of dropouts
- **"I didn't know what to write in the description"** — 29%
- **"I wasn't sure if my price expectation was realistic"** — 24%
- **"I started and couldn't finish, then forgot to come back"** — 19%
- **"The image upload didn't work well on my phone"** — 16%

### Business Impact

- Lost potential GMV from abandoned submissions: estimated $8–15M/month
- Low supply in certain categories drives buyers to competitors
- Authentication cost is wasted on abandoned submissions that are never completed after initial review

---

## 3. Goals & Success Metrics

### Primary Goals
1. Increase submission start → completion rate from 34% → 55%
2. Reduce avg. time to submit from 24 minutes → 12 minutes
3. Increase seller retention (sellers who submit a second item) from 28% → 42%
4. Increase listings per active seller from 1.4 → 2.1

### KPI Framework

| Metric | Baseline | Target | Timeline |
|--------|----------|--------|----------|
| Submission completion rate | 34% | 55% | 90 days |
| Time to submit (avg.) | 24 min | 12 min | 60 days |
| Image upload completion (mobile) | 61% | 80% | 60 days |
| AI description adoption rate | N/A | > 60% | 60 days post-launch |
| Seller 30-day retention | 28% | 42% | 120 days |
| Listings per seller per quarter | 1.4 | 2.1 | 120 days |
| Authentication rejection rate | 8% | ≤7% | 90 days |

### Guardrail Metrics
- Authentication rejection rate (must not increase — AI descriptions must not mislead)
- Listing quality score (buyer satisfaction with listing accuracy)
- Fraud submission rate (must not increase with easier submission)

---

## 4. Solution Overview

### 4.1 Step-by-Step Guided Submission Flow

**What changes:**

Instead of a single long form, the submission flow becomes a progressive, multi-step wizard with:
- Clear progress indicator ("Step 3 of 6")
- One primary action per step
- Save & continue later capability at every step
- Mobile-first design throughout

**New Step Structure:**

```
Step 1: What are you selling?  (Category selection — visual grid)
Step 2: Tell us about it       (Basic details: title, era, brand)
Step 3: Condition              (Guided condition assessment with examples)
Step 4: Photos                 (Simplified upload with guide overlay)
Step 5: Description            (AI-assisted — see 4.2)
Step 6: Pricing & Terms        (Price estimate + commission preview)
```

**Key UX principles:**
- No step requires more than 3 inputs
- Photo upload uses native camera on mobile (not file picker)
- Progress is saved automatically every 30 seconds
- "Continue later" button prominent on every step — sends resume email
- Each step shows an estimated time ("~2 minutes")

---

### 4.2 AI-Assisted Item Description Generator

**The problem:** Writing a compelling, accurate description is the highest drop-off step in the current funnel. Most sellers aren't professional copywriters and don't know what details matter to collectors.

**How it works:**

1. After completing Steps 1–4 (category, details, condition, photos), the AI generates a draft description
2. Draft is based on: category + inputs + photo analysis + comparable sold listings
3. Seller sees the draft pre-populated in the description field
4. Seller can: accept as-is, edit inline, or regenerate with different emphasis

**AI generation inputs:**
- Category + subcategory
- Brand/maker, model, reference number (if applicable)
- Era/decade
- Condition grade + condition notes
- Photos (analyzed for visible details, markings, damage)
- Seller's own notes (optional free-text field on Step 4)

**Example output:**

*Seller inputs:* 1967 Rolex Submariner 5513, condition "very good," "original bracelet present, some surface scratches"

*AI-generated description:*
> "A handsome 1967 Rolex Submariner reference 5513, presented in very good overall condition. The matte black dial shows excellent aging consistent with its vintage, with all markers intact and legible. The case retains good proportions with light surface wear commensurate with age. Original Oyster bracelet present, with matching taper to the case. A solid example of one of the most sought-after vintage dive watches, ideal for the collector seeking an honest, unmolested original."

**Quality guardrails:**
- AI must not claim condition facts not provided by seller (no hallucination of "mint" if seller said "good")
- Human review step confirms AI description matches photos before listing goes live
- Disclaimer shown to seller: "Review this description carefully — you're responsible for its accuracy"

---

### 4.3 Price Estimation Tool

**The problem:** 24% of sellers abandon because they're uncertain whether their price expectations are realistic. Many either overprice (items sit unsold) or underprice (seller dissatisfaction post-sale).

**How it works:**

Shown on Step 6 (Pricing & Terms), before seller inputs their reserve:

1. System shows "Estimated value range: $X,XXX – $X,XXX" based on:
   - Comparable sold auction results (same category + era + condition)
   - Current demand signals (active watchers in category, recent search volume)
   - Condition adjustment (graded vs. ungraded, original vs. restored)

2. Seller sees a price distribution chart:
   - "Items like yours have sold for..." with bell curve
   - "Setting your reserve here gives you ~X% chance of sale"

3. Seller inputs their desired reserve price
4. System shows dynamic probability: "At $3,500 reserve, 78% of similar items sold at auction"

**Data requirements:**
- Minimum 10 comparable sold results in past 24 months for estimate
- If insufficient data, show: "We don't have enough data for a reliable estimate, but our specialists will review before listing"

**Design principle:** Show ranges, not false precision. "~$3,000 – $5,000" is more trustworthy than "$4,127"

---

### 4.4 Progress Tracker & Save Draft Feature

**Save Draft:**
- Submission state automatically saved to server every 30 seconds
- "Save & finish later" always available
- Incomplete submissions accessible from seller dashboard
- Automated recovery email sent after 24h if submission not completed:
  *"Your [item category] submission is waiting — you're halfway there. Pick up where you left off →"*

**Progress Indicator:**
- Visual stepper at top of screen: Step 1 ○ — Step 2 ○ — Step 3 ● (current) — Step 4 ○ — Step 5 ○ — Step 6 ○
- Estimated time remaining shown: "About 8 minutes left"
- Completed steps show checkmark (reinforces progress)

**Mobile Image Upload Improvements:**
- Native camera integration (no file picker friction)
- In-app photo guide overlay: "Position item in frame · Good lighting · 5 photos minimum"
- Auto-retry on upload failure with progress indicator
- Accepts HEIC format (iOS native) — converts server-side

---

## 5. User Journey Map

See `user-journey-map.md` for full journey documentation including emotions at each stage.

---

## 6. User Stories & Acceptance Criteria

### Epic 1: Guided Submission Flow

**US-001:** As a first-time seller, I want a guided step-by-step process so I don't feel overwhelmed by a long form.

*Acceptance Criteria:*
- [ ] Submission split into ≤ 6 distinct steps
- [ ] Each step has a clear title and estimated time
- [ ] Progress bar/stepper visible on every step
- [ ] Back navigation available without losing entered data
- [ ] Entire flow completable on mobile without desktop required

**US-002:** As a seller interrupted mid-submission, I want to save my progress and continue later so I don't lose my work.

*Acceptance Criteria:*
- [ ] Progress auto-saves every 30 seconds
- [ ] "Save & continue later" button on every step
- [ ] Incomplete submissions visible in seller dashboard
- [ ] Recovery email sent after 24h of inactivity (with deep link to resume)
- [ ] Resuming restores exact step and all previously entered data

---

### Epic 2: AI Description Generator

**US-003:** As a seller, I want an AI-generated description draft so I don't have to write from scratch.

*Acceptance Criteria:*
- [ ] AI draft generated after steps 1–4 are complete
- [ ] Draft appears pre-filled in description field
- [ ] Seller can accept, edit, or regenerate
- [ ] AI draft does not include condition claims beyond seller's stated input
- [ ] Generation completes in < 5 seconds
- [ ] Disclaimer shown: seller is responsible for accuracy

**US-004:** As a seller reviewing an AI draft, I want to edit it inline so I can personalize without starting over.

*Acceptance Criteria:*
- [ ] Description field is editable rich text
- [ ] "Regenerate" option available (generates new variation)
- [ ] Character count shown (recommended 150–400 words)
- [ ] Preview shows how description will appear to buyers

---

### Epic 3: Price Estimation

**US-005:** As a seller, I want to see comparable sale prices before setting my reserve so I can price confidently.

*Acceptance Criteria:*
- [ ] Price estimate shown before reserve input
- [ ] Estimate shows a range (not a single number)
- [ ] At least 5 comparable sales shown with sale price + date
- [ ] If insufficient data (< 10 comps), honest "not enough data" message shown
- [ ] Reserve probability displayed after user inputs price ("78% of similar items sold at this price")

---

## 7. Out of Scope (v1)

- Seller authentication portal (separate initiative)
- Multi-item bulk submission (v2)
- Consignment tracking post-submission (v2)
- Seller commission negotiation (separate policy decision)

---

## 8. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| AI description contains inaccuracies | Medium | High | Human review before listing; seller accountability disclaimer |
| Price tool creates anchoring bias (sellers reject fair offers) | Medium | Medium | Show range, not point estimate; use "likely range" language |
| Save draft creates submission "debt" that clutters operations | Low | Medium | Auto-expire drafts after 90 days with seller email warning |
| Easier submission → more fraud attempts | Medium | High | Keep existing authentication step; add photo-matching fraud check |
| AI description adoption < 30% | Low | Low | Default to pre-populated (opt-out, not opt-in) |

---

## 9. Phased Rollout

| Phase | Scope | Timeline |
|-------|-------|----------|
| Alpha | Internal + invited power sellers (n=50) | Week 1–3 |
| Beta | 10% new seller cohort | Week 4–7 |
| A/B Test | 50/50 new vs. returning sellers | Week 8–12 |
| GA | Full rollout | Week 13+ |

---

## 10. Dependencies

- ML/AI: Description generation model fine-tuned on collectibles listings
- Data: Historical auction results pipeline for price estimation
- Mobile: Native camera integration for iOS/Android
- Email: Transactional email for draft recovery
- Authentication team: Review impact of new submission format on auth workflow
