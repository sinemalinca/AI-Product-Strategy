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
