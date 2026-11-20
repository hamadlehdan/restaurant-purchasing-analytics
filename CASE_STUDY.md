# Restaurant Purchasing Intelligence — portfolio case study

> **SIMULATED CASE STUDY.** Every venue, supplier, purchase, price and budget in this project was generated synthetically. It is **not** based on any employer's confidential data or real purchasing records.

## Business question
How could a multi-venue hospitality operator monitor purchasing cost increases, identify supplier price differences, and decide where to investigate procurement savings?

## Context and scope
Eight fictional restaurants, eight recurring purchased products, five fictional suppliers. Transaction-grain purchases cover January 2025–September 2026. For fair year-on-year analysis, all comparisons here use **January–September of each year**.

## Data pipeline
- Preserved the untouched source in `01_raw_purchases.csv` (1,363 rows).
- Standardized venue, product, supplier and date text; recovered a missing unit price only when the invoice total and quantity independently reconciled.
- Identified and removed **19** duplicate invoice-line IDs.
- Quarantined **9** nonduplicate rows with invalid quantities or totals, leaving **1,335** validated records. Rejected records remain auditable in `03_quarantined_rows.csv`.
- Logged **172** field-level transformations in `04_cleaning_change_log.csv`.
- Verified positive quantities, unique transaction IDs, supported categories, and exact quantity × price line-total reconciliation.

## Headline analysis — simulated outcomes
| Metric | Result |
|---|---:|
| 2026 Jan–Sep purchasing | BD 122,314.67 |
| 2025 Jan–Sep purchasing | BD 117,181.96 |
| Year-over-year difference | +4.38% |
| Fictional 2026 budget | BD 123,041.36 |
| Budget variance (positive = over budget) | BD -726.69 (-0.59%) |
| Indicative supplier-switch price opportunity | BD 5,631.25 (scenario only) |
| Largest supplier share | Green Basket (24.4%) |

## Findings
**1. Purchasing cost is changing.** Like-for-like Jan–Sep purchasing spend changed +4.38% year over year. This is *spend*, not inflation: it combines quantity, product mix, and unit price changes. Investigate quantities and weighted unit prices separately before attributing causes.

**2. Fictional plan variance.** 2026 purchasing expenditure is BD 726.69 below the assumed plan. The benchmark is illustrative: 2025 same-month product spend plus 5%, rather than an approved operating budget.

**3. Supplier price benchmark (not a guaranteed saving).** For equivalent product labels, the largest potential price gaps were:
- **Coffee beans**: Harbor Supply averaged BD 9.66/unit vs Northline Wholesale at BD 8.53/unit; modelled price-only opportunity BD 1,545.99.
- **Chicken breast**: Green Basket averaged BD 2.55/unit vs Eastbay Foods at BD 2.35/unit; modelled price-only opportunity BD 1,434.73.
- **Napkins**: Harbor Supply averaged BD 1.14/unit vs Northline Wholesale at BD 1.01/unit; modelled price-only opportunity BD 613.73.

These are *observational* comparisons. The records do not prove that product quality, supplier capacity, contract terms, service level or volume discounts are identical.

## Recommendations to a fictional operations manager
1. **Validate invoice quality first:** require unique invoice-line IDs, positive quantities, normalized supplier names, and invoice total reconciliation before monthly reporting.
2. **Run a supplier quote exercise:** start with the three largest modelled price opportunities; compare equivalent product specifications, delivery terms and minimum quantities.
3. **Monitor price and volume separately:** track weighted unit prices *and* units ordered, not only total spend, to distinguish cost movement from purchasing volume.
4. **Review the budget variance monthly:** flag a product-venue combination for investigation when the variance exceeds an agreed threshold; do not treat the fictional 5% uplift as an operational target.

## Dashboard design
- KPI cards: current year spend, prior-year change, budget variance and illustrative supplier-price opportunity.
- Monthly comparison: 2025 vs 2026 Jan–Sep trends.
- Venues: cost concentration across eight restaurants.
- Suppliers: share of 2026 spend.
- Product-price benchmark: supplier-weighted average price and illustrative difference.
- Interactions: venue and product filters, clean CSV export, filter reset.

## Limitations
- All data is artificially generated; these results are a **demonstration of an analytical workflow**, not a finding about a real business.
- Spend trends do not establish why costs changed. No sales, covers, purchase order approvals, recipe consumption, supplier quality scores, or waste measures are available.
- Quarantined records reduce reported spend slightly relative to the fabricated ground truth; they should be investigated in a real system, never silently omitted without review.
- The Tableau-ready CSV is supplied, and the interactive HTML dashboard is finished. Publishing in Tableau Public requires a signed-in Tableau account and may require rebuilding the visual sheets there. Do not upload confidential operational data to Tableau Public.

## Reproduction
Run `python3 build_project.py` to regenerate the fictional source, cleaned data, validation report, and summary files. Use `python3 refresh_from_raw.py` to clean a *similarly structured* replacement source without generating new fictional raw data. The downloadable dashboard is stored in `index.html` and works offline.