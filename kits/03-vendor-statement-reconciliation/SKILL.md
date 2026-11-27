# Vendor Statement Reconciliation — Agent Playbook

Status: v1, free agent kit. Review with your AP lead before live use.
Use: GCC AP desks in India. Generic template.
Scope: Compare a vendor's statement of account (SOA) with our vendor ledger export, explain every difference, and draft a reconciliation statement and reply for an AP user to approve. Never post adjustments or promise payment dates.

## 1. Inputs

- Vendor SOA (CSV, XLSX or PDF table) received by email — demo: `demo-data/statements/`.
- `vendor_ledger_fbl1n.csv` — our ledger for the vendor: invoices (credit), payments, debit notes, TDS (debit), with clearing documents and UTRs.
- `vendor_master.csv` — registered email (sender check).

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Draft only. No ERP postings, no clearing, no payment commitments.
2. Sender domain must match the master. A mismatch → hold and verify before sharing any ledger data.
3. Share only this vendor's data. Mask bank accounts. Do not attach our full ledger; list the reconciling items.
4. Never change bank or master data because a statement shows different details.
5. TDS: restate what was deducted as posted. Do not advise on law or rates.

## 3. Procedure

1. Confirm sender domain. Parse the SOA; skip comment lines.
2. Compute both balances as of the SOA date. Vendor balance = invoices − receipts on their statement. Our balance = credits − debits on our ledger.
3. Match line by line on reference (normalise invoice numbers), then amount, then UTR for payments.
4. Classify each unmatched item:
   - A. Invoice on SOA, not in our books → request copy; check intake queue.
   - B. Payment in our books, not on SOA → send remittance (date, amount, UTR).
   - C. Debit note in our books, not on SOA → send DN copy and reason.
   - D. TDS in our books, not on SOA → explain TDS deducted as posted; certificate follows the client's Form 16A cycle.
   - E. Invoice in our books, not on SOA → ask vendor to confirm.
   - F. Amount mismatch on same reference → quote both values, ask for documents.
5. Prove it: our balance + sum of differences = vendor balance. If it doesn't tie, stop and escalate.
6. Draft the reconciliation statement and reply. Log in the tracker.

## 4. Outputs

- Reconciliation statement per vendor: both balances, each reconciling item with category, amount and next action.
- Draft reply to the vendor.
- Internal actions list (e.g., "locate INV-KP-2440 in intake").

## 5. Escalation

Unexplained difference, possible duplicate payment, a vendor balance lower than ours (possible overpayment), MSME vendor with overdue items, or a sender mismatch → AP lead.
