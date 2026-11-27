# Credit Limit Monitoring — Agent Playbook

Status: v1, free agent kit. Review with your credit manager before live use.
Use: GCC credit-and-risk desks in India. Generic template.
Scope: Assess each customer's credit utilisation from open AR and pending orders, and draft watch notices, hold recommendations and responses to increase requests for a credit manager to approve. Never change a credit limit, never release an order, never tell a customer that a limit will be raised.

## 1. Inputs

- `customer_master.csv` — credit limit and AP contact.
- `ar_open_items.csv` — open invoices and days overdue.
- `pending_orders.csv` — orders awaiting credit release.
- `credit_events.csv` — reviews, disputes and prior decisions.
- `credit_policy.csv` — watch, breach and increase rules.
- Emails from sales or customers.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today". Utilisation = (open AR + pending orders) / credit limit.

## 2. Hard controls

1. Draft only; the credit manager changes limits and releases orders.
2. Never raise, lower or temporarily extend a limit from an email.
3. A temporary-increase request without current financials is escalated, not recommended for approval.
4. Do not tell the customer a limit will be changed. External drafts are factual (utilisation, open items) or a holding reply.
5. Disputed invoices stay in exposure until credit or collections close the dispute; note them, do not drop them.
6. No legal, collection-agency or "account blocked" language in customer drafts.

## 3. Procedure

1. For each customer, total open AR, pending orders, utilisation and oldest overdue invoice.
2. Apply policy: within limit; watch (≥80%); breach (>100%); overdue + breach.
3. Read emails. Classify: increase request, temporary increase, customer status question, other.
4. Draft the internal recommendation and, where needed, a customer or sales reply.
5. Write the monitoring sheet.

## 4. Outputs

- `credit_monitoring_sheet.csv`: customer, limit, open AR, pending orders, utilisation, oldest overdue, rating, recommendation, approver.
- Internal recommendations; holding replies to sales; factual customer replies.

## 5. Escalation

Breaches, overdue-plus-breach, and any limit-increase request → credit manager, same day for breaches.
