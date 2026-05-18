# Three-Horizon Roadmap

## Horizon 1 — Ship (0–4 weeks)

| Initiative | Strategy Component | Why it ships now | Confidence |
|---|---|---|---|
| Ship One Click recommendation flow with seller approval | Bet | Core expression of the product thesis and fastest path to learning whether sellers want AI-assisted setup. | H |
| Add editable CPC, daily budget, and campaign duration fields | Contract | Directly supports trust and HITL control without requiring major infrastructure. | H |
| Implement confidence UX states for Recommended, Suggested, and Not Confident | Contract | Critical trust layer already defined in the strategy and feasible with current recommendation logic. | H |
| Run seller validation sprint with interviews and wizard-of-oz testing | Bet | Fastest way to validate trust, usability, and recommendation acceptance before scaling. | H |
| Measure campaign creation uplift and recommendation acceptance rate | Bet | Required to validate whether the core business bet works at all. | H |
| Expand golden dataset from 10 rows to 150+ real recommendation cases | Contract | The reliability target is impossible to defend with the current dataset size. | M |
| Create recommendation quality scorecard for relevance, spend safety, ROAS, stock awareness, and confidence calibration | Contract | Creates an operational definition of “good recommendation” before optimization work begins. | M |
| Track seller approvals, edits, overrides, and rejected recommendations | Moat | Foundational telemetry needed for the future learning loop and recommendation improvement. | H |

## Horizon 2 — Validate (1–3 months)

| Initiative | Strategy Component | Hypothesis | Kill Criteria | Confidence |
|---|---|---|---|---|
| Build feedback pipeline from seller actions and campaign outcomes | Guardrails | Feeding seller behavior and outcomes back into recommendations will improve acceptance and recommendation quality over time. | If recommendation acceptance and quality metrics do not improve after integrating feedback loops by week 8, we stop further pipeline expansion. | M |
| Add post-campaign performance explanation for sellers | Bet | Sellers who understand why outcomes happened will trust AI recommendations more and continue using One Click. | If explained campaigns do not improve repeat One Click usage or seller trust scores by week 6, we stop. | M |
| Build category-level benchmarks for CPC, budget, stock, and conversion patterns | Moat | Marketplace-native benchmarks will improve recommendation quality in ways external AI tools cannot replicate. | If benchmark-driven recommendations do not outperform generic recommendations by week 8, we stop. | M |

## Horizon 3 — Explore (3–6 months)

| Initiative | Strategy Component | What must be true first | Confidence |
|---|---|---|---|
| Explore personalized seller optimization memory | Moat | Seller behavior signals and feedback loops must already produce stable recommendation improvements. | M |
| Explore inventory-aware bidding and seasonal forecasting | Moat | Reliable inventory, pricing, and demand signals must exist with enough historical coverage. | M |
| Explore always-on campaign optimization agent with seller approval boundaries | Guardrails | Sellers must first trust recommendation quality and approval workflows at meaningful scale. | L |
| Monitor cross-marketplace AI ad planning tools for partner opportunities | Guardrails | Clear evidence must emerge that partnership creates distribution or data leverage instead of commoditization risk. | L |

## Unmapped — Cut or Rethink

| Initiative | Why it's unmapped | Recommendation |
|---|---|---|
| None | All initiatives connect to at least one strategy component. | No cuts required from mapping alone. |

## Mapping Disagreements

| Initiative | I mapped to | You'd map to | Why |
|---|---|---|---|
| Add post-campaign performance explanation for sellers | Bet | Contract | This initiative primarily builds seller trust and explainability rather than strengthening the core product thesis itself. |
| Build feedback pipeline from seller actions and campaign outcomes | Guardrails | Moat | The strongest long-term value is the recursive learning loop and defensibility, which is fundamentally moat-building. |
| Monitor cross-marketplace AI ad planning tools for partner opportunities | Guardrails | Moat | This is more about strategic ecosystem positioning and defensive leverage than operational safety boundaries. |

## Roadmap Notes

The roadmap is currently over-indexed on H1 execution, which is appropriate for early validation, but it is still relatively thin on Margin-focused initiatives and medium-term defensibility experiments.

If budget were cut, the H3 bet to protect would be **personalized seller optimization memory**, because it is the clearest path toward a true behavioral data moat that competitors cannot easily copy.

The initiative to cut or deprioritize today is **monitor cross-marketplace AI ad planning tools for partner opportunities**, because it is strategically vague, non-compounding, and less important than building Hepsiburada’s proprietary marketplace-native advantage.
