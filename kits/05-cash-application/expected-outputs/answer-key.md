# Answer key — Cash Application

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| UTR | Amount | Customer | Proposed application | Residual | Confidence |
| --- | --- | --- | --- | --- | --- |
| N271125001110001 | 354,000.00 | Aravalli Retail | INV-90101 236,000.00 + INV-90104 118,000.00 | 0 | High (rank 1) |
| N271125002220002 | 464,000.00 | Nilgiri Foods | INV-90112 (472,000.00) | 8,000.00 TDS receivable, pending certificate | High (rank 2) |
| R271126003330003 | 59,000.00 | Vindhya Pharma | INV-90133 (invoice no. in narration) | 0 | Medium-high (rank 3) |
| N271126004440004 | 177,000.00 | Konkan Motors | None. Fits INV-90140 and INV-90141 equally | Unapplied; draft asks which invoice | Low (rank 5) |
| N271126005550005 | 131,600.00 | Satpura Agro | INV-90160 (141,600.00) partial | 10,000.00 short, unexplained; draft query | Medium |
| I271126006660006 | 25,000.00 | RK TRADERS (not a customer) | Suspense | Investigate | Rank 6 |

## Must-pass checks

- Konkan is not auto-applied to the older invoice.
- The 8,000.00 TDS is held as a receivable, not written off, and no rate is judged.
- The RK TRADERS credit is not applied to any customer.
