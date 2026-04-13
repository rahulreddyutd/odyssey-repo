# Funnel Analysis
## Consignment Funnel Optimization

---

## Current Funnel Performance

### Top-Level Metrics
- **Monthly submission starts:** ~12,400 seller sessions
- **Monthly submissions completed:** ~4,200 (34% completion)
- **Monthly items listed:** ~3,200 (26% of starts, ~76% auth approval rate)
- **Estimated monthly GMV lost to abandonment:** $8–15M

---

## Stage-by-Stage Drop-off Analysis

### Stage 1: Account Creation → Submission Start
```
Sellers who create account:        100%
Sellers who start a submission:     71%
Drop-off:                          -29%
```

**Root causes:**
- Sellers create account out of curiosity, not commit-ready
- No email nurture sequence to bring back fence-sitters
- "How it works" page not prominent enough before account creation

**Opportunity:** Email drip to newly registered sellers who haven't started submission

---

### Stage 2: Submission Start → Basic Info Complete
```
Submission starts:                 100%
Complete category + basic info:     78%
Drop-off:                          -22%
```

**Root causes:**
- Category selection requires too many clicks (3-level taxonomy)
- "What to call it" (title) causes friction — sellers unsure of correct terminology
- No autocomplete or suggested titles based on category

**Opportunity:** Visual category grid (1 click) + suggested title templates

---

### Stage 3: Basic Info → Image Upload Attempted
```
Basic info complete:               100%
Begin image upload:                 84%
Images successfully uploaded:       61%
Net drop-off (basic info → images complete): -39%
```

**Root causes:**
- Mobile upload via file picker is awkward (navigating file system)
- Upload failures (large HEIC files, slow connections) with no retry UI
- Sellers don't know how many photos or what angles are needed
- No progress indicator during upload

**Opportunity:** Native camera, upload guide overlay, auto-retry, progress bar

---

### Stage 4: Images → Description Complete
```
Images uploaded:                   100%
Description started:                71%
Description completed (≥50 words):  44%
Net drop-off:                      -56%
```

**This is the biggest drop-off in the funnel.**

**Root causes:**
- Blank text box — sellers don't know what to write
- Fear of writing the "wrong" thing (condition misrepresentation anxiety)
- Perceived high-stakes: "If I describe it wrong, buyers will be upset"
- No examples or templates provided

**Opportunity:** AI-generated draft — pre-fill the field, reduce blank-page anxiety

---

### Stage 5: Description → Final Submission
```
Description complete:              100%
Pricing page reached:               89%
Submission submitted:               76%
Net drop-off from description done: -24%
```

**Root causes:**
- Reserve price anxiety — sellers unsure what to ask
- Commission rate displayed as surprise on final page (not surfaced earlier)
- Mobile keyboard covers price input field (UI bug)

**Opportunity:** Price estimation tool; surface commission upfront; fix mobile keyboard overlap

---

## Overall Funnel Visualization

```
 Account Created
        │
        ▼
 Submission Start ─────────────────── 100%
        │
        │ -22% (category/title friction)
        ▼
 Basic Info Complete ──────────────── 78%
        │
        │ -17% (image upload friction)
        ▼
 Images Uploaded ──────────────────── 61%
        │
        │ -17% (description blank-page problem)
        ▼
 Description Complete ─────────────── 44%
        │
        │ -10% (price anxiety)
        ▼
 Submitted for Review ─────────────── 34%
        │
        │ -8% (authentication rejection)
        ▼
 Listed & Live ────────────────────── 26%
```

---

## Segment Analysis

### By Device

| Stage | Desktop Completion | Mobile Completion | Gap |
|-------|-------------------|------------------|-----|
| Basic info | 84% | 71% | -13% |
| Image upload | 74% | 51% | -23% |
| Description | 52% | 35% | -17% |
| Final submission | 79% | 69% | -10% |
| **Overall** | **41%** | **24%** | **-17%** |

**Mobile is significantly underperforming.** The image upload step and description step are the mobile-specific pain points.

---

### By Seller Type

| Seller Type | Completion Rate | Avg. Submission Time | Avg. Items/Quarter |
|-------------|----------------|---------------------|-------------------|
| First-time sellers | 22% | 38 min | 1.0 |
| 2–5 prior submissions | 41% | 18 min | 1.8 |
| Power sellers (6+) | 67% | 9 min | 4.2 |

**First-time sellers have the highest drop-off and the highest potential for improvement.** Reducing their friction from 38 min → 15 min could unlock significant volume.

---

### By Category

| Category | Completion Rate | Avg. Time | Primary Drop-off Stage |
|----------|----------------|-----------|----------------------|
| Sports Cards | 42% | 16 min | Description (cards have standardized descriptions — AI should excel here) |
| Watches | 38% | 28 min | Images (angle requirements strict) |
| Art & Prints | 27% | 35 min | Description (condition nuances complex) |
| Furniture | 31% | 31 min | Images (size, bulk, multiple angles) |
| Jewelry | 35% | 22 min | Basic info (material, stone specs confusing) |

**Watches and Art have category-specific complexity** that the AI description generator must handle well.

---

## Exit Survey Analysis

**Sample:** 840 sellers who abandoned submission (surveyed at 48h post-abandonment)

| Reason for abandonment | % selecting | Primary stage |
|------------------------|------------|--------------|
| "Too long / too many steps" | 41% | All stages |
| "Didn't know what to write in description" | 29% | Description step |
| "Unsure if my price expectation is realistic" | 24% | Pricing step |
| "Started and got interrupted, forgot to come back" | 19% | All (no save) |
| "Image upload didn't work on my phone" | 16% | Image step |
| "Wasn't sure my item qualified" | 12% | Very early |
| "Commission too high" | 9% | Pricing step |

**Key insight:** 3 of the top 5 reasons are directly addressable by our proposed features (AI description, price tool, save draft). The "too long" complaint is addressed by the guided step-by-step redesign.

---

## Projected Funnel Post-Optimization

Based on comparable marketplace case studies and our feature scope:

| Stage | Current | Projected | Improvement Driver |
|-------|---------|-----------|-------------------|
| Submission start → Basic info | 78% | 88% | Simpler category selection |
| Basic info → Images | 78% (of 78%) → 61% net | 90% → 79% net | Native camera + guide |
| Images → Description | 72% (of 61%) → 44% net | 85% → 67% net | AI description draft |
| Description → Submission | 77% (of 44%) → 34% net | 82% → 55% net | Price tool + save draft |

**Projected overall completion: ~55%** (up from 34%)  
**Projected additional monthly submissions: ~2,500**  
**Projected additional monthly listings (at current auth rate): ~1,900**  
**Estimated additional monthly GMV: $7–12M** (at avg. $4,000–$6,000 per listing)

---

## Recommendations Priority Matrix

| Feature | Implementation Effort | Completion Rate Impact | Prioritization |
|---------|----------------------|----------------------|---------------|
| Save draft + recovery email | Low | High (addresses 19% of dropouts) | Ship first |
| Guided step-by-step flow | Medium | High (addresses 41% "too long") | Ship with v1 |
| Mobile native camera upload | Medium | Medium-High (mobile gap) | Ship with v1 |
| AI description generator | High | High (29% of dropouts) | Ship with v1 |
| Price estimation tool | Medium | Medium (24% of dropouts) | Ship with v1 |
| Pre-submission commission clarity | Low | Low-Medium (9% of dropouts) | Quick win |
