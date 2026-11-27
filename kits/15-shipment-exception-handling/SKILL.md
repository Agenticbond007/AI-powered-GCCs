# Shipment Exception Handling — Agent Playbook

Status: v1, free agent kit. Review with your logistics lead before live use.
Use: GCC logistics / inbound desks in India. Generic template.
Scope: Read the shipment tracker and carrier or supplier emails, and draft exception briefs, requester updates and claims or discrepancy notes for a logistics lead to approve. Never change a PO, never accept a new date or a claim, never commit a delivery date.

## 1. Inputs

- `shipment_tracker.csv` — ASN, ETA, quantities, status, requester.
- `vendor_master.csv` — registered supplier emails.
- `exception_policy.csv` — delay, short, damage and customs rules.
- Supplier, carrier and warehouse emails.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; the logistics lead sends and the buyer amends the PO.
2. A supplier or carrier's new date is "supplier-stated" or "carrier-stated" until the lead accepts it. Never write it as confirmed.
3. Do not accept or reject damage liability, and do not offer a credit.
4. Do not amend quantities or close an ASN from a short-delivery email.
5. External drafts go only to the registered vendor email, the named requester, or the warehouse address already on the tracker.

## 3. Procedure

1. For each open shipment, compute days past ETA and quantity short (ASN − received).
2. Attach emails to the shipment they name.
3. Classify: on time, no action; delay; short delivery; damage; customs hold.
4. Draft the exception brief, the requester update, and any discrepancy or claims note.
5. Write the exception log.

## 4. Outputs

- `shipment_exception_log.csv`: shipment, PO, exception type, original ETA, stated new date, qty short, action, owner.
- Exception briefs, requester updates, discrepancy notices, claims packs (drafts).

## 5. Escalation

Delays more than 3 days past ETA, customs holds, damage, and any requester-flagged line-down risk → logistics lead (and buyer where the policy says so).
