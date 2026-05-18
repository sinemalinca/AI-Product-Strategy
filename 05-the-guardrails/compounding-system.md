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

## Governance Policy

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
