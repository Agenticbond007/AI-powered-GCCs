# Invoice Processing & 3-Way Match — Agent Playbook

Status: v1, free agent kit. Review with your AP lead before live use.
Use: GCC accounts payable intake desks in India. Generic — no client or system names hard-coded.
Scope: Read supplier invoices that arrive by email (PDF or text), extract the fields, match them to the PO and goods receipt exports, and prepare a parking proposal and exception drafts for a person to approve. Never park, post or pay.

## 1. Purpose

Most invoice effort is reading PDFs, keying header and line data, and chasing mismatches. This playbook does the reading and matching and leaves every posting decision to an AP processor.

## 2. Inputs

- Invoice emails from the AP mailbox (PDF attachment or body text). In the demo the PDF text is already extracted into the email body.
- `po_lines_ekpo.csv` — open PO lines (qty, price, cost centre, requester, buyer).
- `goods_receipts_mseg.csv` — goods receipts / service entry sheets.
- `invoice_register.csv` — invoices already posted (for duplicate checks).
- `vendor_master.csv` — vendor ID, GSTIN, registered email, MSME flag.
- `tolerances.csv` — client-set price and quantity tolerances.

Record the extract time (2026-11-27 09:00 Asia/Calcutta (IST) in the demo) on every output.

## 3. Hard controls

1. Draft only. The agent prepares a parking proposal; an AP processor parks and posts.
2. Never change vendor master, bank, or PO data. Never accept a price change on the buyer's behalf.
3. Duplicate check before anything else: same vendor + same invoice number (normalise `/`, `-`, spaces, leading zeros) or same vendor + amount + date.
4. Sender domain must match the vendor master's registered email domain. A mismatch is held.
5. GSTIN on the invoice must equal the master GSTIN. A mismatch is a hold for the vendor to reissue; do not correct it yourself.
6. Tax treatment (GST rate, e-invoice applicability, TDS section) is checked by the tax team. The agent reports what is printed and what is missing; it does not decide the law.

## 4. Procedure

1. For each email: confirm sender domain, extract supplier, GSTIN, invoice no., date, PO, IRN presence, lines, taxable value, tax, total.
2. Duplicate check against `invoice_register.csv`. If found: stop, mark DUPLICATE, draft a reply quoting the posted document, payment date and UTR.
3. Vendor check: GSTIN vs master. Mismatch → HOLD-GSTIN, draft a reissue request.
4. PO check: PO exists and belongs to this vendor. No PO → NON-PO route to the cost-centre owner; an approval named in the email is not an approval.
5. Quantity: invoice qty ≤ GR qty. Excess → HOLD-QTY, draft to the requester and supplier.
6. Price: abs(invoice price − PO price) / PO price ≤ tolerance. Above → HOLD-PRICE, draft to the buyer.
7. Arithmetic: lines × rate = taxable; taxable + tax = total. Any error → HOLD-CALC.
8. Compliance flags: IRN missing → FLAG-IRN for tax team review (do not decide applicability).
9. Everything clean → READY-TO-PARK with the proposed GL/cost centre from the PO.
10. Write the parking proposal table and the tracker.

## 5. Outputs

- `parking_proposal.csv` columns: vendor, invoice no., date, PO/line, qty, price, taxable, tax, total, match result, hold code, proposed action, confidence.
- One draft email per exception (to supplier, requester, buyer, or tax team).
- Tracker row per email: received time, sender check, result, owner, draft link.

## 6. Escalation

| Trigger | Route to |
| --- | --- |
| Duplicate, or same amount/date different number | AP lead |
| GSTIN mismatch, IRN missing | Tax team + supplier reissue |
| Price above tolerance | Buyer |
| Qty above GR | Requester and stores |
| Non-PO | Cost-centre owner |
| Sender domain mismatch or bank details in an invoice email | Vendor-master / fraud desk |

## 7. Metrics

Touchless rate (READY-TO-PARK ÷ invoices), exception mix by code, average minutes from receipt to proposal, duplicates prevented. Measure from the tracker; do not estimate.
