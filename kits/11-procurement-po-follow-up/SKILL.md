# Procurement PO Follow-up — Agent Playbook

Status: v1, free agent kit. Review with your procurement lead before live use.
Use: GCC procurement / buying desks in India. Generic template.
Scope: Read the open-PO export and supplier and requester emails, then draft expediting emails, requester updates and a proposed delivery-date tracker for a buyer to approve. Never change POs, accept prices or commit dates on the supplier's behalf.

## 1. Inputs

- `open_po_lines_me2m.csv` — open PO lines with delivery date, received qty, acknowledgement.
- `vendor_master.csv` — registered supplier emails.
- `follow_up_policy.csv` — reminder and escalation days.
- Supplier and requester emails.

"Today" is the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Draft only; the buyer sends and updates the PO.
2. Price, quantity or terms changes go to the buyer. The desk never says "accepted".
3. A supplier's new date is recorded as "supplier-stated" until the buyer accepts it.
4. Emails go only to the PO's supplier (registered email) or the PO's requester.

## 3. Procedure

1. For each open line: days to or past delivery date; open qty = PO − received.
2. Read emails and attach them to PO lines (by PO number).
3. Decide per line:
   - Supplier gave a new date → record it, update requester, note impact.
   - Partial delivery with balance date → record; update requester.
   - Price/terms change request → route to buyer; acknowledge only.
   - Overdue, no acknowledgement → expedite to supplier; escalate to buyer if past the escalation day.
   - Due within the pre-due window and not acknowledged → reminder to confirm.
   - Not due, acknowledged → no action.
4. Reply to requester chases with facts and the next step.
5. Output the tracker.

## 4. Outputs

- `po_followup_tracker.csv`: PO/line, vendor, open qty, due date, days overdue, supplier-stated date, action, owner.
- Supplier expedite/reminder drafts, requester updates, buyer routing notes.

## 5. Escalation

Lines past the escalation day, price/terms requests, and requester-flagged business impact → buyer.
