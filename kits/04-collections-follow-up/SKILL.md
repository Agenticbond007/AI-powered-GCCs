# Collections Follow-up — Agent Playbook

Status: v1, free agent kit. Review with your collections lead before live use.
Use: GCC order-to-cash desks in India. Generic template.
Scope: Build today's collections worklist from the AR ageing export, read customer replies, and draft the right follow-up for each customer for a collector to approve. Never send, never post, never threaten.

## 1. Inputs

- `ar_open_items_fbl5n.csv` — open invoices with due date and days overdue.
- `customer_master.csv` — AP contact, terms, credit limit.
- `collection_notes.csv` — previous reminders, calls, promises to pay (PTP).
- `unapplied_receipts.csv` — money received but not yet applied.
- `dunning_policy.csv` — client-set levels, tone and approver.
- Customer emails in the collections mailbox.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; the collector sends. Level 3 and broken-promise drafts need collections-lead approval.
2. No legal, credit-hold, interest or supply-stop language unless the lead adds it.
3. Check unapplied receipts and disputes before chasing. Never chase money already received or a disputed invoice.
4. Each draft goes only to that customer's registered AP contact and lists only that customer's invoices.
5. Never accept bank-detail changes or share our bank details in a new format by email; point to the invoice's registered remittance details.

## 3. Procedure

1. For each customer, list open items, days overdue and total.
2. Read new emails and classify: promise to pay, dispute, already paid, request for copy, other.
3. Apply in this order:
   a. Unapplied receipt matches (UTR, amount) → no chase; route to cash application; draft a thank-you.
   b. Dispute → log dispute case, pause dunning on that invoice only, route to sales ops / billing; acknowledge.
   c. Valid PTP with a future date → record it; no chase before the date; acknowledge.
   d. Broken PTP (date passed, not received) → escalate per policy.
   e. Otherwise → dunning level by the oldest overdue invoice.
   f. Not yet due and within the pre-due window → courtesy reminder.
4. Draft each email with invoice numbers, amounts, due dates and a clear ask.
5. Write the worklist and tracker.

## 4. Outputs

- `collections_worklist.csv`: customer, invoices, overdue amount, action, level, approver, next follow-up date.
- One draft per customer needing contact; internal routing notes (billing, cash application).

## 5. Escalation

Broken promises, level 3, disputes above the client's threshold, customers over credit limit, and any request to change bank details → collections lead.
