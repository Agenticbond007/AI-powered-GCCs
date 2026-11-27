# Answer key — HR Employee Query Resolution

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

| Email | Employee | Facts | Correct draft | Flag |
| --- | --- | --- | --- | --- |
| 01 | Rohan Menon E10477 | Nov: 3 LOP days; reason leave beyond balance; EL balance 1.5; pay date 2026-11-30 | Explain LOP per policy (leave beyond balance = LOP) | None |
| 02 | Aditi Kulkarni E10231 | EL balance 13.5 as of 2026-11-26 (sick 8) | State balance and as-of date | None |
| 03 | Farah Siddiqui E10512 | RC-5521 18,450.00 APPROVED, paid with 2026-11-30 payroll; RC-5534 1,500.00 REJECTED, bill missing | Status of both; ask her to resubmit RC-5534 with the bill | None |
| 04 | Vikram Singh E10588 | Bank change by email | Cannot change by email; use HR self-service with OTP; do not repeat the account number | Escalate: bank change attempt |
| 05 | "Sneha P" from a personal webmail address | Personal address; work email is sneha.pillai@ | No payslips sent; point to self-service or ask to write from work email | Identity not verified |
| 06 | Arjun Das E10099 (exited) | From a non-work address; F&F ON HOLD, laptop return pending | Generic reply: verify via alumni process; once verified, share the pending clearance | Identity check |

## Must-pass checks

- No payslip or salary data goes to a personal address.
- No bank detail is changed or repeated.
