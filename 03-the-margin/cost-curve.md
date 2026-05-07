# Cost Curve & Pricing Strategy

## Packaging Decision

**Leader:** One-click campaign setup recommendation  
**Filler:** AI-written campaign explanation  
**Killer:** Advanced always-on campaign optimization agent  
**Killer usage %:** 30%  
**Bundle or add-on:** Add-on

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $0.04 | This is the cost of the more expensive model path for harder recommendation cases. I assumed only a small share of requests goes here. |
| Inference (cascading/triage) | $0.07 | This is the larger share of requests. Most One Click flows should run on a cheaper path first. |
| Infrastructure | $0.05 | Basic backend orchestration, logging, and service costs. |
| Data/storage | $0.03 | Storing recommendation events, campaign inputs, and performance signals. |
| Human-in-the-loop | $0.02 | Light internal review for recommendation quality and tuning. |
| **Total AI COGS** | **$0.21** | Estimated monthly cost per active seller using One Click. |

## Cascading Strategy

**Triage model:** Claude Haiku 4.5  
**Frontier model:** Claude Opus 4.7  
**Routing rule:** Most requests should go through a cheaper path first. Standard recommendation and short explanation flows can run on Haiku. Only edge cases, low-confidence recommendations, or more complex reasoning should go to Opus.  
**Expected cascade ratio:** 80/20

## Pricing Model

**Current pricing:** Sponsored Product Ads is already part of the marketplace ads flow. Sellers pay through ad spend, not through a separate AI fee.  

**Proposed AI pricing:** In the first phase, One Click should stay bundled inside the core ads workflow because it helps increase campaign creation and ad spend. Later, more advanced automation features could be offered as a premium layer for larger sellers.  

**Model:** hybrid

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | Margin drops, but the feature can still survive if most traffic stays on the cheap path. | Reduce use of expensive models, simplify explanation generation, and move more flows to rules or Haiku. |
| Heaviest segment doubles | Power sellers can create much more AI traffic than expected and push blended cost up faster. | Add usage guardrails, improve caching, and give heavy users a more optimized path. |
| Model provider raises prices 50% | Total AI COGS increases, especially if too many requests depend on the expensive model path. | Shift more traffic to fallback logic or cheaper models, and test a backup provider. |

## Board One-Pager

**Before (traditional SaaS):** Sellers create campaigns manually. Setup takes more effort, and some sellers drop before launching ads. Revenue comes from ad spend, but campaign adoption is limited by friction.  

**After (AI-enabled):** One Click helps sellers launch campaigns faster by recommending the product, CPC, budget, and duration in one flow. This can increase campaign creation and total ad spend, while keeping cost under control through cascading.  

**Net margin shift:** Margin may go down slightly on a per-action basis because AI adds variable cost, but if One Click increases campaign adoption enough, the overall business impact can still be positive.
