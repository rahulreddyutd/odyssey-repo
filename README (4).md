# Product Management Portfolio
## Collectibles Marketplace — Case Studies

> Three end-to-end PM case studies for a high-end collectibles auction marketplace.  
> Each project includes a full PRD, user research, metrics framework, and experimentation plan.

---

## About This Portfolio

These projects demonstrate product thinking across the full buyer-seller marketplace loop — from how buyers discover and bid on items, to how sellers get their items onto the platform.

Each case study is structured the way real product work is done: grounded in data, designed around user needs, validated through experimentation, and tied to business outcomes.

---

## Projects

### 1. [AI-Powered Collectibles Discovery Engine](./ai-discovery-engine/)
**Problem:** Collectors can't find what they're looking for. Search is keyword-only, the homepage is identical for every user, and there's no way to discover items like ones you love.

**Solution:** Personalized homepage, intent-aware search ("rare vintage watches under $5k"), AI similarity engine ("More Like This"), and smart contextual filters.

**Impact target:** Homepage CTR +41% · Search abandonment -26% · Pages/session +56%

→ [View Project](./ai-discovery-engine/README.md)

---

### 2. [Bidding Experience Optimization](./bidding-experience-optimization/)
**Problem:** 46% of mobile users abandon during bidding. The flow takes 8 taps and 3 page navigations. Real-time auction state isn't visible. Most users who get outbid don't come back.

**Solution:** Single-modal bid flow (3 taps), real-time WebSocket price updates, live countdown timer, integrated auto-bid with proxy bidding logic.

**Impact target:** Bid completion +21% · Mobile completion +33% · Outbid re-bid rate +77% · +$8–12M monthly GMV

→ [View Project](./bidding-experience-optimization/README.md)

---

### 3. [Consignment Funnel Optimization](./consignment-funnel-optimization/)
**Problem:** 66% of sellers who start a consignment submission never finish it. The form is too long, description writing causes anxiety, pricing is opaque, and there's no way to save progress.

**Solution:** Step-by-step guided flow, AI-generated listing descriptions, comparable price estimation tool, auto-save with recovery emails.

**Impact target:** Completion rate 34% → 55% · Time to submit -50% · Seller retention +50% · +$9.6M monthly GMV

→ [View Project](./consignment-funnel-optimization/README.md)

---

## Skills Demonstrated

**Product Discovery**
- User research synthesis → persona development
- Funnel analysis with segment breakdowns
- Exit survey analysis and root cause identification
- Emotional journey mapping (current vs. future state)

**Product Strategy**
- Opportunity sizing with conservative / base / optimistic scenarios
- Competitive landscape analysis
- Make-or-buy decisions (AI vs. template vs. blank canvas)
- Phased rollout strategy with risk mitigation

**Requirements & Execution**
- Full PRDs with user stories and acceptance criteria
- Technical architecture documentation
- Dependency mapping across cross-functional teams
- Ethical design constraints (social proof integrity, AI accuracy guardrails)

**Data & Metrics**
- North star metric selection with rationale
- 4-layer KPI hierarchies (input → output → revenue → guardrail)
- A/B experiment design with sample size calculations
- Impact models tied to revenue

**Experimentation**
- Frequentist A/B testing framework
- Multi-arm experiments with pre-registration
- Ethical guardrails on urgency and social proof features
- Interaction effects analysis

---

## Document Structure

```
portfolio/
├── README.md  ←  You are here
│
├── ai-discovery-engine/
│   ├── README.md
│   ├── PRD.md
│   ├── user-personas.md
│   ├── experimentation-plan.md
│   ├── metrics-dashboard.md
│   └── wireframes/  (see Figma link)
│
├── bidding-experience-optimization/
│   ├── README.md
│   ├── PRD.md
│   ├── current-vs-proposed-flow.md
│   ├── kpi-framework.md
│   ├── ab-testing-plan.md
│   ├── product-strategy.md
│   └── wireframes/  (see Figma link)
│
└── consignment-funnel-optimization/
    ├── README.md
    ├── PRD.md
    ├── funnel-analysis.md
    ├── user-journey-map.md
    ├── experiment-roadmap.md
    └── impact-estimation.md
```


