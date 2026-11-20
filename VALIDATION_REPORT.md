# Validation report — simulated purchases

| Check | Result |
|---|---:|
| Raw records preserved | 1,363 |
| Expected source invoice lines before injected duplicates | 1,344 |
| Duplicate rows removed | 19 |
| Invalid nonduplicate rows quarantined | 9 |
| Clean usable rows | 1,335 |
| Canonical field corrections/recoveries logged | 172 |
| Duplicate IDs remaining | 0 |
| Nonpositive quantities remaining | 0 |
| Unreconciled line totals remaining | 0 |
| Unknown venues/products remaining | 0 |

**Disposition:** The cleaned data passes the programmed transaction-level integrity checks. However, 9 nonduplicate invoice lines remain excluded pending source verification, and the budgets are fictional assumptions. This is appropriate for a labelled portfolio demonstration; not appropriate for an operational financial close.

**Reconciliation:** raw unique IDs = 1344; clean + nonduplicate quarantine = 1344; raw = clean + duplicate quarantine + nonduplicate quarantine = 1363.