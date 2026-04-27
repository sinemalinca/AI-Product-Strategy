# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** Hepsiburada Sponsored Product Ads — Self-Service Campaign Setup  
**Your Role:** Product Manager

Hepsiburada Sponsored Product Ads allows marketplace sellers to promote the products they sell on Hepsiburada. Sponsored products can appear higher in search results or ahead of other sellers offering the same product, helping sellers increase product visibility and generate incremental sales within the marketplace.

For this diagnostic, the scope is limited to the self-service seller experience: sellers use their admin panel to view eligible products, create sponsored product campaigns, define budget and CPC settings, and track campaign performance through a dashboard.

---

## Scores

### Contextual Moat — 4/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:**

Sponsored Product Ads has a strong contextual moat inside the Hepsiburada marketplace because sellers cannot gain sponsored visibility on Hepsiburada through an external advertising platform. If a seller wants to promote products in Hepsiburada search results or win visibility against other sellers of the same product, they need to use Hepsiburada’s own advertising tools.

However, advertising is not the seller’s entire daily sales operation. Sellers can still receive organic sales without running ads, and they may also allocate their advertising budgets to other marketplaces where they sell. This means the product has strong in-platform dependency, but seller budget can still shift if campaign setup feels difficult, performance is unclear, or competing marketplaces promise better returns.

The moat is strongest where Sponsored Product Ads is directly connected to marketplace sales outcomes, product-level visibility, and hourly performance tracking. The risk is that sellers may abandon campaign creation if the self-service flow is too complex or if they do not trust the recommended setup.

**Named attacker (from partner challenge):** Trendyol Ads

---

### Data Advantage — 5/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:**

Hepsiburada has a strong proprietary data advantage because it owns closed-loop marketplace data that external AI platforms or generic ad tools cannot directly access. This includes product impressions, clicks, add-to-cart events, purchases, conversion rates, ROAS, category performance, product price, stock, discounts, ratings, reviews, and the number of sellers offering the same product.

This data is highly valuable because Sponsored Product Ads decisions are not only about generating clicks. The system can recommend products with stronger sales potential, suggest more profitable CPC bids, and guide sellers toward campaigns that are more likely to convert within Hepsiburada’s own marketplace context.

The data advantage compounds with usage: the more sellers create campaigns, the more Hepsiburada can learn which products, categories, CPC levels, budgets, time windows, and seller behaviors lead to better advertising outcomes. This creates a meaningful advantage over generic AI tools, because the strongest signals come from Hepsiburada’s own commerce funnel and transaction data.

**Named attacker (from partner challenge):** Amazon Ads

---

### Platform Exposure — 3/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:**

The product has moderate platform exposure. A generic AI platform like OpenAI or Google cannot directly replace Hepsiburada Sponsored Product Ads unless it is integrated into Hepsiburada’s advertising infrastructure. Sponsored visibility inside Hepsiburada is marketplace-native, so external tools cannot independently place ads in Hepsiburada search results or manage seller campaigns without access to Hepsiburada’s systems.

The more realistic risk comes from marketplace competitors such as Trendyol or Amazon. They can copy the hero feature — one-click campaign setup — inside their own ad products. They can also claim a simpler campaign creation experience, a larger buyer audience, or higher advertising revenue potential for sellers.

Hepsiburada’s defense is its ability to combine marketplace-specific performance data with campaign automation. The strongest version of the product is not just “one-click setup,” but a trusted AI-assisted setup that recommends the right products, CPC bids, budgets, and campaign timing based on real conversion potential inside Hepsiburada.

**Named attacker (from partner challenge):** Trendyol Ads + Amazon Ads

---

## Killer Memo

> You run AI at **Trendyol / Amazon Ads**. Your OKR: make this product irrelevant.
>
> **3-sentence memo:**
>
> 1. **Attack:** We will attack Hepsiburada Sponsored Product Ads by making campaign creation feel easier, faster, and more performance-oriented for sellers inside our own marketplace ad platform.
> 2. **Wedge:** Our wedge will be an AI-powered one-click campaign setup that recommends the best products to advertise, the optimal CPC bid, the right budget, and the best campaign timing with minimal seller effort.
> 3. **Why users switch:** Sellers will shift more of their ad budget to us if we can promise a larger buyer audience, easier campaign setup, clearer performance visibility, and stronger incremental sales potential.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->

The biggest strategic risk is that competitors copy the one-click AI campaign setup experience and use a larger buyer audience or stronger seller trust to capture more marketplace ad budget.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->

**M**

I am moderately confident in this bet. Hepsiburada has a strong data advantage and in-platform control over sponsored visibility, but the user experience and seller trust must be strong enough to prevent ad budget from shifting to competing marketplaces.
