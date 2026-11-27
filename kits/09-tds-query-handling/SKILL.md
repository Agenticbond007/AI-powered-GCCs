# TDS Query Handling — Agent Playbook

Status: v1, free agent kit. Review with your direct-tax lead before live use.
Use: GCC AP tax desks in India. Generic template.
Scope: Answer vendor questions about TDS deducted (26AS, Form 16A, lower deduction certificates, PAN errors) from the deduction, challan, certificate and LDC registers, and draft replies for a tax analyst to approve. The agent restates facts; it never gives tax advice, changes rates, files returns, or promises refunds.

## 1. Inputs

- Vendor emails to the AP tax mailbox.
- `tds_deduction_register.csv` — deductions as posted (section, rate, amount, challan, quarter, PAN as reported).
- `challan_register.csv` — deposit status.
- `form16a_issue_log.csv` — certificate status per quarter.
- `ldc_register.csv` — lower deduction certificates on file.
- `vendor_master.csv` — PAN and registered email.

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Draft only; the tax analyst approves.
2. Never change a TDS rate or section because of an email. LDCs apply only after the tax team verifies the certificate.
3. No legal explanations of sections or rates; restate what was posted and route "why" questions to the tax lead.
4. No refund promises. Excess-deduction claims go to the tax lead.
5. Sender domain must match the master. Share only that vendor's data; PAN may be shown in full only to the vendor itself.

## 3. Procedure by query type

| Type | Look up | Draft says |
| --- | --- | --- |
| 26AS not showing | Deduction → challan → quarter → PAN | The chain of facts; if all present, ask vendor to recheck after the return is processed |
| Form 16A request | Issue log | Issued (date) and resend via the client's process, or pending → no date promise, escalate |
| LDC claim | LDC register | In register → tax review; not in register → ask for the certificate, no rate change |
| Posting differs from LDC on file | Register vs posting | Facts both sides; tax lead review |
| PAN mismatch | Register PAN vs master PAN | Acknowledge; tax lead to correct via revision; no promise of timing |
| Why deducted | Posting | Section and amount as posted; tax lead to reply on the basis |

## 4. Outputs

- Draft reply per email; tracker row with type, facts used, approver.
- Escalation list for the tax lead.

## 5. Escalation

Pending certificates past the client's issue calendar, LDC or PAN issues, refund claims, undeposited challans, and any "why" question → direct-tax lead.
