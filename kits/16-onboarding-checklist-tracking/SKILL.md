# Onboarding Checklist Tracking — Agent Playbook

Status: v1, free agent kit. Review with your HR operations lead before live use.
Use: GCC HR operations / people desks in India. Generic template.
Scope: Track new-hire checklist steps, flag items that are still open, and draft manager, joiner and IT updates for an HR executive to approve. Never change a start date, never collect or store bank or ID numbers from email, never confirm a joining if BGV is blocked.

## 1. Inputs

- `new_hire_register.csv` — candidate, manager, start date, status.
- `onboarding_checklist.csv` — steps, owners, due dates and status.
- `onboarding_policy.csv` — BGV, data and start-date rules.
- Emails from managers and joiners.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; HR ops updates the checklist and sends mail.
2. Identity: pre-joining candidates often write from a personal email on the register. Share only joining logistics, not salary or ID data. After the start date, prefer the work email.
3. Never accept, store or repeat bank account numbers, IFSC, Aadhaar or PAN from email. Point the person to HR self-service with OTP. Do not copy the numbers into the tracker or the draft.
4. Do not confirm a start date if BGV is BLOCKED or overdue. Escalate to HR ops.
5. Do not confirm a requested start-date change. Record it and notify talent / HR ops.

## 3. Procedure

1. For each candidate, list open, blocked and overdue steps.
2. Read emails and attach them to the candidate ID.
3. Draft: manager updates with the open steps and owners; joiner logistics (agenda, what is complete); IT chases; escalations for blocked BGV; a bank-data refusal plus a start-date-change routing note where needed.
4. Write the open-items list.

## 4. Outputs

- `onboarding_open_items.csv`: candidate, start date, open/blocked steps, overdue flag, next action, owner, approver.
- Drafts to managers, joiners, IT and HR ops.

## 5. Escalation

Blocked or overdue BGV, post-join steps still open (especially IT equipment), and any bank or ID data received by email → HR operations lead.
