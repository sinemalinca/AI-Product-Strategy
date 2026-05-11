## Defender Briefing — 60 seconds

**Bet:** AI-driven One Click campaign setup that recommends the best product, CPC, budget, and duration for marketplace sellers.
**Users + domain:** Marketplace sellers using Sponsored Product Ads in a self-service e-commerce ad platform.

**Top 3 golden rows already covered:**
1. Strong product signals: high sales trend, high conversion, healthy stock, stable price, positive campaign history → recommend with a reasonable CPC, budget, and duration.
2. Strong sales and conversion but low stock → lower confidence and explain stock risk before approval.
3. High traffic but weak conversion → avoid a strong recommendation and do not suggest an aggressive CPC without stronger supporting signals.

**Confidence threshold + low-confidence behavior:** Over 90%: show as Recommended with a clear approve action.
50–90%: show as Suggested with softer language and visible trade-offs.
Below 50%: do not present it as a strong recommendation; seller must review or adjust manually before launch.

**Where I think the holes are:** The biggest gaps are seller-specific behavior, budget sensitivity, category seasonality, and situations where short-term momentum looks strong but may not be durable.


## Red-Team Findings

My partner ran a **🎯 Confident Hallucination** attack: My partner asked what happens when a product shows strong short-term sales momentum, but stock is limited and the suggested CPC would push the seller toward unusually high spend. The concern was that the AI might still present this as a strong recommendation because the recent sales signal looks attractive.

**Worst miss they found that I'd missed:** The worst miss is that the AI may over-trust short-term performance signals and produce a confident recommendation, even when stock risk and spend risk should clearly reduce confidence. In that case, the seller could overspend on a campaign that is not actually a strong candidate.

**Severity:** High

**New gold row I'm adding to close the gap:** Input: Product shows strong short-term sales momentum, but stock is limited and the recommended CPC would push the seller toward unusually high spend.
Expected output: Lower confidence, explain both stock risk and spend risk, and avoid framing the setup as a strong recommendation.
Edge case: Y
Judge type: rule + LLM
