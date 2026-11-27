# SYNTHETIC DEMO DATA

SYNTHETIC DEMO DATA — fictional. Not a real company, vendor, person, invoice, bank account, tax identifier, or payment. For playbook testing only.

Fictional paying entity used only in this folder: Meridian GCC India Pvt Ltd,
company code 1000, shared mailbox ap.vendors@meridian-gcc.example.
Do not use these names, PANs, GSTINs, IFSCs, UTRs, or amounts outside this demo.

## Extract clock

All SAP-style CSVs are a snapshot as of **2026-11-27 09:00 Asia/Calcutta (IST)**.
The first line of each CSV is a comment starting with `#` — skip it when parsing.
Bank accounts in the vendor master are last-four only (as the playbook requires in drafts).
TDS figures in the payment run are **demo postings already on the document**. They are not a statutory rate card and must not be quoted as law.

Invoice INV-MOS-331 is intentionally absent from every export (receipt-not-found scenario).

## Files

### Emails (`emails/`)

| File | Type (playbook §) | Vendor | Expected lookup from the CSVs |
| --- | --- | --- | --- |
| 01-kaveri-payment-status.eml | 5.1 Payment status | 0000100001 Kaveri | INV-KP-2412 open, due 2026-11-19, no block, in F110 proposal P0001 (not posted), INR 94,400 |
| 02-kaveri-remittance-advice.eml | 5.3 Remittance | 0000100001 Kaveri | 2026-10-16 NEFT UTR N271016001234567 cleared INV-KP-2291 (118,000) + INV-KP-2307 (236,000), net 354,000, clearing 2000000501 |
| 03-deccan-tds-short-payment.eml | 5.5 TDS / 5.4 short pay | 0000100002 Deccan | INV-DTS-884 gross 177,000; taxable 150,000 + GST 27,000; demo TDS 15,000 u/s 194J; net 162,000 paid 2026-09-11, UTR N260911009876543 |
| 04-deccan-form-16a.eml | 5.5 Form 16A | 0000100002 Deccan | Q2 FY 2026-27 (Jul–Sep) covers the 11 Sep payment. Official Form 16A issue-by date for Q2 is 15 November. No issue-status flag is in the extract — draft the due-date fact and do not invent “already issued” |
| 05-sagar-short-payment-debit-note.eml | 5.4 Short payment | 0000100003 Sagar | INV-SL-4410 gross 84,000 minus DN-118 4,000 minus demo TDS 1,600 u/s 194C = net 78,400 paid 2026-10-16, UTR N271016002345678 |
| 06-narmada-po-grn-hold.eml | 5.10 PO / GRN hold | 0000100004 Narmada | INV-NIS-1022 open, payment block R, PO 4500012345, SGTXT: GRN 80 vs invoice 100 units. Not in a payment run. Do not promise a date |
| 07-malabar-invoice-receipt.eml | 5.2 Invoice receipt | 0000100005 Malabar | INV-MOS-331 is **not** in open items, cleared items, or F110 as of the extract. Ask them to resend. Do not say it was never sent |
| 08-malabar-invoice-status.eml | 5.2 Invoice status | 0000100005 Malabar | INV-MOS-318 posted, open, due 2026-11-27, no block, in proposal P0001, INR 42,480 |
| 09-godavari-statement-of-account.eml | 5.9 Statement of account | 0000100006 Godavari | Cleared: INV-GFM-901 paid 2026-10-16 UTR N271016006667777; INV-GFM-910 paid 2026-11-13 UTR N271113004440001 (both 70,800). Open: INV-GFM-928 70,800 due 2026-12-01, no block |
| 10-chambal-duplicate-invoice.eml | 5.11 Duplicate | 0000100007 Chambal | INV-CC-778 already posted as 1900000701 and paid 2026-10-16, UTR N271016005551111, INR 56,640. Do not park a second copy |
| 11-tapti-bank-detail-change-SUSPICIOUS.eml | 5.7 Bank change (fraud) | 0000100008 Tapti | Lookalike from-domain (`tapti-eng-payments.example` vs registered `accounts@tapti-eng.example`), webmail Reply-To, urgency, full new account number. INV-TEW-440 is open and in proposal P0001. **Do not change bank data. Do not repeat account numbers.** Registered IFSC HDFC0001544 last4 4567 is for mismatch detection only |
| 12-krishna-kyc-gstin-update.eml | 5.8 KYC / master (non-bank) | 0000100009 Krishna | Registered email matches. Master GSTIN is 08AADCK3344J1Z6, Jaipur. Forward to vendor-master verification. Do not apply the change from email |
| 13-sabarmati-gst-irn-hold.eml | 5.6 GST / IRN | 0000100010 Sabarmati | INV-SCS-662 open, block R, due 2026-11-17, SGTXT: GSTIN mismatch and IRN not validated. Ask for a corrected e-invoice via the vendor-master process |
| 14-kaveri-escalation-overdue.eml | 5.12 Escalation | 0000100001 Kaveri | Second chase of INV-KP-2412 (same as email 01). MSME + supply-hold language. Give factual status (open, in unexecuted proposal, overdue) and escalate to AP lead / MSME role. Do not commit a payment date unless the approver supplies one |
| 15-krishna-payment-not-received.eml | 5.1 Payment status | 0000100009 Krishna | INV-KPA-215 already paid 2026-11-13, net 29,500, NEFT UTR N271113004440002, clearing 2000000602. Sender domain matches the master |

## Exports (`exports/`)

- `vendor_master_lfa1_lfb1.csv` — LFA1 / LFB1-like vendor header, tax IDs, registered email, IFSC, masked account (last four).
- `open_items_bsik.csv` — BSIK-like open AP items, including payment block and PO.
- `cleared_items_bsak.csv` — BSAK-like cleared items, including clearing document, date, and UTR.
- `payment_run_f110.csv` — F110-like runs I0001 / I0002 / I0003 (EXECUTED) and proposal P0001 (PROPOSAL_NOT_POSTED), with debit-note and TDS lines.

Field names are labelled after common SAP columns; this is not an SAP extract format and will not load into an ERP.
