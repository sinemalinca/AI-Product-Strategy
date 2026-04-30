# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 3/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 2/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 4/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 3/5 |

### Correction Loop — 3/5
**What you capture today:** Whether the seller accepts or rejects the one-click recommendation, whether they change the suggested CPC, budget, or duration, and how the campaign performs after launch.

**How it compounds:** This helps us understand whether the recommendation was trusted and whether it actually worked. Over time, we can learn which suggestions are accepted more often and which campaign setups perform better. I gave this a 3 because the signal is useful, but it is not yet a fully automated learning loop.

### Preference Loop — 2/5
**What you capture today:** Seller-level choices like preferred budget range, changes to campaign duration, approval behavior, and whether the seller usually accepts or edits the recommendation.

**How it compounds:** In time, the product could learn that some sellers prefer lower-risk budgets, shorter campaigns, or more cautious CPC levels. But today the product is still driven more by marketplace performance data than by deep seller-level personalization. That is why this is still a weak loop.

### Domain Context Loop — 4/5
**What you capture today:** Signals like sales trend, conversion rate, stock status, price, discount level, category performance, campaign results, and seller competition on the same product.

**How it compounds:** What works in one product or category can improve recommendations in similar areas. The system can learn which combinations of stock, conversion, pricing, and sales momentum usually make good ad candidates. This is one of the strongest loops because learning can carry across products, sellers, and categories inside the same marketplace.

### Network Loop — 3/5
**What you capture today:** Broader patterns across many sellers and campaigns, including which recommendation setups work better across product types, seller behaviors, and category conditions.

**How it compounds:** As more sellers use One Click, the system can improve its general recommendation logic using wider marketplace patterns. This helps, but it is not a strong network effect in the classic sense. One seller does not directly create visible value for another seller. The value comes from shared learning, so I see this as a medium-strength loop.

**Total Flywheel Score: 12/20**  
**Weakest Loop:** Preference  
**Fix for weakest loop:** Start capturing seller-level decision patterns more clearly and use them in future recommendations. For example, the product could learn each seller’s usual budget comfort zone, preferred campaign duration, and whether they tend to accept or edit recommendations.

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Amazon Ads  
**Vector:** Launches a similar AI-powered one-click campaign setup inside its own retail media workflow, with stronger automation and broader advertiser trust.  
**Time-to-threat:** 6-9 months  
**% of value at risk:** 40%

### 2. Vertical Competitor
**Attacker:** Trendyol Ads  
**Vector:** Adds a similar one-click campaign setup for marketplace sellers and competes directly for seller ad budget with a familiar local workflow.  
**Time-to-threat:** 3-6 months  
**% of value at risk:** 55%

### 3. Adjacent Expansion
**Attacker:** Google Ads  
**Vector:** Expands merchant-facing automation and campaign recommendations for e-commerce sellers, becoming a trusted place for AI-based ad decisions.  
**Time-to-threat:** 9-12 months  
**% of value at risk:** 25%

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:** Trendyol Ads

**Attack vector (target the weakest loop):** Launch a similar one-click campaign setup and win on simplicity before Hepsiburada builds stronger seller-level learning.

**Weeks 1-4 — what they ship:** Release a basic AI campaign assistant that recommends which product to promote, suggested CPC, budget, and campaign duration in one simple setup flow.

**Weeks 5-8 — how they poach users:** Position it as the fastest way to launch ads, promote it heavily in seller communications, and highlight that sellers do not need to make manual campaign decisions.

**Weeks 9-12 — why users don't come back:** Add simple recommendation explanations and better default settings, so the experience feels easy enough that sellers stop seeing Hepsiburada’s setup flow as worth the extra effort.

**Your defense:** Make One Click stronger not only on simplicity, but on recommendation quality. The real defense is using Hepsiburada’s own marketplace signals better, explaining clearly why a product was selected, and gradually learning what works better for each seller over time.
