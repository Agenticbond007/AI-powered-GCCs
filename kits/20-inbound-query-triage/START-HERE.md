# START HERE — AI-powered GCCs Free Agent Kits

Twenty-one ready-to-run AI agent kits for transactional work in India's global capability centres (GCCs).
Each kit runs on **emails and exported files only**. No ERP login, no mailbox connection, no system access.

> All demo data is SYNTHETIC DEMO DATA — fictional companies, people and numbers. Never real.

## 1. What a kit is

| Part | Purpose |
| --- | --- |
| `SKILL.md` | The playbook: purpose, inputs, step-by-step process, controls and approval gates, outputs, escalation. Load it into your AI agent as its instructions. |
| `demo-data/` | Synthetic emails (`.eml`) and SAP-style CSV exports for a safe dry run. |
| `expected-outputs/answer-key.md` | What a correct run produces, so you can score the agent. |
| `README.md` | A 10-minute quick start for that kit. |

## 2. The kits

| # | Kit | Area | What it does |
| --- | --- | --- | --- |
| 01 | Vendor Query Resolution | P2P | Answers vendor emails on payment status, TDS, holds and remittances; flags bank-change fraud |
| 02 | Invoice Processing & 3-Way Match | P2P | Reads emailed invoices, matches PO and GRN, proposes parking and exceptions |
| 03 | Vendor Statement Reconciliation | P2P | Reconciles vendor statements to our ledger and explains every difference |
| 04 | Collections Follow-up | O2C | Builds the collections worklist and drafts reminders, acknowledgements and escalations |
| 05 | Cash Application | O2C | Matches bank credits to invoices from remittance emails and a bank file |
| 06 | Bank Reconciliation | R2R | Reconciles bank statement to GL cash book and drafts journal entries |
| 07 | Variance Commentary | FP&A | Drafts evidence-backed actual-vs-budget commentary from a trial balance |
| 08 | GST 2B vs Purchase Register | Tax | Reconciles GSTR-2B to the purchase register and drafts vendor follow-ups |
| 09 | TDS Query Handling | Tax | Answers vendor TDS questions from the TDS registers |
| 10 | HR Employee Query Resolution | HR | Answers people-desk emails with identity checks |
| 11 | Procurement PO Follow-up | Procurement | Drafts supplier expediting and requester updates from the open-PO report |
| 12 | Intercompany Reconciliations | R2R | Reconciles intercompany ledgers, explains every difference and drafts queries and proposed journals |
| 13 | Invoice Releasing & Tracking | O2C | Tracks whether issued invoices have been released and received, and drafts resends and master-data notes |
| 14 | Credit Limit Monitoring | Credit | Assesses utilisation from open AR and pending orders, and drafts hold recommendations and replies to increase requests |
| 15 | Shipment Exception Handling | Supply Chain | Drafts exception briefs, requester updates and claims or discrepancy notes from the shipment tracker |
| 16 | Onboarding Checklist Tracking | HR | Tracks new-hire steps, flags what is still open, and drafts manager, joiner and IT updates |
| 17 | Timesheet Exception Review | HR | Reviews a weekly timesheet export and prepares an exception list for a timekeeping lead |
| 18 | IT Service Desk Triage | IT | Classifies inbound IT emails, assigns a priority and queue, and drafts a first response |
| 19 | Access Request Drafting | IT | Turns intake emails into an access-request pack with roles, approvers, SoD checks and end dates |
| 20 | Inbound Query Triage | Customer Service | Classifies customer emails, routes them to the right queue, and drafts a first response |
| 21 | Refund and Adjustment Drafts | Customer Service | Drafts recommended credits or escalations from refund requests, invoices and policy |

## 3. Quick start — no access required

1. **Unzip** a kit (or the all-kits pack) into a folder.
2. **Open an AI agent** that can read files: Grok Bot, or any LLM agent with file access.
3. **Load the playbook.** Give the agent `SKILL.md` as its instructions and point it at `demo-data/`. Prompt:

   ```
   You are running the "<kit name>" agent kit. Read SKILL.md and follow it exactly.
   Process every file in demo-data/. Produce the outputs SKILL.md lists as drafts only.
   Do not send anything. End with the tracker table and a list of items needing human approval.
   ```

4. **Review the drafts** against `expected-outputs/answer-key.md`. Every must-pass check should hold.
5. **Try your own data.** Replace `demo-data/` with your own exports and a sample of real emails, masked (see section 5). Keep the same column names or tell the agent your mapping.

## 4. The human-approval principle

- **Draft only.** The agent reads, looks up, matches and drafts. A named person approves and sends every message, and posts every entry.
- **No system writes.** The kits never post to an ERP, pay, park, change master data or file a return.
- **Hard stops.** Bank-detail changes by email, unverified senders, unknown bank debits and anything needing tax or legal judgement are escalated, never actioned.
- **Evidence for every claim.** Each draft cites the file, row or email it relied on, plus the extract time.

## 5. Data handling

- **Use exports, not logins.** Run on dated CSV/XLSX exports and saved emails. No credentials are needed or wanted.
- **Mask before you share.** Bank accounts to the last four digits; remove PAN, Aadhaar, salary and personal data that the task doesn't need.
- **Keep data in your environment.** Run the agent inside your organisation's approved tenant or workspace. Don't paste client data into tools your security team hasn't approved.
- **Minimum necessary.** Give each kit only the files listed in its `SKILL.md`.
- **Keep the log.** Save the tracker and the approved drafts as your audit trail.

## 6. From demo to pilot to production

| Stage | What changes | Access |
| --- | --- | --- |
| **Demo** (day 1) | Synthetic data, answer key | None |
| **Shadow pilot** (2–4 weeks) | Your masked exports and a copy of real emails; agent drafts beside your team, you compare | Files only |
| **Live pilot** | Agent reads the shared mailbox or vendor portal queue; exports refreshed daily; drafts approved in the mailbox | Read access to mailbox or portal |
| **Production** | Read-only ERP access (e.g. SAP) replaces exports; approval workflow, monitoring, SLAs and controls testing | Read-only ERP + approval workflow |

Writes to an ERP, if ever enabled, sit behind named human approval and the client's change control.

## 7. Free kits. We deliver the operating model.

**The kits are free. We deliver the AI-powered operating model.**

The kits show what one agent can do. Running agents safely across a GCC takes more: process design, deployment in your environment, governance and controls, the human-approval workflow, scaling across service lines (finance, supply chain, HR, operations and more), and ongoing operation and improvement. That is what AI-powered GCCs offers.

**Contact — AI-powered GCCs**
- A Manjusha, Founder & CEO
- Prerna Bhoga, Chief of Staff
- +91 93409 32225

## 8. License

Free to use, provided as-is, without warranty. See `LICENSE.txt`. Not tax, legal, accounting or HR advice. All demo data is synthetic.
