Golden Dataset — Module 4

Test cases:
  1. Edge: N · Judge: rule — IN: Product has strong 14-day sales trend, high conversion rate, healthy stock, stable price, and positive recent campaign performance → OUT: Recommend this product with a reasonable CPC, budget, and duration. Explanation should highlight strong trend, conversion, and stock health.
  2. Edge: Y · Judge: rule — IN: Product has strong sales trend and high conversion rate, but stock is low → OUT: Do not recommend aggressively. Lower confidence and explain stock risk before campaign approval.
  3. Edge: N · Judge: rule — IN: Product has high traffic but weak conversion rate → OUT: Avoid a strong recommendation and do not suggest a high CPC without stronger supporting signals.
  4. Edge: Y · Judge: LLM — IN: Two similar products exist: one has better conversion rate, the other has stronger recent sales momentum → OUT: Recommend the stronger overall candidate and explain the trade-off clearly.
  5. Edge: Y · Judge: LLM — IN: Product has discount applied, strong rating, and improving category performance, but mixed historical campaign results → OUT: Recommendation may be positive, but the explanation must mention both upside and uncertainty.
  6. Edge: N · Judge: rule — IN: Product has high conversion rate and healthy stock, but price is significantly above category average → OUT: Do not overstate performance. Recommendation should reflect pricing risk and avoid overly aggressive CPC.
  7. Edge: Y · Judge: LLM — IN: Product has weak recent sales, but historically strong campaign ROAS → OUT: Do not reject the product too quickly. Weigh historical ad performance and explain why the case is still viable or not.
  8. Edge: Y · Judge: rule — IN: Product shows rising sales trend caused by a short-term seasonal spike → OUT: Do not treat the spike as stable demand unless broader signals support it. Lower confidence if needed.
  9. Edge: Y · Judge: rule — IN: Product belongs to a volatile category and has limited recent performance data → OUT: Reduce confidence and avoid framing the setup as a strong recommendation.
  10. Edge: Y · Judge: LLM — IN: Product has strong signals overall, but the suggested CPC would push the seller toward unusually high spend → OUT: Moderate the bid or clearly explain the spend risk before approval.

Dataset health
- Total: 10
- Edge cases: 7 (70.0%)
- Judge mix: 60% rule / 40% LLM / 0% both
