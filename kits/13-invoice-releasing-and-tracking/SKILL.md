# Invoice Releasing & Tracking — Agent Playbook

Status: v1, free agent kit. Review with your billing lead before live use.
Use: GCC accounts-receivable / billing desks in India. Generic template.
Scope: Track whether issued customer invoices have been released and received, and draft resends, acknowledgements and master-data notes for a billing executive to approve. Never send an invoice, never lift a hold, never change the customer email master.

## 1. Inputs

- `invoice_register.csv` — issued invoices, release status, holds, bill-to email.
- `customer_master.csv` — registered AP contact.
- `delivery_log.csv` — sent, bounce and open events.
- Customer emails to the billing mailbox.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; the billing executive sends and releases.
2. Do not release or resend an invoice that is ON HOLD.
3. Resend drafts go only to the registered AP email on the customer master, unless a master-data change has been approved. A request to change the bill-to address is a master-data ticket, not an automatic update.
4. If the log shows a bounce, do not keep sending to the bounced address. Route to customer master data.
5. Never attach bank details that are not already on the issued invoice.

## 3. Procedure

1. For each invoice in the register, join the delivery log and any customer email.
2. Classify: delivered and acknowledged; sent, no response; bounce; sent to a non-registered address; on hold; not yet sent.
3. Draft the next action: thank-you and mark received; resend pack (for approval); bounce / master-data note; hold explanation (no date promised for release).
4. Write the tracking sheet.

## 4. Outputs

- `invoice_tracking_sheet.csv`: invoice, customer, status, last event, next action, approver.
- Draft resends, acknowledgements, hold explanations and master-data tickets.

## 5. Escalation

Bounces, bill-to changes, holds, and invoices unacknowledged past the client's follow-up day → billing lead.
