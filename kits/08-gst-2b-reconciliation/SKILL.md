# GST GSTR-2B vs Purchase Register Reconciliation — Agent Playbook

Status: v1, free agent kit. Review with your indirect-tax lead before live use.
Use: GCC tax and AP desks in India. Generic template.
Scope: Match the GSTR-2B download (CSV/XLSX from the GST portal, downloaded by the client) to the purchase register, classify mismatches, and draft vendor follow-ups and a summary for the tax lead. The agent never logs in to the GST portal, never files, and never decides input tax credit eligibility.

## 1. Inputs

- `gstr2b_oct2026.csv` — supplier GSTIN, invoice no., date, taxable value, IGST/CGST/SGST.
- `purchase_register_oct2026.csv` — the same fields from the books.
- `vendor_master.csv` — vendor GSTIN and registered email for follow-ups.

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo).

## 2. Hard controls

1. Facts only. Report match status; the tax lead decides ITC treatment.
2. No portal access, no filing, no ERP posting.
3. Follow-ups go to the vendor's registered email only, quoting only that vendor's invoices.
4. Do not quote GST law, due dates or rates beyond what is printed on the documents.

## 3. Procedure

1. Normalise invoice numbers (uppercase; drop `/`, `-`, spaces and leading zeros) and GSTINs.
2. Match key = GSTIN + normalised invoice number. Then compare date, taxable value and tax (tolerance INR 1 unless the client sets one).
3. Second pass for unmatched rows: same PAN (characters 3–12 of the GSTIN) + invoice number → GSTIN mismatch.
4. Classify: MATCHED; MATCHED-FORMAT (number format only); MATCHED-DATE (date differs only); VALUE-MISMATCH; GSTIN-MISMATCH; IN-PR-NOT-2B; IN-2B-NOT-PR.
5. Draft vendor follow-ups: missing in 2B (ask vendor to report the invoice in their return), value mismatch, GSTIN mismatch. Draft an AP query for IN-2B-NOT-PR.
6. Summary table: counts and tax amounts by status.

## 4. Outputs

- `gst_recon_oct2026.csv` with status per invoice and tax difference.
- Vendor follow-up drafts; AP query; one-page summary for the tax lead.

## 5. Escalation

Any GSTIN mismatch, value differences above the client threshold, and suppliers missing for two periods → indirect-tax lead.
