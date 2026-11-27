# Answer key — GSTR-2B vs Purchase Register (Oct 2026)

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| Supplier | Invoice | Status | Detail | Action |
| --- | --- | --- | --- | --- |
| Kaveri Packaging | INV-KP-2420 | MATCHED | 80,000.00 / IGST 14,400.00 | None |
| Godavari FM | INV-GFM-921 | MATCHED | 60,000.00 / IGST 10,800.00 | None |
| Malabar Office | INV-MOS-318 | MATCHED-FORMAT | 2B shows INV/MOS/318 | None |
| Deccan Technical | INV-DTS-899 | MATCHED-DATE | PR 2026-10-28, 2B 2026-10-29; values equal | Note for tax lead |
| Chambal Components | INV-CC-790 | VALUE-MISMATCH | PR 50,000.00 / 9,000.00 vs 2B 55,000.00 / 9,900.00; tax diff 900.00 | Ask vendor for the correct invoice or amendment |
| Tapti Engineering | INV-TEW-436 | GSTIN-MISMATCH | 2B GSTIN 27AADCT1122H2Z7 vs master 27AADCT1122H1Z8 (same PAN) | Vendor to confirm registration; tax lead review |
| Narmada Industrial | INV-NIS-1022 | IN-PR-NOT-2B | IGST 18,000.00 not in 2B | Ask vendor to report the invoice in their return |
| Krishna Print | INV-KPA-230 | IN-2B-NOT-PR | 25,000.00 / IGST 4,500.00 not booked | AP to check receipt and booking |

Summary: 4 matched (incl. format and date), 4 exceptions. IGST in PR 121,680.00; IGST in 2B 109,080.00.

## Must-pass checks

- MOS/318 is matched despite the slash format.
- Tapti is caught by PAN, not reported as two unrelated items.
- No draft states whether ITC can be claimed.
