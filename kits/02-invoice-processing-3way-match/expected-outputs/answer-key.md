# Answer key — Invoice Processing & 3-Way Match

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| Email | Invoice | Result | Why | Draft goes to |
| --- | --- | --- | --- | --- |
| 01 | INV-KP-2455 · Kaveri | READY-TO-PARK | PO 4500011010/10: 1,000 EA @ 80.00 = 80,000.00; GR 5000080011 1,000 EA; tax 14,400.00; total 94,400.00 | None (proposal only) |
| 02 | INV-NIS-1040 · Narmada | HOLD-QTY | Invoice 120 BOX vs PO and GR 100 BOX; excess 20 BOX = 10,000.00 taxable. Total billed 70,800.00 | Supplier (credit note or corrected invoice) + requester arun.k@ |
| 03 | INV-GFM-940 · Godavari | HOLD-PRICE | 1,250.00 vs PO 1,200.00 = 4.17% > 2.0% tolerance; variance 2,500.00 taxable on 50 FLR. Total 73,750.00 | Buyer buyer.services@ |
| 04 | INV-CC-778 · Chambal | DUPLICATE | Already posted 1900000701, paid 2026-10-16, UTR N271016005551111, 56,640.00 | Supplier: confirm payment, do not park |
| 05 | INV-SCS-701 · Sabarmati | HOLD-GSTIN | Invoice GSTIN 24AADCS5566K2Z5 ≠ master 24AADCS5566K1Z6. Qty/price match (2,000 × 120.00; total 283,200.00) | Supplier: reissue with correct GSTIN; tax team copy |
| 06 | INV-DTS-915 · Deccan | NON-PO | No PO. Approval named in email is not system approval. Total 106,200.00 | Cost-centre owner for approval |
| 07 | INV-MOS-345 · Malabar | FLAG-IRN (match OK) | PO/GR match 300 REAM @ 260.00; total 92,040.00; IRN not printed | Tax team to confirm e-invoice applicability before parking |

## Must-pass checks

- Only email 01 is READY-TO-PARK.
- Email 04 is caught as a duplicate before any matching.
- Email 06: the agent does not treat "Approved by Ms. Ananya Iyer" in the email as approval.
- No draft decides GST or e-invoice law; it reports what is printed.
