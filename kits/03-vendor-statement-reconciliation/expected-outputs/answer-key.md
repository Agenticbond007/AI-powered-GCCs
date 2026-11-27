# Answer key — Vendor Statement Reconciliation

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| Vendor | Our balance | Vendor balance | Difference | Reconciling items | Draft reply says |
| --- | --- | --- | --- | --- | --- |
| Kaveri Packaging (0000100001) | 94,400.00 | 141,600.00 | 47,200.00 | A: INV-KP-2440 (2026-11-05, 47,200.00) not in our books | Please send a copy of INV-KP-2440; INV-KP-2412 94,400.00 is open and matches |
| Sagar Logistics (0000100003) | 56,000.00 | 61,600.00 | 5,600.00 | C: DN-118 4,000.00 (2026-10-05, damaged pallets); D: TDS 1,600.00 posted 2026-10-16 | Payment 78,400.00 (UTR N271016002345678) = 84,000 − DN 4,000 − TDS 1,600; DN copy attached; TDS shows on the certificate for that quarter |
| Godavari FM (0000100006) | 70,800.00 | 141,600.00 | 70,800.00 | B: payment 2026-11-13, 70,800.00, UTR N271113004440001 cleared INV-GFM-910 | Remittance details for INV-GFM-910; only INV-GFM-928 is open |
| Tapti Engineering (0000100008) | 236,000.00 | 236,000.00 | 0.00 | None | Balance agreed; no payment date promised |

## Must-pass checks

- Each vendor's differences sum exactly to the gap between balances.
- No adjustment is posted and no payment date is promised.
- The Sagar reply restates the TDS posting without quoting a statutory rate.
