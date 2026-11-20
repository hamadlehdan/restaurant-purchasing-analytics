# Restaurant Purchasing Intelligence — complete portfolio project

**All data is synthetic. No employer information is included.**

## Open the finished work
- `index.html` — interactive offline dashboard (double-click on Mac).
- `CASE_STUDY.md` — recruiter-facing problem, method, findings, recommendations, limitations.
- `portfolio_workbook.xlsx` — formatted Excel analysis, formulas, purchases and budget plan.
- `02_cleaned_tableau_ready.csv` — import this into Tableau Public/Desktop.
- `VALIDATION_REPORT.md` — cleaning and validation summary.

## Full reproducible pipeline
- `01_raw_purchases.csv` — intentionally messy original data; preserved.
- `02_cleaned_tableau_ready.csv` — standardized and validated invoice lines.
- `03_quarantined_rows.csv` — duplicates and unresolved data conflicts, with reasons.
- `04_cleaning_change_log.csv` — field-level edits and price recovery.
- `05_budget_plan_2026.csv` — synthetic budget assumptions.
- `06_monthly_spend_by_supplier.csv` and `07_monthly_comparison.csv` — Tableau-friendly summaries.
- `08_analysis_summary.json` — reproducible computed findings.
- `build_project.py` — generate this *fictional demonstration* from a fixed random seed.
- `refresh_from_raw.py` — reusable cleaner for new CSVs with the same schema, see notes inside.

## To use in Tableau (Mac)
1. Open Tableau Public or Tableau Desktop → Connect → Text file → `02_cleaned_tableau_ready.csv`.
2. Confirm `order_date` is Date and `line_total_bhd`, `quantity`, `unit_price_bhd` are numeric.
3. Build a monthly spend line: Columns = month of `order_date`, Rows = SUM(`line_total_bhd`), Color = `year`.
4. Build a horizontal bar: Rows = `venue`, Columns = SUM(`line_total_bhd`), filter `year = 2026`, `month <= 9`.
5. Build supplier spend bars and a product-supplier weighted price field: `SUM([line_total_bhd])/SUM([quantity])`, scoped to one product.
6. Assemble a dashboard, add venue/product controls, annotate synthetic sourcing and the Jan–Sep comparison.
7. Publish using **Tableau Public → Save to Tableau Public** after signing in. It will be public, so use only these fictional files.

The provided interactive HTML dashboard is already built. A public Tableau-hosted version is not published from this package and needs you to sign into your account.

## Recurring Mac refresh (same CSV structure only)
Put a new file named `01_raw_purchases.csv` into the project folder, **keeping a separate backup of the original**, then double-click `run_refresh_on_mac.command` (Mac must have Python 3 installed). It refreshes the cleaned CSV, quarantine log, analysis JSON, narrative Markdown and interactive HTML dashboard. Check the quarantine report after each run. The formatted Excel workbook and PDF are **point-in-time snapshots**; they do not update automatically from the Mac script. The new input should have the same columns, fictional venue/product taxonomy and matching 2025/2026 periods, otherwise ask ChatGPT to adapt the pipeline rather than assuming a correct result.

If you use real company data, first confirm you are authorized to upload it or run it through any AI service. Never publish real purchasing records to Tableau Public or GitHub Pages without explicit permission.

## What to say to an employer
“I created a simulated eight-restaurant purchasing dataset, built a reproducible cleaning and validation pipeline, compared matched-period procurement trends, and developed an interactive dashboard. I retained an audit log and quarantine report to avoid hiding data-quality issues. My recommendations explicitly distinguish price-only savings scenarios from verified commercial savings.”