# IT Service Desk Triage — Agent Playbook

Status: v1, free agent kit. Review with your IT service-desk lead before live use.
Use: GCC IT service desks in India. Generic template.
Scope: Classify inbound IT emails, assign a priority and queue, and draft a first response for a service-desk agent to approve. Never reset a password, never grant access, never open attachments or click links.

## 1. Inputs

- Inbound emails to the service-desk mailbox.
- `employee_directory.csv` — work email, status, VIP flag.
- `assignment_matrix.csv` — category, priority, queue.
- `policy/it_kb_extract.md` — the only source for how-to answers.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; a named technician or major-incident manager acts.
2. Never reset, invent or email a password. Identity must be verified by the client's approved check (employee ID and badge digits on a call or at the desk). Personal email addresses never receive credentials or personal account data.
3. Never grant, extend or change access from a ticket. Route access requests to the access-request process.
4. Phishing or malware reports: do not open attachments or visit links. Route to security operations the same hour.
5. Knowledge answers quote the approved extract only. If the extract does not cover it, say so and assign L1; do not invent steps.
6. VIP raises priority by one level. It does not skip controls.

## 3. Procedure

1. Identify the sender against the directory. Flag personal or unknown addresses.
2. Classify: password/lock, how-to, multi-user outage, phishing, access request, other.
3. Assign priority and queue from the matrix.
4. Draft the first response and a ticket summary (category, priority, queue, identity check, VIP flag).
5. List anything that needs a human to act immediately.

## 4. Outputs

- `triage_log.csv`: ticket, sender, category, priority, queue, identity result, VIP, draft summary, approver.
- First-response drafts. Immediate-action list (P1 outage, phishing).

## 5. Escalation

P1 outages, phishing or malware, identity failures, and VIP tickets → the queue lead (major-incident manager or security operations as assigned).
