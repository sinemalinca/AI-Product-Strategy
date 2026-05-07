# Cost Curve & Pricing Strategy

## Packaging Decision

**Leader:** One-click campaign setup recommendation  
**Filler:** AI-written campaign explanation  
**Killer:** Advanced always-on campaign optimization agent  
**Killer usage %:** 20–30%  
**Bundle or add-on:** Add-on

## Cost Model

| Cost Category | Monthly Cost | Notes |
|--------------|--------------|-------|
| Inference (small model) | $7.88 | Covers simple flows such as short recommendation explanations and low-complexity recommendation tasks. Assumes 70% of 5,000 monthly requests run on Claude Haiku 4.5. |
| Inference (mid model) | $15.00 | Covers standard One Click recommendation flows that need more reasoning than the small model path. Assumes 25% of 5,000 monthly requests run on Claude Sonnet 4.6. |
| Inference (frontier model) | $10.00 | Covers edge cases, low-confidence recommendations, or more complex reasoning. Assumes 5% of 5,000 monthly requests run on Claude Opus 4.7. |
| Infrastructure | $0.20 | Basic orchestration, logging, and service costs. |
| Data/storage | $0.15 | Storing recommendation events, campaign inputs, and performance signals. |
| Human-in-the-loop | $0.05 | Light internal review and quality checks. |
| **Total AI COGS** | **$33.28 / month** | Estimated monthly AI-related cost for 5,000 One Click requests. |

## Cascading Strategy

**Small model:** Claude Haiku 4.5  
**Mid model:** Claude Sonnet 4.6  
**Frontier model:** Claude Opus 4.7  

**Routing rule:** Most requests should start on the cheapest path. Simple explanation flows and low-complexity recommendation tasks go to Haiku. Standard recommendation flows go to Sonnet. Only edge cases, low-confidence recommendations, or more complex reasoning go to Opus.  

**Expected model mix:**  
- Small: 70%  
- Mid: 25%  
- Frontier: 5%

## Pricing Model

**Current pricing:** Sponsored Product Ads is already part of the marketplace ads flow. Sellers pay through ad spend, not through a separate AI fee.  

**Proposed AI pricing:** One Click can stay bundled as a lightweight recommendation feature, as long as the expensive path stays limited. If usage grows a lot or more advanced automation is added later, a premium automation tier may be needed.  

**Model:** hybrid

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Margin gets tighter, especially if more traffic shifts to Sonnet or Opus. | Reduce frontier usage, simplify explanation generation, and move more flows to cheaper models or internal rules. |
| Heaviest segment doubles | A sharp rise in recommendation volume increases total AI cost quickly. | Add guardrails, improve caching, and keep the default flow on the cheap path. |
| Model provider raises prices 50% | AI COGS rises meaningfully, especially on the mid and frontier paths. | Test a backup provider, reduce non-essential calls, and shift more traffic to fallback logic where possible. |

## Board One-Pager

**Before (traditional SaaS):** Sellers create campaigns manually. Setup takes more effort, and some sellers may drop before launching ads. Revenue comes from ad spend, but campaign creation is limited by friction.  

**After (AI-enabled):** One Click helps sellers launch campaigns faster by recommending the product, CPC, budget, and duration in one flow. At a monthly volume of 5,000 requests, the feature still looks manageable if most traffic stays on the small and mid paths and only a small share is escalated to the frontier model.  

**Net margin shift:** AI adds variable cost, so margin is lower than a fully manual setup flow. But if One Click increases campaign creation and ad spend enough, the overall business impact can still be positive.


## Board One-Pager evaluated with given prompt

**Before (traditional SaaS):**
- **Current pricing:** Sponsored Product Ads is part of the marketplace ads flow. Sellers pay through ad spend, not through a separate AI fee.
- **Current gross margin:** 90%
- **Value framed as:** Sellers create campaigns manually or through coded recommendation logic. The product creates value by enabling ad spend, but campaign creation is still limited by setup friction and decision effort.

**After (AI-enabled):**
- **Proposed pricing:** One Click stays bundled as a lightweight recommendation feature for now. If usage grows a lot or more advanced automation is added later, a premium automation tier may be needed.
- **AI COGS per user/month:** $0.13 per active seller/month
- **Expected gross margin:** 88%
- **Value framed as:** One Click helps sellers launch campaigns faster by recommending the product, CPC, budget, and duration in one flow. The value is not just AI access. The value is lower setup effort, faster campaign launch, and potentially higher ad spend.

**Net margin shift:**
- **Margin moves from 90% to 88%.**
- The margin changes because AI adds a new variable cost layer. The old setup relied more on coded logic, while the new setup uses model-based decisioning. That creates extra inference and monitoring cost, but the cost is still manageable at the current monthly volume.

**Why this is still a good business:**
- This is still a good business if One Click increases campaign creation enough to lift total ad spend.
- Even if margin per action is slightly lower, total gross profit can still improve if more sellers launch campaigns and spend more.
- The business case gets stronger if easier setup also improves repeat usage over time.
- The key condition is that most traffic stays on the small and mid model paths, while the frontier model is used only for edge cases.

**Board-ready narrative:**
One Click is not a free AI layer. It adds real variable cost to campaign setup, so margin will be a bit lower than in the old coded-logic version. But at the current working volume, the cost still looks manageable because most requests stay on the small and mid model paths, and only a small share goes to the frontier model. The upside is that sellers can launch campaigns with less effort, which can increase campaign creation and total ad spend. The main risk is cost creep if usage grows faster than expected or if too many requests move to the expensive path. The mitigation is clear: strong cascading, usage guardrails, fallback logic, and a premium tier if advanced usage grows.

**The bet works if...**
The bet works if One Click increases campaign creation and ad spend enough to offset the added AI cost, while keeping most traffic on the cheaper paths and reserving the frontier model for edge cases only.

---

## Trade-offs

- Moving from coded logic to AI decisioning makes the product more flexible, but also less deterministic.
- Recommendation quality may improve, especially in edge cases, but evaluation and monitoring become more important.
- Setup can feel easier and smarter for sellers, but the cost to serve is no longer close to zero.
- The old model was cheaper and easier to control. The new model has more upside, but it also needs stronger routing, guardrails, and fallback planning.
- This trade-off is worth it only if the increase in campaign creation and ad revenue is larger than the added AI cost.
