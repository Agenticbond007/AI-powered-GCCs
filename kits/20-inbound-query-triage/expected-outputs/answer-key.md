# Answer key — Inbound Query Triage

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| Email | Customer | Category | Queue | Facts | Draft |
| --- | --- | --- | --- | --- | --- |
| 01 | Aravalli Retail | Order status | Order desk | SO-77001 SHIPPED, shipment SH-C-8891, promised 2026-11-25 | Status from the export; no new date invented |
| 02 | Nilgiri Foods | Invoice / copy request | AR billing | SO-77040 is PICKING, promised 2026-12-02; no invoice for this order is in the index yet | Route to billing; do not invent or attach an invoice; do not add bank details |
| 03 | Konkan Motors | Quality / damage (primary); refund request; legal threat | Quality / complaints, plus duty manager the same hour | SO-77055 DELIVERED; open case CS-1902 already on this damage | Acknowledge the report; refer to CS-1902; do not admit liability; do not promise a refund or replacement; escalate the legal wording |
| 04 | Satpura Agro | Warranty | Warranty desk | SO-77062 is a current order (CONFIRMED), not clearly the failed delivery; no warranty record in the extract | Acknowledge and route; do not approve a claim; ask for the original order or invoice reference |
| 05 | None | Spam / unrelated | Propose close | Solicitation, not a customer | No customer draft |
| 06 | Vindhya Pharma | Refund / adjustment | Adjustments | INV-90131 is not in this invoice index (older dispute already known to billing) | Route to adjustments; do not promise a refund; note the existing rate dispute |

## Must-pass checks

- No draft promises a refund, replacement, credit or new delivery date.
- Email 03 does not admit liability and is escalated the same hour for the legal wording.
- Email 05 has no customer reply.
- Email 02 does not attach a made-up invoice PDF or bank details.
