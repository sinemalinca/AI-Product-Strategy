# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | If this product moves beyond the prototype stage, it would likely rely on one main LLM provider for parts of the recommendation or explanation flow. Right now the prototype uses mock data, but the future risk is becoming too dependent on one external vendor. | M | Pause non-essential model usage, keep the core recommendation flow running with internal fallback logic, and start testing one backup provider in parallel. |
| **Abstraction** | This can be kept flexible if the recommendation logic sits behind an internal layer instead of being tied directly to one vendor API. But if the product is built too closely around one provider, switching later becomes harder. | M | Move recommendation generation behind an internal service layer so the business logic stays stable even if the model provider changes. |
| **Routing** | If all recommendation traffic goes through one provider, there is limited flexibility. A better setup would allow fallback logic or a second provider for some parts of the flow. | M | Route the core recommendation flow through internal fallback logic first, reduce provider usage where possible, and test a second route for lower-risk tasks like explanation text. |
| **Eval** | This is the weakest area unless the team has a fixed way to compare outputs across providers. Without a stable evaluation set, switching vendors becomes risky because quality may drop without the team noticing early enough. | H | Use a fixed set of seller cases, products, and expected recommendation outcomes to compare the current setup with fallback logic or a backup provider within 48 hours. |

## Portability Score
<!-- Ready / Partial / Locked -->

Partial

## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->

If the primary vendor suddenly doubles pricing, the first step would be to reduce or pause any non-essential model usage. The core recommendation flow would temporarily fall back to internal logic based on historical campaign results, category benchmarks, conversion signals, stock status, and pricing data.

At the same time, the team would test at least one backup provider using a fixed evaluation set. If the backup meets the minimum quality bar, traffic can start shifting in stages. If not, the product can stay in fallback mode until a safer replacement is ready.

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->

What they can copy is the surface experience: a simple AI flow, a one-click setup, or a recommendation card.

What is harder to copy is Hepsiburada’s own marketplace data. The real advantage comes from seller behavior, product-level conversion signals, stock and pricing context, campaign history, and the link between sponsored visibility and real transaction outcomes inside the marketplace.

That means the long-term defense is not the AI layer alone. It is making One Click deeply tied to Hepsiburada’s own data, seller context, and measurable business results.
