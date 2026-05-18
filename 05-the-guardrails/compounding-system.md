# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Seller approvals, edits, overrides, rejected recommendations, and post-campaign performance signals such as clicks, conversion, ROAS, CPC efficiency, and sales uplift. | Improved future recommendations for product selection, CPC, budget, duration, and confidence calibration. | Y | broken |
| Cross-Domain Transfer | Category-level campaign patterns, product performance signals, pricing behavior, stock risk, and CPC outcomes across similar product groups. | Better recommendations for adjacent categories or similar product types, especially when a seller has limited campaign history. | Y | missing |
| Network Intelligence | Aggregated campaign outcomes from many sellers, including accepted recommendations, edited CPCs, budget changes, category benchmarks, and performance results. | Marketplace-level benchmarks that improve individual seller recommendations while protecting seller-level privacy. | Y | broken |

**Broken loop identified by partner:**  
Recursive Learning — seller corrections and campaign outcomes do not reliably flow back into the recommendation system yet.

**Fix plan:**  
Create a feedback pipeline that captures seller approvals, edits, overrides, rejected recommendations, and post-campaign performance. Review these signals weekly, add repeated failure patterns to the golden dataset, and use them to improve recommendation rules, confidence calibration, and model evaluation.

## Context Connectivity

**How knowledge flows:**  
Campaign performance data, product funnel metrics, seller edits, category benchmarks, stock signals, pricing data, and ad spend outcomes should flow into the recommendation system. Product, ads, data, and seller-facing teams should use the same feedback view to understand where recommendations work and where they fail.

**Where it silos:**  
Seller feedback, manual edits, support insights, and post-campaign learnings can stay separated across product analytics, ad reporting, seller support, and data teams. If these signals are not connected, the AI may keep generating recommendations without learning from real seller behavior.

## Governance Policy

**Scope:**  
This policy covers the AI-assisted One Click campaign setup flow for Sponsored Product Ads. It includes product selection recommendations, suggested CPC, daily budget, campaign duration, confidence messaging, and seller-facing explanations.

It does not cover fully autonomous campaign optimization, automatic bid changes after launch, or campaign creation without seller approval.

**Autonomy boundaries:**  

- **Auto:** The AI can analyze product and campaign signals, recommend a product to advertise, suggest CPC, daily budget, and campaign duration, generate a seller-facing explanation, assign a confidence level, and flag risk drivers such as low stock, weak conversion, unstable demand, or high spend risk.
- **Human approval required:** Seller approval is required before any campaign is created or launched. Seller review is also required when the recommendation has low confidence, includes high spend risk, includes stock risk, or contains conflicting product signals. Sellers must be able to edit CPC, budget, and duration before approval.
- **Never auto:** The system must never launch a campaign without seller approval, increase budget or CPC after launch without approval, hide material risk signals, present low-confidence setups as strong recommendations, or use seller-level data for external model training without permission.

**Escalation triggers:**  
Escalation is required when confidence is below 50%, when the suggested setup includes unusually high spend, when stock risk is material, when product signals conflict, or when the recommendation repeatedly gets edited or rejected by sellers. Low-confidence recommendations should move to seller review, while repeated high-risk patterns should be reviewed by the product or ads team.

**Audit cadence:**  
The product manager owns the governance policy and reviews it monthly with the ads, data, and engineering teams. The golden dataset is reviewed weekly during early rollout and monthly after stabilization. High-risk recommendation patterns, seller overrides, and low-confidence cases are reviewed as part of the golden dataset audit.

**Regulatory exposure (EU AI Act / other):**  
Risk tier: Limited

The system recommends advertising campaign setup decisions but does not make hiring, credit, medical, legal, or eligibility decisions. The main risks are financial impact on sellers, unfair or overly aggressive recommendations, data privacy, and misleading confidence. Controls include seller approval before launch, editable recommendations, confidence tiers, golden dataset evaluation, audit logs, and restrictions on external use of seller-level data.

## Agent Topology

Current agent status: recommendation assistant, not autonomous agent.

| Agent | Can Do | Cannot Do | Approval Owner | Logs |
|-------|--------|-----------|----------------|------|
| One Click Recommendation Assistant | Analyze product signals, recommend product, CPC, budget, and duration, explain rationale, show confidence, and flag risks. | Launch campaigns without seller approval, change bids or budgets after approval, access unrelated seller data, or train external models on seller-level data. | Seller for campaign launch; product/ads team for policy changes and new automation capabilities. | Recommendations, confidence scores, seller edits, approvals, and overrides should be logged for audit and evaluation. |

## Shadow AI Audit

| Tool / Workaround | Owner | Risk Level | Decision |
|-------------------|-------|-----------|----------|
| Sellers export product performance data and ask ChatGPT which products they should advertise. | Sellers | M | govern / build |
| Sellers use ChatGPT or spreadsheet AI to estimate CPC and daily budget before creating a campaign. | Sellers | H | govern / build |
| Seller-facing teams use personal AI tools to draft campaign recommendations for sellers. | Seller-facing teams | H | govern / build |
| Sellers use external AI ad tools to compare marketplace ad performance and decide where to allocate spend. | Sellers | M | govern / partner |
| Sellers paste campaign results into ChatGPT to understand why performance was weak and what to change next. | Sellers | M | govern / build |

**Total tools found:** 5

**Tools after triage:**  
4 build candidates, 1 partner candidate, 0 ignore

**Estimated hidden spend:**  
Approximately $130/month across surveyed or assumed users

**Pattern assessment:**  
The audit found several user-side AI workarounds around campaign setup, especially product selection, CPC and budget planning, and post-campaign performance explanation. The dominant signal is a capability gap: users want help making better ad decisions, and some of that work is happening outside the governed product workflow.

**Build:**  
Product selection recommendation from exported or platform-native product performance data.  
CPC and daily budget recommendation inside the campaign setup flow.  
AI-generated campaign performance explanation after launch.  
Internal seller-facing recommendation support should move into the official One Click workflow instead of personal AI tools.

**Partner:**  
Explore partnership or integration opportunities for broader cross-marketplace ad planning tools, but keep Hepsiburada-specific Sponsored Product recommendations native because they depend on closed-loop marketplace data.

**Ignore + Monitor:**  
Ignore generic AI usage for rewriting seller-facing text unless it directly affects campaign setup, spend decisions, or seller trust. Monitor external AI ad planning tools to understand whether they start replacing marketplace-native campaign workflows.

**Roadmap brief:**  
The audit found 5 user-side AI workarounds: 4 build candidates and 1 partner candidate. The strongest near-term move is to build the workflows that directly affect seller spend decisions inside Sponsored Product Ads: product selection, CPC and budget recommendation, and post-campaign explanation. Cross-marketplace planning should be monitored as a partner opportunity, but Hepsiburada-native recommendations should stay in-product because they depend on proprietary marketplace signals. Re-run this audit quarterly, because AI workarounds can shift quickly.
