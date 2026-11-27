# Intercompany Reconciliations — Agent Playbook

Status: v1, free agent kit. Review with your financial controller before live use.
Use: GCC record-to-report / intercompany desks in India. Generic template.
Scope: Reconcile intercompany ledgers between group entities, explain every difference, and draft queries and proposed journals for a controller to approve. Never post, never net, never write off a difference.

## 1. Inputs

- `entity_master.csv` — legal entities, currencies and IC contacts.
- `ic_ledger_in01.csv`, `ic_ledger_sg01.csv`, `ic_ledger_uk01.csv` — open IC items per entity.
- `fx_rates.csv` — group rates used for booking and for the extract date.
- `ic_policy.csv` — mismatch, FX and netting rules.
- Emails from counterpart IC desks.

Use the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) as "today".

## 2. Hard controls

1. Draft only; the controller posts and sends.
2. Do not write off an amount mismatch. Both controllers must agree a correcting entry.
3. Do not book an item that appears on only one ledger from an email request. Query the originator and the silent-side owner.
4. FX differences: propose a draft JE only if within the policy threshold; escalate if above. Cite the rate card and booking date.
5. Netting is a proposal only, for treasury and both controllers.
6. Use registered IC emails from the entity master only.

## 3. Procedure

1. Build a pair-wise position: India vs each counterpart, by document number.
2. Classify each document: matched; timing (counterpart confirms a future booking date); amount mismatch; one-sided; FX difference.
3. Attach inbound emails to the document they name.
4. Draft a query or confirmation for every unexplained or disputed item. Propose JEs only where policy allows.
5. Produce the recon pack: matched total, open differences, proposed entries, items for approval.

## 4. Outputs

- `ic_recon_pack.csv`: document, counterpart, India amount, counterpart amount, difference, class, action, owner.
- Draft emails to counterpart desks and internal notes to the India controller.
- Proposed JEs (drafts) where policy allows.

## 5. Escalation

Amount mismatches, one-sided charges, differences above the FX threshold, and any netting proposal → India controller (Ananya Rao in the demo).
