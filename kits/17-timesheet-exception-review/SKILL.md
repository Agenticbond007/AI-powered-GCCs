# Timesheet Exception Review — Agent Playbook

Status: v1, free agent kit. Review with your HR operations / payroll lead before live use.
Use: GCC timekeeping and payroll-prep desks in India. Generic template.
Scope: Review a weekly timesheet export against policy and project master, and prepare an exception list plus manager and employee drafts for a timekeeping lead to approve. Never approve hours, never post to payroll, never change a timesheet.

## 1. Inputs

- `timesheets_week_ending_2026-11-22.csv` — daily hours by employee and project (week Mon 16 Nov to Sun 22 Nov).
- `project_master.csv` — valid project codes.
- `overtime_policy.csv` — day length, caps, weekend and approval rules.
- Emails from managers and employees.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; the timekeeping lead and the line manager approve; payroll posts.
2. Never approve, reject-and-close, or post hours.
3. Hours above 12 in a calendar day are a hard flag. Do not recommend approval.
4. Weekend or holiday hours need prior written manager approval already on file (an email in this kit counts). If it is missing, flag them; do not assume approval.
5. Invalid project codes are returned to the employee. They are not approved against a guessed code.
6. Sick or leave coding is decided by the manager and HR; the agent only flags the gap.

## 3. Procedure

1. For each employee in the extract, total regular and overtime hours; list weekdays with no entry.
2. Flag: missing weekday; weekday hours > 8 without OT type or approval; hours > 12 in a day; weekend hours; project code not on the master.
3. Attach emails (approvals, explanations, recode requests).
4. Draft the exception list and short notes to the manager or employee.
5. Employees with a clean week are listed as clear, with no draft needed.

## 4. Outputs

- `timesheet_exception_list.csv`: employee, date or range, exception type, hours, evidence, recommendation, owner, approver.
- Drafts to managers and employees. A cover note for the timekeeping lead.

## 5. Escalation

Days over 12 hours, weekend OT without written approval, and repeated missing timesheets → HR ops / payroll lead.
