# Experiment Roadmap
## Consignment Funnel Optimization — Seller Experience

---

## Experiment 1: AI-Assisted vs. Manual Listing

**The question:** Does providing an AI-generated description draft significantly increase description completion rates and overall submission completion compared to a blank text field?

**Hypothesis:** Sellers abandon the description step primarily due to blank-page anxiety, not disinterest in selling. A pre-populated AI draft reduces the psychological barrier of starting, increasing completion rates and (because sellers spend less time on this step) reducing overall time to submit.

**Variants:**
- **Control (A):** Current blank description text field with placeholder text ("Describe your item's history, condition, and any notable features")
- **Treatment B:** AI-generated draft pre-populated in description field, with "Regenerate" and "Edit" options
- **Treatment C:** Description template/prompts (non-AI): 5 structured fields ("Brand," "Condition details," "Provenance," "Notable features," "Known issues") that compile into a description

**Audience:** All sellers who reach the description step in the submission flow

**Traffic split:** 40% / 30% / 30%  
*(More traffic to control to ensure stable baseline; smaller allocation to Treatment C since we expect Treatment B to win)*

**Primary metric:** Description step completion rate (sellers who complete description / sellers who reach description step)

**Secondary metrics:**
- Overall submission completion rate (start → submit)
- Description word count (Treatment B should increase avg. word count)
- Authentication rejection rate (AI descriptions must not cause misrepresentation)
- Time spent on description step (lower = less friction, but too low might mean sellers aren't reviewing)

**Guardrail metric:** Authentication rejection rate — if AI descriptions lead to more rejections (misrepresentation), we must retrain or add guardrails before continuing.

**Sample size:**
- Baseline description completion: 62% of those who reach the step
- MDE: 15% relative lift → 71%
- Required: ~1,500 sellers reaching description step per variant
- Estimated runtime: 3 weeks (given seller submission volume)

**Expected outcome:** Treatment B wins on completion and time; Treatment C (structured fields) may be a good fallback for sellers who want more control than AI but more structure than blank canvas. Recommend shipping B with C as a "Switch to manual" option.

---

## Experiment 2: Short Form vs. Detailed Form

**The question:** Does reducing required fields in the submission form (minimum viable submission) increase overall completion rates, even if it means less listing detail?

**Hypothesis:** We are over-collecting information at submission time. Many fields we collect upfront could be gathered post-authentication or filled by our specialists. A shorter form will increase completion rates without meaningfully impacting listing quality.

**Variants:**
- **Control (A):** Current form — all fields required (category, title, description, condition, 5 photos, reference numbers, provenance, era, brand)
- **Treatment B:** "Short form" — minimum required fields only (category, 1-line title, condition grade, 3 photos minimum); detailed fields available but optional
- **Treatment C:** Progressive disclosure — same as Control but fields appear progressively after previous section is complete (reduces overwhelm without removing fields)

**Audience:** New sellers only (first-time submitters)  
*Rationale: Experienced sellers already know the process — this experiment is about first-time friction*

**Primary metric:** Submission completion rate (start → submit)

**Secondary metrics:**
- Authentication approval rate (does shorter form lead to more rejections?)
- Listing quality score (buyer satisfaction with listing accuracy — measured post-launch)
- Time to submit
- Seller retention rate at 30 days (do sellers from short-form submit again?)

**Guardrail:** Authentication rejection rate — if Treatment B increases rejections > 2% above baseline, the information was necessary and we should not remove it.

**Expected outcome:** Treatment B wins on completion but may lose on authentication rate. Treatment C (progressive disclosure) is likely the best overall balance — recommend it as the default outcome.

---

## Experiment 3: Price Guidance Visibility vs. Hidden

**The question:** Does showing comparable sale prices and sale probability estimates before sellers input their reserve price increase submission completion and improve reserve price accuracy?

**Hypothesis:** Sellers who see comparable data set more realistic reserve prices (closer to market), which increases sale probability. Additionally, reducing price uncertainty reduces the anxiety that causes abandonment at the pricing step.

**Variants:**
- **Control (A):** Reserve price input with no guidance (current state)
- **Treatment B:** Price range estimate shown ("Similar items sold for $X,XXX–$X,XXX") before input
- **Treatment C:** Full price tool — range estimate + bell curve + sale probability at chosen price

**Primary metric:** Pricing step completion rate (sellers who reach pricing step and submit / sellers who reach pricing step)

**Secondary metrics:**
- Reserve price vs. market estimate ratio (Treatment B/C should bring this closer to 1.0)
- Auction sell-through rate (items that sell / items listed) — measured 90 days post-launch
- Seller satisfaction with outcome (post-auction survey: "Were you satisfied with your sale price?")

**Expected outcome:** Treatment C wins on completion (reduces uncertainty) and improves price accuracy. Long-term sell-through rate should improve as reserve prices become more realistic.

---

## Experiment 4: Save Draft + Recovery Email Impact

**The question:** Does adding save draft functionality + automated recovery emails significantly reduce abandonment and increase overall submission completion?

**Variants:**
- **Control (A):** No save draft (current state — progress lost if browser closed)
- **Treatment B:** Auto-save only (progress saved, accessible via dashboard, no email)
- **Treatment C:** Auto-save + recovery email at 24h ("You're halfway there — finish your submission")

**Primary metric:** Submission completion rate (start → submit), measured over 14-day window per seller  
*(Extended window because save draft allows completion days later)*

**Secondary metrics:**
- Recovery email open rate and click-through rate
- Time between draft start and submission completion (Treatment C should compress this)
- Sellers who complete submission within 7 days vs. same-day (baseline)

**Expected outcome:** Treatment C wins; recovery email is expected to recover 10–15% of abandoned sessions. Even Treatment B (auto-save alone) should show improvement over Control.

---

## Experiment 5: Native Camera vs. File Picker (Mobile Only)

**The question:** Does replacing the file picker with a native camera-first experience on mobile significantly increase photo upload completion rates?

**Variants:**
- **Control (A):** Current file picker (opens iOS/Android file browser)
- **Treatment B:** Native camera integration ("Take Photos" → opens camera with guide overlay)

**Audience:** Mobile users only (iOS and Android)

**Primary metric:** Photo upload completion rate on mobile (users who upload ≥ required photos / users who attempt upload on mobile)

**Secondary metrics:**
- Overall submission completion rate (mobile)
- Time spent on photo step
- Photo quality score (assessed by authentication team via blind review)

**Expected outcome:** +20–30% relative lift in mobile photo completion; downstream improvement in mobile overall completion rate

---

## Experiment Roadmap Timeline

| # | Experiment | Priority | Duration | Start | Dependencies |
|---|-----------|----------|----------|-------|-------------|
| 1 | AI-Assisted vs. Manual Description | P0 | 3 weeks | Week 1 | AI model ready |
| 2 | Save Draft + Recovery Email | P0 | 3 weeks | Week 1 | Email infra |
| 3 | Short Form vs. Detailed Form | P1 | 3 weeks | Week 4 | Form rebuild |
| 4 | Native Camera (Mobile) | P1 | 2 weeks | Week 4 | Mobile dev |
| 5 | Price Guidance Visibility | P1 | 3 weeks | Week 6 | Pricing data pipeline |

*Experiments 1 & 2 can run concurrently (different steps, no interaction effect)*  
*Experiments 3 & 4 can run concurrently on non-overlapping populations*

---

## Impact Estimation

If all 5 experiments ship their expected outcomes:

| Experiment | Completion Rate Impact | Confidence |
|-----------|----------------------|-----------|
| Guided step flow (foundational) | +8–12 pts absolute | High |
| AI description (E1) | +10–15 pts absolute | High |
| Save draft + email (E2) | +4–7 pts absolute | Medium |
| Short form (E3) | +3–5 pts absolute | Medium |
| Native camera (E4) | +3–5 pts absolute on mobile | High |
| Price guidance (E5) | +2–4 pts absolute | Medium |

**Combined projected improvement:** 34% → 50–58% completion rate  
*(Not additive — overlapping effects; use 55% as central estimate)*

**Monthly impact at 55% completion:**
- Additional submissions: ~2,500/month (from 4,200 → 6,700)
- Additional listings (at 76% auth rate): ~1,900/month
- At avg. $5,000 GMV per listing: **~$9.5M additional monthly GMV**
- At 15% commission: **~$1.4M additional monthly revenue**
