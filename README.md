# Hepsiburada Sponsored Product Ads — Self-Service Campaign Setup

> We are building an AI-powered one-click campaign setup for marketplace sellers, so they can create sponsored product campaigns faster and with less manual decision-making, using product performance signals such as sales trend, conversion rate, and stock availability.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [x] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Hepsiburada Sponsored Product Ads — Self-Service Campaign Setup
- **AI Value Archetype:** Automator
- **Vulnerability Scores:** Moat 4/5 · Data 5/5 · Platform 3/5
- **Top Risk:** The biggest strategic risk is that competitors copy the one-click AI campaign setup experience and use a larger buyer audience or stronger seller trust to capture more marketplace ad budget.
- **Confidence:** M
- **Prototype:** https://sponsoredproductadsoneclick.lovable.app
- **Kill Criteria:** We would stop or pivot this bet if sellers do not trust the AI-generated recommendations, if they still prefer manual campaign setup, or if the recommended campaigns do not show better adoption, activation, or advertising performance compared to the existing self-service flow.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:**
- **Weakest Loop:** Preference
- **Top Encroachment Threat:** Amazon Ads
- **Encroachment Defense:** Start capturing seller-level decision patterns more clearly and use them in future recommendations. For example, the product could learn each seller’s usual budget comfort zone, preferred campaign dur…
- **Vendor Portability:** Partial

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):**
- **Gross Margin (AI-adjusted):**
- **Pricing Model:** hybrid
- **Pricing Today → Tomorrow:** Sponsored Product Ads is already part of the marketplace ads flow. Sellers pay through ad spend, not through a separate AI fee. → One Click can stay bundled as a lightweight recommendation feature, as long as the expensive path stays limited. If usage grows a lot or more advanced automation is added later, a premium automation tier may be needed.
- **Total AI COGS / unit:**
- **Cascading Strategy:** frontier: Claude Opus 4.7
- **Net Margin Shift:** AI adds variable cost, so margin is lower than a fully manual setup flow. But if One Click increases campaign creation and ad spend enough, the overall business impact can still be positive.
- **Break-even at:**

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** 85%+ recommendation quality on the v1 golden dataset
- **Golden Dataset:** 10 rows, 5 adversarial
- **Confidence UX:** Tiered confidence with visible uncertainty signals and a seller review trigger for low-confidence recommendations.
- **HITL Architecture:** **Trigger:** Confidence <50% OR recommendation includes strong spend risk, stock risk, or conflicting product signals.
- **Failure Mode Coverage:** My partner ran a **Confident Hallucination** attack around a product that showed strong short-term sales momentum, but had limited stock and a suggested CPC that would push the seller toward unusually high spend.…

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** | Loop | Input | Output | Compounds? | Status | |------|-------|--------|-----------|--------| | Recursive Learning | Seller approvals, edits, overrides, rejected recommendations, and post-campaign performance signals su…
- **Governance Posture:** This policy covers the AI-assisted One Click campaign setup flow for Sponsored Product Ads. It includes product selection recommendations, suggested CPC, daily budget, campaign duration, confidence messaging, and seller-…
- **Autonomy Boundaries:** - **Auto:** The AI can analyze product and campaign signals, recommend a product to advertise, suggest CPC, daily budget, and campaign duration, generate a seller-facing explanation, assign a confidence level, and flag risk drivers such as …
- **Escalation Triggers:** Escalation is required when confidence is below 50%, when the suggested setup includes unusually high spend, when stock risk is material, when product signals conflict, or when the recommendation repeatedly gets edited o…
- **Audit Cadence:** The product manager owns the governance policy and reviews it monthly with the ads, data, and engineering teams.…
- **Shadow AI Audit (user-side):** 5 workarounds found · 4 build candidates, 1 partner candidate, 0 ignore build candidates · adjacent spend Approximately $130/month across surveyed or assumed users
- **Agent Boundaries:** Current agent status: recommendation assistant, not autonomous agent.
- **Regulatory Exposure:** Risk tier: Limited

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):**
- **Horizon 2 (Next):**
- **Horizon 3 (Bet):**
- **Board Narrative:** **The case:**
- **Ask:** ## M1 Baseline vs. Now
- **Key Strategic Change:**

→ Details: [`06-the-pitch/`](06-the-pitch/)
