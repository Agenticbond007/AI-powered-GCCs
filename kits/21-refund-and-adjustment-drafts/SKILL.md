# Refund and Adjustment Drafts — Agent Playbook

Status: v1, free agent kit. Review with your adjustments / finance lead before live use.
Use: GCC customer-service adjustments desks in India, working with finance. Generic template.
Scope: Read refund and adjustment requests against invoices, prior refunds and policy, and draft a recommended credit or a refusal / escalation for a named lead to approve. Never process a refund, never post a credit, never tell the customer that money is on the way.

## 1. Inputs

- Customer emails to the adjustments mailbox.
- `orders_invoices.csv` — invoice, amount, delivery date, return window, status.
- `prior_refunds.csv` — refunds already paid or in progress.
- `refund_policy.csv` — window, duplicate, goodwill and chargeback rules.
- `customer_master.csv` — registered contacts.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; the adjustments lead approves and finance posts.
2. Never tell the customer a refund has been processed or that funds will arrive on a date.
3. Do not recommend a standard refund after the return window. Do not draft goodwill as approved.
4. If a refund has already been paid, do not draft a second one. Cite the prior UTR and date.
5. Chargeback language: escalate to finance the same hour. Do not also draft a voluntary refund that could double-pay.
6. A billing dispute already open is not a second refund path. Cross-refer it.
7. Quote only the invoice amount and a clearly calculated proportionate figure. Show the working.

## 3. Procedure

1. Identify the invoice, delivery date, window, status and any prior refund.
2. Classify: in-window unused return; out of window; duplicate charge; already refunded; open billing dispute; chargeback threat; goodwill.
3. Calculate any recommended amount and tax, and write the working.
4. Draft the internal recommendation and a customer holding or explanation reply.
5. Write the adjustments log.

## 4. Outputs

- `adjustments_log.csv`: invoice, customer, class, amount requested, recommended amount, policy basis, approver, finance flag.
- Internal recommendation drafts and customer replies (holding or explanation only).

## 5. Escalation

Chargebacks, goodwill, out-of-window requests, disputed invoices, and any recommended credit above the client's limit → adjustments lead and finance, same hour for chargebacks.
