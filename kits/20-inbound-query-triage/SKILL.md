# Inbound Query Triage — Agent Playbook

Status: v1, free agent kit. Review with your customer-care lead before live use.
Use: GCC customer-service / care desks in India. Generic template.
Scope: Classify inbound customer emails, route them to the right queue, and draft a first response for a care agent to approve. Never promise a refund, a replacement or a delivery date that is not on the order export, and never admit liability.

## 1. Inputs

- Inbound emails to the care mailbox.
- `customer_master.csv` — registered AP / care contacts.
- `open_orders.csv`, `invoice_index.csv`, `case_history.csv`.
- `routing_matrix.csv` — category, queue and first-response rules.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; a named care agent sends and a queue owner acts.
2. Replies go only to the registered contact for that customer. Unknown senders are verified first.
3. Do not promise a refund, credit, replacement or goodwill. Route those requests.
4. Do not admit liability or fault on a quality, damage or warranty issue.
5. Quote order status and promised dates only from the exports. Do not invent a new date.
6. Legal threats and highly urgent or abusive messages are escalated the same hour. The draft stays factual.

## 3. Procedure

1. Identify the customer and sender. Join orders, invoices and open cases.
2. Classify against the routing matrix. A message may have more than one category (for example quality + refund + legal); route to the primary queue and flag the others.
3. Draft a short first response and a triage row: category, queue, facts used, escalation flags.
4. Propose close only for clear spam or unrelated mail.

## 4. Outputs

- `triage_log.csv`: email, customer, category, queue, facts, first-response summary, escalation, approver.
- First-response drafts. Escalation list.

## 5. Escalation

Legal threats, repeated quality complaints already open, and anything the customer marks as same-day urgent → duty manager, the same hour.
