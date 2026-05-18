# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Seller approvals, edits, overrides, rejected recommendations, and post-campaign performance signals such as clicks, conversion, ROAS, CPC efficiency, and sales uplift. | Improved future recommendations for product selection, CPC, budget, duration, and confidence calibration. | Y | broken |
| Cross-Domain Transfer | Category-level campaign patterns, product performance signals, pricing behavior, stock risk, and CPC outcomes across similar product groups. | Better recommendations for adjacent categories or similar product types, especially when a seller has limited campaign history. | Y | missing |
| Network Intelligence | Aggregated campaign outcomes from many sellers, including accepted recommendations, edited CPCs, budget changes, category benchmarks, and performance results. | Marketplace-level benchmarks that improve individual seller recommendations while protecting seller-level privacy. | Y | broken |

**Broken loop identified by partner:** Recursive Learning — seller corrections and campaign outcomes do not reliably flow back into the recommendation system yet.
**Fix plan:** Create a feedback pipeline that captures seller approvals, edits, overrides, rejected recommendations, and post-campaign performance. Review these signals weekly, add repeated failure patterns to the golden dataset, and use them to improve recommendation rules, confidence calibration, and model evaluation.

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

**How knowledge flows:** Campaign performance data, product funnel metrics, seller edits, category benchmarks, stock signals, pricing data, and ad spend outcomes should flow into the recommendation system. Product, ads, data, and seller-facing teams should use the same feedback view to understand where recommendations work and where they fail.

**Where it silos:** Seller feedback, manual edits, support insights, and post-campaign learnings can stay separated across product analytics, ad reporting, seller support, and data teams. If these signals are not connected, the AI may keep generating recommendations without learning from real seller behavior.

<!-- Governance Policy — Sponsored Product One Click Setup -->

## Governance Policy

**Scope:** This policy covers the AI-assisted One Click campaign setup flow for Sponsored Product Ads. It includes product selection recommendations, suggested CPC, daily budget, campaign duration, confidence messaging, and seller-facing explanations.

It does not cover fully autThis policy covers the AI-assisted One Click campaign setup flow for Sponsored Product Ads. It includes product selection recommendations, suggested CPC, daily budget, campaign duration, confidence messaging, and seller-facing explanations.

It does not cover fully autonomous campaign optimization, automatic bid changes after launch, or campaign creation without seller approval.onomous campaign optimization, automatic bid changes after launch, or campaign creation without seller approval.

**Autonomy boundaries:** The AI can analyze product and campaign signals, recommend a product to advertise, suggest CPC, daily budget, and campaign duration, generate a seller-facing explanation, assign a confidence level, and flag risk drivers such as low stock, weak conversion, unstable demand, or high spend risk. — auto. Seller approval is required before any campaign is created or launched. Seller review is also required when the recommendation has low confidence, includes high spend risk, includes stock risk, or contains conflicting product signals. Sellers must be able to edit CPC, budget, and duration before approval. — human approval required. The system must never launch a campaign without seller approval, increase budget or CPC after launch without approval, hide material risk signals, present low-confidence setups as strong recommendations, or use seller-level data for external model training without permission. — never auto.

**Escalation triggers:** Escalation is required when confidence is below 50%, when the suggested setup includes unusually high spend, when stock risk is material, when product signals conflict, or when the recommendation repeatedly gets edited or rejected by sellers. Low-confidence recommendations should move to seller review, while repeated high-risk patterns should be reviewed by the product or ads team.

**Audit cadence:** _(not set)_

**Regulatory exposure (EU AI Act / other):** Risk tier: Limited

The system recommends advertising campaign setup decisions but does not make hiring, credit, medical, legal, or eligibility decisions. The main risks are financial impact on sellers, unfair or overly aggressive recommendations, data privacy, and misleading confidence. Controls include seller approval before launch, editable recommendations, confidence tiers, golden dataset evaluation, audit logs, and restrictions on external use of seller-level data.. Risk tier: limited.

## Agent Topology

Current agent status: recommendation assistant, not autonomous agent.

Agent: One Click Recommendation Assistant
Can do: analyze product signals, recommend product, CPC, budget, duration, explain rationale, show confidence, and flag risks.
Cannot do: launch campaigns without seller approval, change bids or budgets after approval, access unrelated seller data, or train external models on seller-level data.
Approval owner: seller for campaign launch; product/ads team for policy changes and new automation capabilities.
Logs: all recommendations, confidence scores, seller edits, approvals, and overrides should be logged for audit and evaluation.

## Shadow AI Audit
Shadow AI Audit (user-side) — Module 5

## Discover — User-Side Workarounds
- Sellers export product performance data and ask ChatGPT which products they should advertise. | source: Support ticket | signal: Capability gap | freq: M | spend: $20/mo | decision: Build
- Sellers use ChatGPT or spreadsheet AI to estimate CPC and daily budget before creating a campaign. | source: User interview | signal: Workflow gap | freq: H | spend: $20/mo | decision: Build
- Seller-facing teams use personal AI tools to draft campaign recommendations for sellers. | source: Other | signal: Workflow gap | freq: M | spend: $20/mo | decision: Build
- Sellers use external AI ad tools to compare marketplace ad performance and decide where to allocate spend. | source: User interview | signal: Capability gap | freq: L | spend: $50/mo | decision: Partner
- Sellers paste campaign results into ChatGPT to understand why performance was weak and what to change next. | source: Support ticket | signal: Trust gap | freq: M | spend: $20/mo | decision: Build

## Pattern Assessment
- Workarounds found: 5
- Build candidates: 4
- Partner candidates: 1
- Ignore decisions: 0
- Adjacent spend: $130/mo
- Dominant signal: Capability gap

## Action Plan
### Build
Product selection recommendation from exported or platform-native product performance data.
CPC and daily budget recommendation inside the campaign setup flow.
AI-generated campaign performance explanation after launch.
Internal seller-facing recommendation support should move into the official One Click workflow instead of personal AI tools.

### Partner
Explore partnership or integration opportunities for broader cross-marketplace ad planning tools, but keep Hepsiburada-specific Sponsored Product recommendations native because they depend on closed-loop marketplace data.

### Ignore + Monitor
Ignore generic AI usage for rewriting seller-facing text unless it directly affects campaign setup, spend decisions, or seller trust. Monitor external AI ad planning tools to understand whether they start replacing marketplace-native campaign workflows.

## Roadmap Brief
Based on your audit: 5 user-side workarounds discovered.
Decisions: 4 build · 1 partner · 0 ignore · 0 TBD.
Estimated adjacent spend: $130/mo across surveyed users.
Dominant signal: Capability gap.

Recommended next step: Capability gaps dominate — users want something your product does not do. Strongest near-term move is building one or two of these natively before a competitor does.

Sequence the Build column by frequency × strategic relevance. Confirm Partner candidates with the external tools' partnership teams. Re-run this audit each quarter — workarounds shift fast.
