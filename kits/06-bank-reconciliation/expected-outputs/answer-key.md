# Answer key — Bank Reconciliation

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

Account ending 4321, 2026-11-01 to 2026-11-26. Opening balance both sides 5,000,000.00.

| Line | Amount |
| --- | --- |
| Balance per bank statement | 5,434,461.00 |
| Less: outstanding cheque 004512 (rent, 2026-11-18) | −236,000.00 |
| Add: deposit in transit, cheque 220118 (2026-11-26) | +118,000.00 |
| **Adjusted bank balance** | **5,316,461.00** |
| Balance per GL cash book | 5,253,680.00 |
| Add: reverse duplicate posting 100000207 (Godavari, N271124009990009) | +70,800.00 |
| Less: electricity keyed as 45,120.00, bank 45,210.00 (difference) | −90.00 |
| Less: bank charges 2026-11-15 | −1,180.00 |
| Add: sweep interest 2026-11-25 | +3,250.00 |
| Less: unknown NACH debit 2026-11-21 (pending investigation) | −9,999.00 |
| **Adjusted book balance** | **5,316,461.00** |

Adjusted balances agree.

Note: the electricity line is −90.00 to the book (an extra 90.00 paid out than booked). Verify against the bill before correcting.

## Proposed JEs (drafts)

1. Reverse 100000207 duplicate: Dr Bank 70,800.00 / Cr Vendor Godavari (after AP confirms one payment only).
2. Electricity correction: Dr Electricity expense 90.00 / Cr Bank 90.00 (after checking the bill).
3. Bank charges: Dr Bank charges 1,180.00 / Cr Bank (GST split per tax team).
4. Interest: Dr Bank 3,250.00 / Cr Interest income.
5. NACH 9,999.00: **no JE**. Escalate to treasury; ask the bank for the mandate details.

## Must-pass checks

- The NACH debit is escalated, not expensed.
- The duplicate is found by the repeated UTR.
- The recon ties to the rupee.
