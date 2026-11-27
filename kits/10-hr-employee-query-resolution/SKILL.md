# HR Employee Query Resolution — Agent Playbook

Status: v1, free agent kit. Review with your HR operations lead before live use.
Use: GCC HR shared services / people desks in India. Generic template.
Scope: Classify employee emails to the people desk, look up the answer in HR exports and the policy extract, and draft replies for an HR executive to approve. Never change HR data, never send personal data to unverified addresses.

## 1. Inputs

- Employee emails to the people-desk mailbox.
- `employee_master.csv`, `leave_balances.csv`, `payroll_register_nov2026.csv`, `reimbursement_claims.csv`, `fnf_tracker.csv`.
- `policy/hr_policy_faq.md` — the client's approved policy extract (the only source for policy answers).

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Draft only; an HR executive sends.
2. Identity: the sender must be the employee's work email on the master. Personal addresses get no personal data; the draft points to self-service or asks them to write from their work email. Exited employees: confirm identity via the client's alumni process before sharing details.
3. Never change bank details, salary, leave or tax data from email. Bank changes go to self-service with OTP.
4. Never share one employee's data with another. Mask account numbers.
5. Policy answers quote the policy extract only; no legal or tax advice.
6. Sensitive topics (harassment, health, grievances, resignations under dispute) → no draft content beyond acknowledgement; route to the HR business partner.

## 3. Procedure

1. Verify sender; find employee ID.
2. Classify: payroll/LOP, leave balance, reimbursement, bank change, document request, F&F, policy question, sensitive.
3. Look up the facts; draft with the exact figures and the policy line.
4. Log a tracker row: category, facts used, identity check, approver.

## 4. Outputs

Reply drafts; tracker; escalation list.

## 5. Escalation

Identity failures, bank-change attempts, sensitive topics, and F&F holds over the policy timeline → HR operations lead.
