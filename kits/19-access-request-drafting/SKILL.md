# Access Request Drafting — Agent Playbook

Status: v1, free agent kit. Review with your IT security / access-management lead before live use.
Use: GCC identity and access management desks in India. Generic template.
Scope: Turn intake emails into a complete access-request pack (roles, approvers, SoD check, start/end dates) for an access manager to approve. Never provision, extend or revoke access in a system.

## 1. Inputs

- Inbound request emails.
- `identity_register.csv` — employees and contractors, manager, status, contract end.
- `role_catalogue.csv` — roles, type and required approvers.
- `current_access.csv` — roles already held.
- `sod_rules.csv` and `access_policy.csv`.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only. A named access manager provisions or revokes, after the listed approvers sign.
2. Never treat a peer, the requestor, or "manager is travelling" as line-manager approval.
3. Privileged and sensitive roles need every approver in the catalogue, including IT security for privileged roles.
4. Contractor access must have an end date. If the contract end is blank, the pack is not marked ready.
5. A request that would break an SoD rule is stopped. It is not drafted as ready to provision.
6. Leaver revocations are drafted in full. If the last working day has already passed, escalate as late.

## 3. Procedure

1. Identify the person, type, status and line manager.
2. Map the requested roles to the catalogue. List current access.
3. Run the SoD check against current + requested roles.
4. Confirm who has already approved in writing, and who is still required.
5. Draft the pack: ready for approval, stopped (SoD or missing manager), or incomplete (no contractor end date). Draft leaver revocation lists separately.

## 4. Outputs

- `access_request_pack.csv`: request, person, roles, type, SoD result, approvers outstanding, end date, recommendation, approver.
- Draft packs and, where needed, replies asking for a manager approval or a contract end date. Leaver revocation list.

## 5. Escalation

SoD conflicts, privileged roles, late leaver revocations, and contractor requests without an end date → access-management lead and, for SoD, the process owner.
