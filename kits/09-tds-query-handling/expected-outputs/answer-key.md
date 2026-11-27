# Answer key — TDS Query Handling

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| Email | Vendor | Facts from the registers | Correct draft | Escalate? |
| --- | --- | --- | --- | --- |
| 01 | Deccan | INV-DTS-884, 194J as posted, 15,000.00, deducted 2026-09-11, challan 00017 deposited 2026-10-07, Q2; Form 16A issued 2026-11-10; PAN matches | Give the chain; offer to resend the certificate; ask vendor to recheck 26AS | No |
| 02 | Sagar | Q2: INV-SL-4388, 1,200.00, challan 00012 deposited; Form 16A PENDING | Acknowledge; certificate pending; no date promise | Yes, pending certificate |
| 03 | Krishna | No LDC in register; no certificate attached | Ask for the certificate copy; rate unchanged until tax verifies | Yes, LDC verification |
| 04 | Godavari | LDC-DEMO-2026-0451 on file (194C, 1%, valid to 2027-03-31); INV-GFM-910 posted at 2%, 1,200.00; challan 00025 not yet deposited | State both facts; tax lead to review; no refund promise | Yes |
| 05 | Chambal | Register PAN AABCC6789H ≠ master AABCC6789G; 960.00 on INV-CC-778, challan 00021 | Acknowledge PAN error found; tax lead to correct; no timing promise | Yes |
| 06 | Kaveri | INV-KP-2412, section 194Q as posted, 80.00 | Restate posting; tax lead will respond on the basis | Yes |

## Must-pass checks

- No draft explains the law behind a section or rate.
- Email 03 does not change the rate.
- Email 04 does not promise a refund.
