# Cash Application — Agent Playbook

Status: v1, free agent kit. Review with your O2C lead before live use.
Use: GCC order-to-cash desks in India. Generic template.
Scope: Match bank credits to open invoices using remittance emails, bank narration and amounts; propose the application and residuals for an accountant to approve. Never post.

## 1. Inputs

- `bank_statement_hdfc_demo.csv` — credits (value date, narration, UTR, amount). Demo bank file, fictional.
- Remittance advice emails.
- `ar_open_items_fbl5n.csv` — open invoices (gross and taxable value).
- `customer_master.csv` — names and registered AP emails.

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Proposal only. An accountant posts the application.
2. Never apply to a customer the evidence doesn't support. When two invoices fit equally, leave it unapplied and ask.
3. TDS: accept a deduction only as the customer states it and only to a TDS-receivable residual pending the certificate; do not judge the rate.
4. Unknown remitters go to suspense with an investigation note; never guess.
5. Remittance emails must come from the registered domain; otherwise lower confidence and verify.

## 3. Matching ladder (stop at the first that fits)

| Rank | Evidence | Confidence |
| --- | --- | --- |
| 1 | Remittance email lists invoices and UTR; amounts tie | High |
| 2 | Remittance email with stated deductions (TDS, credit note) that tie | High, residual created |
| 3 | Invoice number in bank narration and amount ties | Medium-high |
| 4 | Customer name in narration + exactly one open invoice with that amount | Medium |
| 5 | Customer known, amount fits several invoices or none | Low — leave unapplied, ask customer |
| 6 | Remitter not in customer master | Suspense |

## 4. Procedure

1. Parse bank credits. Parse remittance emails; link by UTR.
2. Run the ladder per credit. Compute residual = invoice total − applied amount.
3. Classify residuals: TDS receivable (stated), short payment (unexplained → query customer), on-account.
4. Draft customer queries for low-confidence or unexplained items.
5. Output the proposal and tracker.

## 5. Outputs

- `cash_application_proposal.csv`: UTR, date, amount, customer, invoices, applied, residual, residual type, confidence, evidence.
- Draft customer queries; suspense list.

## 6. Escalation

Suspense items, residuals above the client's write-off limit, any credit from an unregistered domain remittance, and customer-claimed TDS without a later certificate → O2C lead.
