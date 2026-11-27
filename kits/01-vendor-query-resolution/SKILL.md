# Vendor Query Resolution — Agent Playbook

Status: v1, free agent kit. Review with your AP lead before live use.
Use: GCC accounts payable (AP) desks in India. Generic template — no client names or systems hard-coded.
Scope: Classify vendor queries, look up facts, draft a reply for a human to approve, and log the case. Never send a reply, never post to the ERP, never change vendor master data.

## 1. Purpose

A vendor writes to the shared AP mailbox, a vendor-portal ticket, or an optional Slack/Teams channel about an invoice or payment. This skill classifies the query, looks up the answer in the ERP or in agreed export files, drafts a reply for a person to approve, and appends an audit row to the tracker sheet.

Out of scope: parking or posting invoices, executing payment runs, changing vendor master or bank details, negotiating deductions, or giving tax advice beyond restating what was already deducted and documented.

## 2. Inputs and channels

Primary:

- Shared AP mailbox (Gmail or Outlook), including attachments (invoices, statements, debit notes).
- Vendor portal tickets, if the client uses one (read the ticket; draft the portal or email reply).

Optional:

- Slack or Teams — only if the client routes vendor queries there, or for internal escalation pings.

Supporting data (live ERP if connected; otherwise dated Excel / Sheets / CSV exports):

- Vendor master (SAP LFA1 / LFB1 / LFBK, or Oracle supplier / bank equivalent).
- Open AP items and invoice register (SAP BSIK, MIR4 / invoice status, or a VIM-style intake list).
- Cleared items and payment history (SAP BSAK).
- Payment run results (SAP F110 or the bank payment file).
- AP aging, a deduction / debit-note register, and a TDS deduction register where available.

Every lookup records the source and the extract timestamp. If the extract is older than the client's stale-data threshold (default: one business day), say so in the draft. Do not treat "not on this extract" as proof the invoice was never sent, or as a final "unpaid".

## 3. Hard controls (read first)

1. **Draft only.** Every outgoing reply is a draft. A named AP user approves and sends. This skill never sends mail, posts a portal reply, or messages a vendor.
2. **Never change vendor bank details from a query.** A new beneficiary name, account number, IFSC, SWIFT, or any "urgent account change" in email, portal, or chat is a fraud-risk event. Do not update the master. Do not confirm that details will be changed. Do not repeat full account numbers in a draft. Route to the client's verified callback / vendor-master process (see §6). Acknowledge receipt only.
3. **No ERP writes.** No invoice park or post, payment-block change, residual clearing, or master-data edit.
4. **PII and tax identifiers.** PAN, GSTIN, TAN, bank account, IFSC, and staff names appear in the draft and tracker only as needed to answer. Mask bank accounts (last four digits only) in every draft. Do not attach a full vendor-master extract. Do not paste another vendor's data.
5. **Identity check.** Match the sender domain (or portal login) to the registered vendor email on the master. A mismatch, a public webmail address from a vendor that usually uses a company domain, or a lookalike domain is at most medium confidence — and, if bank or master data is involved, a fraud escalation.
6. **Audit log.** Every query gets a tracker row before the draft is offered (see §7).
7. **No invented tax law.** Restate deductions already posted. For rates, thresholds, or filing dates, use the client's current TDS rate card or tax team. Do not recite statutory rates from memory; they change with Finance Acts.

## 4. Standard operating procedure

1. Ingest the message. Capture channel, sender, timestamp, subject, body, attachments, and any invoice, PO, or UTR numbers.
2. Identify the vendor: vendor code, registered name, GSTIN, PAN, or registered email. If more than one vendor fits, stop and flag.
3. Classify using §5. A message may have a primary and a secondary type (for example short payment + TDS).
4. Look up the sources in §5 for that type. Prefer a live ERP read if connected; otherwise the latest approved export.
5. Score confidence (§6). Below the auto-draft threshold: write a holding draft or an internal escalation note, not a substantive payment or tax commitment.
6. Draft the reply in the client's tone and signature. Include the tracker / ticket ID. Quote only facts from the lookup, with an as-of date.
7. Append the tracker row (status = "Draft ready" or "Escalated").
8. Stop for human approval.

## 5. Query taxonomy, lookups, and reply templates

Use these types unless the client adds codes in setup. Amounts are in INR unless the invoice is in another currency.

### 5.1 Payment status

**Look up:** open items, cleared items, payment run result, payment block. Typical sources: SAP FBL1N / BSIK / BSAK / F110; Oracle Payables invoice and payments; or an AP aging plus payment-register export.

**Need:** vendor, invoice reference (XBLNR), document number, gross amount, due date, block, clearing document, payment date, UTR / payment reference, net paid.

**Draft:** Invoice [ref] for ₹[gross], due [date], is [open — no block, next payment run as of [date] | open — blocked because [reason] | paid on [date] via [method], net ₹[net], UTR [id]]. As of [extract date].

### 5.2 Invoice receipt / invoice status

**Look up:** invoice register or incoming park list, open items, exception queue. Sources: SAP MIR4 / invoice status, VIM or similar if used, the shared intake mailbox log, or an invoice-register spreadsheet.

**If found:** We have invoice [ref] dated [date] for ₹[amt]. Current status: [parked / posted / in approval / in a payment proposal / on hold for [reason]].

**If not found:** We do not have invoice [ref] on our register as of [extract date]. Please resend the tax invoice (PDF), PO number, and IRN / QR where applicable, to [intake address]. State only that it is not on the current register — not that the vendor never sent it.

### 5.3 Remittance advice

**Look up:** the clearing document and payment-run lines for that payment date or UTR. List invoices paid, debit / credit notes, TDS, advances, retention, net amount, and UTR.

**Draft:** On [date] we paid ₹[net] by [NEFT / RTGS], UTR [id], towards: [line list: invoice, gross, deductions, TDS section and amount, net]. Do not repeat a full account number; last four digits and IFSC only if needed.

### 5.4 Short or partial payment and deductions

**Look up:** payment-run line versus invoice gross; debit notes / credit memos; retention; advances; TDS line. Sources: BSAK plus a deduction register, or a remittance export.

**Draft:** Invoice [ref] gross ₹[g]. Deductions: [DN-id ₹x for [reason] | advance [id] | retention]. TDS ₹[t] under [section, if posted]. Net paid ₹[n] on [date], UTR [id]. If a deduction has no supporting document in the extract, do not invent a reason — escalate to the AP processor or buyer.

### 5.5 TDS (Income-tax) queries

**Look up:** TDS amount and section on the payment document or TDS register; taxable value used; Form 16A issue status if the client tracks it.

**Restate, do not advise:**

- When GST is billed separately, TDS is generally computed on the taxable value excluding GST (CBDT Circular No. 23/2017 dated 19 July 2017). If GST is not unbundled, follow the posted document and the tax team.
- Form 16A is issued quarterly from TRACES after the TDS return (Form 26Q / 27Q) is processed. The official issue-by dates are 15 August, 15 November, 15 February, and 15 June of the next financial year ([Income Tax Department explainer](https://www.incometaxindia.gov.in/w/form-16-and-form-16a)).

**Draft:** On invoice [ref], TDS of ₹[amt] was deducted under section [as posted] on taxable value ₹[base]. Net paid ₹[n] on [date]. Form 16A for [quarter, FY] is [already issued on [date] / due to be issued after the quarterly return, by [date]]. This mailbox cannot change the section or rate; disputes go to the tax team.

Do not quote statutory TDS rates or thresholds from memory. Use the client's rate card or the deduction already posted.

### 5.6 GST queries (GSTIN, IRN, GSTR-2B, GST TDS)

**Look up:** invoice exception reason, vendor-master GSTIN versus invoice GSTIN, IRN validation flag, GSTR-2B match if the client provides it.

**Draft:** Invoice [ref] is [on hold / rejected] because [GSTIN mismatch with master | IRN missing or not validated | not appearing in GSTR-2B as of [date]]. Please send a corrected e-invoice / IRN, or a GSTIN update via the vendor-master process, not this mailbox.

**GST TDS (CGST Act section 51):** only notified deductors withhold GST TDS. Do not tell a vendor that GST TDS was or was not "required" unless the client's tax team has documented that the entity is (or is not) a section 51 deductor and the amount is posted. If a GST-TDS line is posted, restate it. If the vendor asks why none was deducted, route to tax.

### 5.7 Bank-detail change (fraud-sensitive)

**Look up:** registered vendor email and existing bank (IFSC + last four only) — solely to detect a mismatch. Do not use the new account data in the message.

**Action:** Classify as bank-change / possible fraud. Log it, notify the escalation contacts, and draft only a non-committal acknowledgement: we do not accept bank-detail changes by email; a colleague will contact the registered vendor account through our verified process. Do not include current or proposed account numbers. Do not process the change.

### 5.8 KYC / vendor-master updates (non-bank)

**Look up:** current master (name, address, GSTIN, PAN, contact).

**Draft:** Master-data changes (legal name, GSTIN, address, contact) are not applied from this mailbox. We have forwarded your request to the vendor-master team, who will follow the client's verification steps. Bank details are never updated from this channel (see 5.7).

### 5.9 Statement of account / reconciliation

**Look up:** open items plus cleared items in the requested period (or all open items plus last 90 days of cleared items if unspecified).

**Draft / attach:** A statement as of [extract date]: open invoices (document, ref, date, due, amount, block) and payments in the period (date, UTR, invoices cleared, net). Ask the vendor to mark unapplied items and reply with their references. If the difference is a single missing invoice or payment, say so; if it is unexplained, escalate.

### 5.10 PO / GRN mismatch holds

**Look up:** invoice, PO number, payment block / exception text, and GRN or service-entry quantity and price if available (MIRO exception, MM goods-receipt docs, or a hold-reason export).

**Draft:** Invoice [ref] against PO [no] is on hold because [price variance / quantity or GRN short / missing GR or SES / missing PO]. It will not enter a payment run until [buyer / stores / AP] clears the mismatch. We have notified [role]. Do not promise a payment date.

### 5.11 Duplicate invoice

**Look up:** an existing document with the same vendor + invoice reference (XBLNR) and / or the same amount and date.

**If already posted or paid:** Invoice [ref] is already on our books as document [belnr] dated [date], status [open / paid on [date], UTR [id]]. We will not process a second copy. If this is a different supply, please send a unique invoice number.

**If a match exists and the new copy is not yet posted:** treat as a duplicate; do not ask AP to park it.

### 5.12 Escalations (legal, MSME delay, stop-supply, second chase, executives)

**Look up:** the underlying invoice status first, then route.

**Draft:** A short factual status plus "your concern has been escalated to [role]". Notify the AP lead (and the MSME / legal contact if the vendor cites the MSMED Act, legal action, or a supply stoppage) inside the client's escalation SLA. Do not admit liability or commit a payment date unless the approver supplies one.

## 6. Confidence thresholds and escalation

Score after lookup, before drafting a substantive reply.

| Confidence | Signals | Action |
| --- | --- | --- |
| High | Single vendor match on code or registered email; unique invoice or payment match; amounts tie; extract fresher than the stale threshold | Draft the standard template. The approver may send it unchanged. |
| Medium | Vendor likely but the invoice number differs slightly; several open invoices; extract stale; partial amount match with a documented deduction | Draft with caveats and the as-of date. The approver must check. |
| Low | Vendor not uniquely identified; sender-domain mismatch; conflicting documents; unexplained short payment; any bank-detail or beneficiary change; legal / MSME / stop-supply language; a request to circumvent process | No substantive commitment. Holding acknowledgement and / or internal escalation only. |

Always escalate (even when the invoice matches):

- Bank or beneficiary changes, lookalike domains, urgency plus new account details → fraud / vendor-master callback, immediately.
- Tax section or rate disputes → tax team.
- PO / GRN / price holds → AP processor plus buyer or stores.
- MSME statutory complaints, legal threats, or stop-supply → AP lead (and legal / MSME role if named), same business day.
- SLA breach or a second chase on the same invoice → AP lead.
- Data not in the ERP or exports → AP processor; do not guess.

## 7. Tracker sheet (audit log)

One workbook or Sheet per client. Append-only rows; no silent overwrites. Minimum columns:

`ticket_id | received_at | channel | vendor_code | vendor_name | sender | query_type | invoice_refs | po_refs | confidence | extract_as_of | action (drafted / escalated / holding) | draft_outcome (approved_unchanged / edited / not_sent) | assigned_approver | escalated_to | sla_due | first_draft_at | first_response_sent_at | closed_at | notes`

Store a link to the source message, not a full PAN or bank dump. Put the ticket ID in the draft subject or first line.

## 8. Getting started — setup questions

Ask these before going live. Contacts are by role; personal names can be filled in later.

1. **Channels:** Which shared AP mailbox (Gmail or Outlook, and the address) is in scope? Is there a vendor portal? Should Slack or Teams be watched, or used only for internal escalation?
2. **Systems of record:** Which ERP (for example SAP or Oracle) and company codes? If there is no ERP connector, which dated export files (vendor master, open items, cleared items, payment run, invoice register, TDS register) will be refreshed, by whom, and how often? What is the stale-data threshold?
3. **SLA and operating hours:** First-response and resolution targets by query type, business timezone (default Asia/Calcutta), and working days. Include a same-day target for bank-change acknowledgements and legal / MSME escalations.
4. **Escalation contacts by role:** AP approver(s); vendor-master / callback owner for bank and KYC; tax team; buyer / stores for PO-GRN holds; AP lead; fraud; legal or MSME contact if any. What are the verified callback steps for bank changes?
5. **Tone, signature, and language:** Reply language (English and / or others), sign-off (team versus individual), disclaimer, and whether remittance advice and statements of account are pasted in the body or attached as a file.

Also collect, if available: the current TDS rate card (do not scrape the web for rates), whether the entity is a GST section 51 deductor, the MSME payment policy, and the tracker Sheet or Excel path.

## 9. Metrics (ROI)

Measure from the tracker, not estimates.

- **Volume:** queries received, by type and channel; percentage classified and draft-ready.
- **Speed:** time to first draft; time to first client-approved response (median and 90th percentile); SLA hit rate.
- **Quality:** percentage of drafts approved and sent unchanged; percentage edited; percentage not sent; reopen or repeat-query rate on the same invoice within 14 days.
- **Hours saved:** `(queries with an approved draft) × (client's agreed minutes per manual reply − average minutes of approver edit time)`. Agree the baseline minutes during setup. Do not invent an industry benchmark.
- **Controls:** bank-change attempts detected and not actioned from email; drafts sent without approval (must be zero); stale-extract answers caught.

Review weekly in the first month of a pilot, then monthly.

## 10. Sources (tax dates and practice only)

- Form 16A issue-by dates: [Income Tax Department explainer](https://www.incometaxindia.gov.in/w/form-16-and-form-16a).
- TDS on taxable value excluding separately billed GST: CBDT Circular No. 23/2017 dated 19 July 2017 (use the official CBDT text; do not rely on a cached copy).
- GST TDS is a notified-deductor regime under CGST Act section 51. Do not assume a private GCC deducts it.

Statutory TDS rates, thresholds, and MSME timelines are not listed here because they change. Use the client's tax and legal guidance.
