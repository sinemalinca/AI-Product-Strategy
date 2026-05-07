# Cost Curve & Pricing Strategy

## Packaging Decision

**Leader:** One-click campaign setup recommendation  
**Filler:** AI-written campaign explanation  
**Killer:** Advanced always-on campaign optimization agent  
**Killer usage %:** 20–30%  
**Bundle or add-on:** Add-on

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $10.00 | I assumed only 5% of monthly One Click requests go to the most expensive path for harder or low-confidence cases. |
| Inference (cascading/triage) | $22.88 | This covers the larger share of requests on cheaper paths. Most flows should stay here. |
| Infrastructure | $0.20 | Basic orchestration, logging, and service costs. |
| Data/storage | $0.15 | Storing recommendation events, campaign inputs, and performance signals. |
| Human-in-the-loop | $0.05 | Light internal review and quality checks. |
| **Total AI COGS** | **$33.28 / month** | Estimated monthly AI-related cost for 5,000 One Click requests. |

## Cascading Strategy

**Triage model:** Claude Haiku 4.5  
**Frontier model:** Claude Opus 4.7  
**Routing rule:** Most requests should go through the cheaper path first. Standard recommendation flows and short explanations should stay on Haiku. Only edge cases, low-confidence recommendations, or more complex reasoning should go to Opus.  
**Expected cascade ratio:** 95/5

## Pricing Model

**Current pricing:** Sponsored Product Ads is already part of the marketplace ads flow. Sellers pay through ad spend, not through a separate AI fee.  

**Proposed AI pricing:** One Click can stay bundled as a lightweight recommendation feature, as long as the expensive model path stays limited. If usage grows much more or advanced automation is added, a premium automation tier may be needed later.  

**Model:** hybrid

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Margin becomes much tighter, especially if too many requests move to the expensive path. | Reduce frontier usage, simplify explanation generation, and shift more traffic to cheaper models or internal rules. |
| Heaviest segment doubles | A sudden increase in recommendation volume can push AI cost up quickly. | Add guardrails, improve caching, and keep the default flow on the cheap path. |
| Model provider raises prices 50% | AI COGS rises meaningfully, but the feature can still survive if the core recommendation flow is not fully dependent on the expensive model. | Test a backup provider, reduce non-essential calls, and route more requests through fallback logic. |

## Board One-Pager

**Before (traditional SaaS):** Sellers create campaigns manually. Setup takes more effort, and some sellers may drop before launching ads. Revenue comes from ad spend, but campaign creation is limited by friction.  

**After (AI-enabled):** One Click helps sellers launch campaigns faster by recommending the product, CPC, budget, and duration in one flow. With a 5,000-request monthly volume, the feature still looks manageable if most requests stay on the cheap path and only a small share is escalated.  

**Net margin shift:** AI adds variable cost, so margin is lower than a fully manual setup flow. But if One Click increases campaign creation and ad spend enough, the overall business impact can still be positive.
