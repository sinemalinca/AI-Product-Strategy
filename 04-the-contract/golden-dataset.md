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
| Accuracy | 85% | Weekly eval run against 10 golden rows in v1, expanding over time with rule checks and LLM review for mixed-signal cases. | Below 80% → trigger gold-set audit |
| Hallucination rate | <2% | Weekly eval run plus sampled manual review of explanations and flagged recommendation cases for unsupported claims, overstated confidence, or fabricated rationale. | Above 5% → pause rollout and review recommendation logic |
| Latency (p95) | <3 seconds | Product analytics and service monitoring on One Click recommendation generation time. | Above 5 seconds for 5 minutes → page on-call |
| Drift velocity | No major drop across 2 consecutive eval cycles | Compare eval results over time across the golden dataset, especially mixed-signal and adversarial cases. | 5-point drop across 2 eval cycles → trigger gold-set audit |

## HITL Architecture

**Trigger:** Confidence <50% OR recommendation includes strong spend risk, stock risk, or conflicting product signals.

**Reviewer:** Primary reviewer is the seller through manual review and editable fields. Repeated high-risk or low-confidence patterns are reviewed internally by the product or ads team.

**Feedback loop:** Seller edits, overrides, and repeated low-confidence cases should feed back into the golden dataset review and future recommendation evaluation.

## Red-Team Findings

My partner ran a **Confident Hallucination** attack around a product that showed strong short-term sales momentum, but had limited stock and a suggested CPC that would push the seller toward unusually high spend. The concern was that the AI might still present this as a strong recommendation because the recent sales signal looks attractive.

**Worst miss they found that I'd missed:**  
The model may over-trust short-term performance signals and produce a confident recommendation, even when stock risk and spend risk should clearly reduce confidence. In that case, the seller could overspend on a campaign that is not actually a strong candidate.

**Severity:**  
High

**New gold row I'm adding to close the gap:**  
Input: Product shows strong short-term sales momentum, but stock is limited and the recommended CPC would push the seller toward unusually high spend.  
Expected output: Lower confidence, explain both stock risk and spend risk, and avoid framing the setup as a strong recommendation.  
Edge case: Y  
Judge type: rule + LLM
