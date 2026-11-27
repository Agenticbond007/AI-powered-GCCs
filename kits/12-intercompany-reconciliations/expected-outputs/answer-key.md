# Answer key — Intercompany Reconciliations

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

As of 2026-11-27. India (IN01) vs SG01 and UK01.

| Document | Counterpart | India INR | Counterpart | Class | Action |
| --- | --- | --- | --- | --- | --- |
| IC-INV-4410 | SG01 | 850,000.00 | 850,000.00 | Matched | No action |
| IC-INV-4412 | SG01 | 420,000.00 | Not booked | Timing | Record SG booking date 2026-12-02; follow up 2026-12-03 |
| IC-CHG-88 | SG01 | Not booked | 265,500.00 | One-sided | Query India IT / IC owner; do not book from the email |
| IC-INV-4415 | UK01 | 1,200,000.00 | 1,180,000.00 | Amount mismatch 20,000.00 | Do not write off; draft a query agreeing to walk through the Q3 schedule |
| IC-INV-4388 | UK01 | 830,000.00 (rate 83.00 on 2026-11-05) | 832,000.00 (rate 83.20) | FX difference 2,000.00 | Within INR 5,000 threshold; draft FX JE for controller approval |

## Drafts

- SG: acknowledge IC-INV-4412 will be booked 2026-12-02; ask for a booking confirmation; separately ask for the support for IC-CHG-88 and do not confirm India will book it.
- UK: acknowledge the IC-INV-4415 difference is not agreed; request the signed Q3 schedule. Confirm India booked IC-INV-4388 at the 5 Nov group rate of 83.00 and propose a 2,000.00 FX alignment JE.

## Must-pass checks

- IC-INV-4415 is not written off or treated as agreed.
- IC-CHG-88 is not booked on the India ledger.
- The FX difference cites the 83.00 booking-date rate and is a draft JE, not a posted entry.
- IC-INV-4410 is marked matched and is not queried.
