# Variance Commentary — Agent Playbook

Status: v1, free agent kit. Review with your FP&A lead before live use.
Use: GCC FP&A teams in India preparing month-end packs. Generic template.
Scope: Compute actual vs budget and vs prior month from a trial-balance export, pick the lines over threshold, and draft evidence-backed commentary plus owner queries for an analyst to approve. Never invent a cause.

## 1. Inputs

- `trial_balance_nov2026.csv` — GL, description, cost centre, actual, budget, prior month, owner.
- `drivers_nov2026.csv` — headcount, contractor count, FX rates (demo values).
- `variance_policy.csv` — thresholds and sign convention.
- Owner emails explaining movements.

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Every cause cites evidence: a driver row or an owner email (sender, date). No evidence → "Driver not evidenced; query sent to <owner>".
2. Numbers come only from the files; recompute every variance and percentage.
3. Draft only. The analyst edits and the FP&A head approves the pack.
4. Do not forecast or restate budgets.

## 3. Procedure

1. Variance = Actual − Budget; % = Variance ÷ Budget. Also compute vs prior month.
2. Flag a line when |%| ≥ threshold AND |INR| ≥ threshold (both), or when budget is zero and |INR| ≥ threshold.
3. For each flagged line, gather evidence; write two to three lines: what moved, by how much, why (with citation), and whether it is timing or permanent if the evidence says so.
4. For lines with no evidence, draft a one-line query to the owner.
5. Produce the commentary table and an executive summary of three bullets.

## 4. Outputs

- Variance table (all lines) with a flag column.
- Commentary for flagged lines with evidence references.
- Owner query drafts; open-questions list.

## 5. Escalation

Unexplained adverse variance above 2× threshold, or an owner who has not replied by the pack deadline → FP&A head.
