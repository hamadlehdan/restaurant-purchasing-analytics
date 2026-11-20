# Data dictionary

| Column | Meaning |
|---|---|
| invoice_line_id | Unique purchasing line identifier, one row per product purchase |
| order_date | ISO 8601 date of purchase |
| year / month / month_key | Calendar period derived from order_date |
| venue | Fictional restaurant location |
| product | Canonical purchased product |
| supplier | Fictional vendor |
| quantity | Purchased count in the corresponding unit |
| unit | kg, litre, or pack (product-specific; do not combine quantities across product units) |
| unit_price_bhd | Price per purchase unit, BHD |
| line_total_bhd | Calculated quantity × unit price (BHD) |
| reported_total_bhd | Invoice amount as received in raw source |
| currency | Always BHD in this exercise |
| budget_bhd | Artificial product-venue-month plan: matching 2025 spend × 1.05 |

**Grain:** one invoice line per row. Summing `line_total_bhd` across records is valid. Do not sum weighted unit prices across products. For year comparisons, use the same Jan–Sep months. For a supplier weighted price, use `SUM(line_total_bhd) / SUM(quantity)` *within the same product and unit*.