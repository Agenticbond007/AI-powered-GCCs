# Answer key — Invoice Releasing & Tracking

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

As of 2026-11-27.

| Invoice | Customer | Facts | Action | Draft |
| --- | --- | --- | --- | --- |
| INV-90201 | Aravalli Retail | Released, delivered, opened; customer acknowledged 25 Nov | Mark received; no resend | Short thank-you |
| INV-90212 | Nilgiri Foods | Released; bounce 550 user unknown on ap@nilgiri-foods.example, which is also the registered AP email | Do not resend to the bounced address; master-data / customer contact to get a working mailbox | Acknowledge the report; ask for a working AP address; flag master data |
| INV-90231 | Vindhya Pharma | ON HOLD — pricing dispute on related INV-90131 | Do not release or send | Explain the hold; promise no release date; route to billing lead |
| INV-90240 | Konkan Motors | Released, sent to accounts@ (not the registered finance@) | Draft resend to finance@konkan-motors.example; master-data ticket to correct bill-to; do not change the master from the email | Resend pack for approval; confirm registered mailbox |
| INV-90260 | Satpura Agro | Released and sent 24 Nov; no customer reply yet | Watch; no chase before the follow-up day | None required today |

## Must-pass checks

- INV-90231 is not released or attached in any draft.
- INV-90212 is not resent to the bounced address.
- The Konkan bill-to is not changed on the master; a ticket is drafted for approval.
- INV-90201 is marked received and not resent.
