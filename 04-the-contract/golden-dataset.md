# Golden Dataset & Reliability Contract

## Golden Dataset Spec

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | Product with strong sales trend, high conversion rate, healthy stock, and stable price | The system should recommend this product for campaign setup, with a reasonable CPC and budget range | N | rule |
| 2 | Product with low stock but strong recent sales and conversion | The system should either avoid recommending this product or clearly reduce confidence and explain the stock risk | Y | rule |
| 3 | Product with high traffic but weak conversion rate | The system should avoid aggressive recommendation and should not suggest a high CPC without strong supporting signals | N | rule |
| 4 | Two similar products where one has better conversion but the other has a stronger sales trend | The system should recommend the better overall candidate and explain the trade-off clearly | Y | LLM |
| 5 | Product with discount applied, strong rating, and improving category performance, but mixed historical campaign results | The system may recommend the product, but the explanation should mention both the positive signals and the uncertainty | Y | LLM |

**Adversarial rows included:** 3  
**Coverage gaps identified by partner:** Cases where the AI may over-recommend high-spend setups, cases where recent short-term signals conflict with longer-term product weakness, and cases where stock risk is not serious enough to block recommendation but still important enough to lower confidence.

## Confidence UX Design

**Approach:** tiered confidence

**High confidence (>90%):**
Show the recommendation as “Recommended” with a short explanation, expected outcome, and a clear primary action such as “Approve and Create Campaign.”

**Medium confidence (70-90%):**
Show the recommendation as “Suggested” instead of “Recommended.” Add a short explanation of trade-offs and encourage the seller to review CPC, budget, and duration before approval.

**Low confidence (<70%):**
Do not present the setup as a strong recommendation. Show a message like “This setup is less certain based on current signals” and ask the seller to review or adjust the campaign manually before launch.

**User control surface:**
The seller can review the recommended product, edit CPC, budget, and duration, and decide whether to approve or adjust the setup before campaign creation.

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | 85%+ recommendation quality on golden dataset | Weekly eval run against labeled test cases | Below 80% |
| Hallucination rate | <2% | Manual review of sampled outputs and flagged cases | Above 5% |
| Latency (p95) | <3 seconds | Product analytics and service monitoring | Above 5 seconds |
| Drift velocity | No major drop across 2 consecutive eval cycles | Compare eval scores over time by scenario type | 5-point drop in 2 cycles |

## HITL Architecture
A human does not need to review every recommendation. The default flow stays self-service. Human review or escalation is needed when confidence is low, when product signals are strongly conflicting, or when the recommendation could push the seller toward unusually high spend with weak support. The first escalation layer is seller-side review through editable fields. A second layer can be internal review for repeated low-confidence or high-risk recommendation patterns.

## Red-Team Findings
One failure mode the partner found is that the AI may recommend an expensive campaign setup too confidently when short-term sales momentum looks strong, even if stock is limited or long-term conversion quality is weak. This matters because the seller may trust the recommendation and overspend on a campaign that is not actually a strong candidate.
