# Bank Reconciliation — Agent Playbook

Status: v1, free agent kit. Review with your R2R lead before live use.
Use: GCC record-to-report desks in India. Generic template.
Scope: Match the bank statement to the GL cash book, classify every unmatched item, prove the reconciliation, and draft proposed journal entries and follow-ups for an accountant to approve. Never post.

## 1. Inputs

- `bank_statement_demo_bank.csv` — bank statement export (fictional bank).
- `gl_cash_book_fbl3n.csv` — GL cash account line items.
- `recon_parameters.csv` — account, period, opening balance, date window, tolerance.

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Proposals only. JEs are drafted with evidence; an accountant posts and a reviewer approves.
2. Never net off unrelated items to force a tie. If it doesn't tie, stop and report the gap.
3. Unknown debits (NACH, card, unexplained transfers) are possible unauthorised transactions: escalate the same day, never "plug".
4. Mask account numbers to the last four digits.

## 3. Procedure

1. Check both files start from the same opening balance.
2. Match one-to-one on reference/UTR + amount, then amount + date within the window, then many-to-one.
3. Classify unmatched items:
   - Bank side, not in books: bank charges, interest, unknown debits → propose JE or escalate.
   - Book side, not in bank: outstanding cheques/payments, deposits in transit → timing; list with age.
   - Same reference, different amount → probable keying error; find the source document.
   - Same reference twice in books, once in bank → duplicate posting; propose reversal.
4. Build the statement: bank balance ± timing items = adjusted bank; book balance ± book corrections = adjusted book. They must be equal.
5. Draft JEs and follow-up emails.

## 4. Outputs

- Reconciliation statement (balances, each item, category, age, action).
- Proposed JEs (date, accounts, amount, evidence).
- Escalation note for unknown debits; follow-ups for stale items.

## 5. Escalation

Unknown debits → treasury lead immediately. Outstanding items older than the client threshold, duplicates, and any unreconciled difference → R2R lead.
