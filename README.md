# E-Commerce Profitability Diagnostic

**Revenue held steady all year. Profit nearly disappeared. This project finds out why.**

---

## Overview
 An 18,000-order e-commerce dataset (Sept 2025–Aug 2026) looked healthy on the surface — revenue stayed strong, month after month. But contribution profit told a different story, collapsing to under 1% margin for the year. This project traces that gap back to its root causes using a full Python → SQL → Power BI pipeline.

**The question:** revenue looks fine, so where did the profit go?

---

## Dataset
| | |
|---|---|
| **Source** | E-commerce transaction data (Orders, Customers, Products, Marketing, Targets) |
| **Size** | 18,000 rows |
| **Period** | Sept 2025 – Aug 2026 |
| **Format** | Excel / CSV |

**Data quality:** No nulls, no duplicates, no broken references — every formula checked out. A clean dataset, which meant the profit collapse was real, not a data error.

---

## Methodology
**Python** → cleaned and validated the raw data, then rebuilt it as a proper star schema.

**MySQL** → independently verified every finding with SQL — joins, CTEs, and window functions (`LAG`, `RANK`, `NTILE`, running totals) — cross-checked against the Python results.

**Power BI** → built the final diagnostic dashboard on the verified model, with 12 custom DAX measures for margin, discount rate, return rate, and channel ROI.

---

**Dashboard Features**

* KPI cards — Contribution Profit, Realized Revenue, Return Rate %, Margin %

* Time trend — revenue vs. contribution profit by month

* Category breakdown — profit by product category

* Channel efficiency — profit per marketing naira by acquisition channel

* Regional drill-down — profit by customer segment and region

* Discount & return trend — discount rate and return rate by month


**Key Insights**

* Margin collapsed from 13.2% to under 1% for the year, even though revenue held steady at ₦200–300M a month

* Average discount rate roughly doubled, from ~10% to ~22-23%, starting Nov 2025, and never came back down — company-wide, across every channel and category

* Electronics alone erases ₦100M in profit; its 22% base margin can't absorb the discount rate every other category tolerates fine

* Marketplace and Instagram lose money on every naira of marketing spend; Website is the only channel with strong, reliable ROI

* Just 6.9% of orders are returned, but they wipe out 87% of the profit the remaining orders generate

* Delta is the only region operating at a loss, despite solid revenue (₦198M) — the cause traces specifically to its Consumer segment, where the return rate runs a full point above every other region's consumer base


## Dashboard
![Dashboard Preview](dashboard_preview.png)

Power BI · Star-schema model (1 fact table + 5 dimensions)· KPI cards, trend lines, category and channel breakdowns, RFM customer segmentation, and a region-level profit/loss view.

---

**Recommendations**

* Cap discount rate by category — thin-margin categories like Electronics need a lower ceiling than high-margin ones like Fashion

* Reassess spend on Marketplace and Instagram, or renegotiate their cost structure, given consistently negative ROI

* Investigate the Nov 2025 discount policy change specifically — that's the exact point where company-wide margin turned negative

* Audit return drivers by channel — Instagram and Marketplace also carry the highest return rates

* Investigate Delta's Consumer segment specifically — elevated returns there, not category mix or discounting, are driving the region's loss

**Limitations**

* No product-level detail on why individual SKUs get returned (defect, sizing, wrong item, changed mind) — return rate is visible, root cause per return is not

* Revenue targets provided in the source data appear mis-scaled relative to actual revenue every month, so the Targets table was treated cautiously rather than as a reliable benchmark

* Region and customer-segment sample sizes vary — Delta's finding is based on its full order volume for the year, but smaller regions in general should be read with that in mind

---

## Expected Impact
Turns a vague "profit feels low" concern into a specific, evidenced diagnosis — pinpointing the exact lever (discounting), category (Electronics), channels (Marketplace, Instagram), and region (Delta) driving the gap between healthy revenue and near-zero profit.

---

## Tools
`Python` `Pandas` `SciPy` `MySQL` `Power BI` `DAX`
