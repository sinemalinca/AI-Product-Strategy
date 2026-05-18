# Sponsored Product Ads — AI One Click Campaign Setup

> We are building an AI-powered one-click campaign setup for marketplace sellers, so they can create sponsored product campaigns faster and with less manual decision-making, using Hepsiburada’s closed-loop product, campaign, and marketplace performance signals.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [ ] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Hepsiburada Sponsored Product Ads — AI-assisted One Click Campaign Setup
- **AI Value Archetype:** Automator
- **Vulnerability Scores:** Moat 4/5 · Data 5/5 · Platform 3/5
- **Top Risk:** Marketplace competitors such as Trendyol Ads or Amazon Ads can copy the one-click setup experience and use stronger seller trust or larger buyer reach to capture seller ad budget.
- **Confidence:** M
- **Prototype:** https://sponsoredproductadsoneclick.lovable.app
- **Kill Criteria:** Stop or pivot if sellers do not trust the AI-generated recommendations, continue to prefer manual campaign setup, reject recommendations most of the time, or if One Click does not improve campaign creation, activation, or advertising performance compared to the existing self-service flow.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** 12/20
- **Weakest Loop:** Preference
- **Competitive Position:** The product is strongest where Hepsiburada combines marketplace-native sponsored visibility with closed-loop commerce data. External AI tools can copy the surface experience, but they cannot directly access Hepsiburada’s product impressions, clicks, conversion, stock, pricing, campaign outcomes, and seller behavior.
- **Top Encroachment Threat:** Trendyol Ads and Amazon Ads
- **Encroachment Defense:** Defend by making One Click stronger not only on simplicity, but on recommendation quality, seller trust, and Hepsiburada’s marketplace-specific performance signals. The long-term defense is learning from seller-level decisions, campaign outcomes, and category-level performance patterns over time.
- **Vendor Portability:** Partial

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):** 90%
- **Gross Margin (AI-adjusted):** 88%
- **Pricing Model:** Hybrid. One Click stays bundled in the Sponsored Product Ads flow for now, while advanced automation could become a premium add-on later.
- **Total AI COGS:** $33.28/month for 5,000 One Click requests, or about $0.13 per active seller/month under the working assumption.
- **Cascading Strategy:** 70% small model, 25% mid model, 5% frontier model. Simple flows run on the cheapest path, standard recommendation flows use the mid model, and frontier usage is reserved for edge cases or low-confidence recommendations.
- **Net Margin Shift:** Margin moves from 90% to 88% because AI adds a new variable cost layer. The bet still works if One Click increases campaign creation and ad spend enough to offset the added AI cost.
- **Break-even at:** One Click must lift campaign creation and ad spend enough to cover the added AI cost while keeping most traffic on cheaper model paths.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** 85%+ recommendation quality on the v1 golden dataset
- **Golden Dataset:** 10 rows, 5 adversarial
- **Judge Mix:** 60% rule / 40% LLM
- **Confidence UX:** Tiered confidence with visible uncertainty signals and a seller review trigger for low-confidence recommendations.
- **HITL Architecture:** The first reviewer is the seller through manual review and editable fields. Repeated high-risk or low-confidence patterns are reviewed internally by the product or ads team.
- **Failure Mode Coverage:** Covers mixed signals, stock risk, pricing risk, unstable demand, high spend risk, and confident hallucination where the model may sound confident while making a weak or risky recommendation.
- **Key Red-Team Finding:** The model may over-trust short-term performance signals and recommend a high-spend setup too confidently when stock and spend risk should reduce confidence.

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** The strongest long-term loop is recursive learning from seller approvals, edits, overrides, rejected recommendations, and post-campaign performance. Today this loop is still broken because those signals do not reliably flow back into the recommendation system yet.
- **Context Connectivity:** Campaign performance data, product funnel metrics, seller edits, category benchmarks, stock signals, pricing data, and ad spend outcomes should flow into one shared recommendation feedback view across product, ads, data, and seller-facing teams.
- **Governance Posture:** AI can recommend and explain, but the seller stays in control of any spend-impacting action. Campaign launch, CPC changes, and budget changes require seller approval.
- **Shadow AI Status:** 5 workarounds found and triaged: 4 build candidates, 1 partner candidate, 0 ignore. Estimated hidden spend is about $130/month across surveyed or assumed users.
- **Agent Boundaries:** Current system is a recommendation assistant, not an autonomous agent. It can recommend product, CPC, budget, duration, rationale, confidence, and risks. It cannot launch campaigns, change bids or budgets, access unrelated seller data, or train external models on seller-level data.
- **Regulatory Exposure:** Limited. The product influences advertising setup decisions but does not make hiring, credit, medical, legal, or eligibility decisions. Main risks are financial impact on sellers, misleading confidence, data privacy, and unfair or overly aggressive recommendations.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):** To be completed in Module 6
- **Horizon 2 (Next):** To be completed in Module 6
- **Horizon 3 (Bet):** To be completed in Module 6
- **Board Narrative:** To be completed in Module 6
- **Key Metric:** To be completed in Module 6

→ Details: [`06-the-pitch/`](06-the-pitch/)
