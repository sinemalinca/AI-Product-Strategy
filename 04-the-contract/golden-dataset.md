# Golden Dataset & Reliability Contract

## Golden Dataset Spec

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | Product has strong 14-day sales trend, high conversion rate, healthy stock, stable price, and positive recent campaign performance | Recommend this product with a reasonable CPC, budget, and duration. Explanation should highlight strong trend, conversion, and stock health. | N | rule |
| 2 | Product has strong sales trend and high conversion rate, but stock is low | Do not recommend aggressively. Lower confidence and explain stock risk before campaign approval. | Y | rule |
| 3 | Product has high traffic but weak conversion rate | Avoid a strong recommendation and do not suggest a high CPC without stronger supporting signals. | N | rule |
| 4 | Two similar products exist: one has better conversion rate, the other has stronger recent sales momentum | Recommend the stronger overall candidate and explain the trade-off clearly. | Y | LLM |
| 5 | Product has discount applied, strong rating, and improving category performance, but mixed historical campaign results | Recommendation may be positive, but the explanation must mention both upside and uncertainty. | Y | LLM |
| 6 | Product has high conversion rate and healthy stock, but price is significantly above category average | Do not overstate performance. Recommendation should reflect pricing risk and avoid overly aggressive CPC. | N | rule |
| 7 | Product has weak recent sales, but historically strong campaign ROAS | Do not reject the product too quickly. Weigh historical ad performance and explain why the case is still viable or not. | Y | LLM |
| 8 | Product shows rising sales trend caused by a short-term seasonal spike | Do not treat the spike as stable demand unless broader signals support it. Lower confidence if needed. | Y | rule |
| 9 | Product belongs to a volatile category and has limited recent performance data | Reduce confidence and avoid framing the setup as a strong recommendation. | Y | rule |
| 10 | Product has strong signals overall, but the suggested CPC would push the seller toward unusually high spend | Moderate the bid or clearly explain the spend risk before approval. | Y | LLM |

**Adversarial rows included:** 5

**Judge mix (rule / LLM):** 60% / 40%

**Coverage gap (from partner):**  
The first version covers strong recommendation cases, mixed-signal cases, stock risk, pricing risk, unstable demand, and spend risk. The main remaining gaps are seller-specific behavior, budget sensitivity, and category seasonality patterns that vary across time.

**Sales test: one sentence — "Here's how we test our AI."**  
We test our AI against a versioned set of campaign recommendation scenarios, including hard edge cases, and block release if recommendation quality falls below the expected bar.

## Confidence UX Design

**Approach:** Tiered confidence with visible uncertainty signals and a seller review trigger for low-confidence recommendations.

**Confident (>90%):** Show the setup as **Recommended** with a short explanation, expected outcome, and a clear primary action like **Approve and Create Campaign**. Keep the tone direct and confident, but still allow the seller to edit CPC, budget, and duration before launch.

**Uncertain (50–90%):** Show the setup as **Suggested** instead of **Recommended**. Use softer language, explain the trade-offs, and encourage the seller to review CPC, budget, and duration before approval.

**Not confident (<50%):** Do not present the setup as a strong recommendation. Show a message like **“This setup is less certain based on current signals”** and require the seller to review or adjust the campaign manually before launch.

**User control surface:**  
The seller can review the recommended product, edit CPC, budget, and duration, and decide whether to approve or change the setup before campaign creation. Low-confidence recommendations should show the main uncertainty drivers, such as stock risk, weak conversion support, or unstable recent demand. Seller corrections should be captured as feedback for future evaluation and model improvement.

- Users see AI reasoning / drivers
- Users correct and override outputs
- Corrections feed back into the model / dataset
- Users adjust the confidence threshold *(not yet)*

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | 85%+ recommendation quality on golden dataset | Weekly eval run against labeled test cases | Below 80% |
| Hallucination rate | <2% | Manual review of sampled outputs and flagged cases | Above 5% |
| Latency (p95) | <3 seconds | Product analytics and service monitoring | Above 5 seconds |
| Drift velocity | No major drop across 2 consecutive eval cycles | Compare eval scores over time by scenario type | 5-point drop in 2 cycles |

## HITL Architecture

The default flow stays self-service. Human review is not needed for every recommendation. The first review layer is the seller, who can inspect and edit the setup before launch. Additional escalation is needed when confidence is low, when signals are strongly conflicting, or when the recommendation could push the seller toward unusually high spend with weak support. Repeated low-confidence or high-risk patterns should be reviewed internally and added back into the dataset.

## Red-Team Findings

One important failure mode is that the model may recommend an expensive setup too confidently when short-term sales momentum looks strong, even if stock is limited or long-term conversion quality is weak. This is risky because the seller may trust the recommendation and overspend on a campaign that is not actually a strong candidate.
