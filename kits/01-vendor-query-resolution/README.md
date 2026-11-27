# Vendor Query Resolution — Free Agent Kit

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

**What it does:** Reads vendor emails to the AP mailbox, looks up the answer in SAP-style exports, and drafts a reply plus a tracker row for an AP user to approve.

**Module:** P2P · Accounts payable · **Access needed:** none — emails and exported files only.

## What's in this kit

| Path | What it is |
| --- | --- |
| `SKILL.md` | The playbook. Load it into your AI agent as its instructions. |
| `demo-data/` | Synthetic emails and exports for a safe dry run. |
| `expected-outputs/answer-key.md` | What a correct run should produce, scenario by scenario. |

**Inputs:** 15 vendor emails (.eml); vendor master, open items, cleared items and payment run exports (CSV).

**Outputs (drafts for human approval):** 15 reply drafts, a tracker sheet, and fraud or escalation flags.

## Run it in 10 minutes

1. Unzip this kit into a folder.
2. Open your AI agent (Grok Bot or any LLM agent that can read files).
3. Paste this prompt and attach or point it at the folder:

```
You are running the "Vendor Query Resolution" agent kit. Read SKILL.md and follow it exactly.
Process every file in demo-data/. Produce the outputs SKILL.md lists as drafts only.
Do not send anything. End with the tracker table and a list of items needing human approval.
```

4. Compare the agent's drafts with `expected-outputs/answer-key.md`.
5. When the demo looks right, swap `demo-data/` for your own exports (masked) and run again.

## Scenarios covered

| Scenario | What a correct run does |
| --- | --- |
| Payment status / remittance | Quotes status, UTR and clearing from the exports |
| TDS or debit-note short payment | Explains the deduction lines already posted |
| Invoice not found | Asks for a resend; never says it was not sent |
| PO/GRN or GST hold | Explains the hold; promises no date |
| Duplicate invoice | Points to the posted original; does not park again |
| Bank-detail change from lookalike domain | Fraud flag, no change, verified callback only |
| MSME escalation | Factual status, escalates to AP lead |

## Rules that never change

- Draft only. A named person approves and sends every message and posts every entry.
- No system writes. The agent never posts, pays, or changes master data.
- Mask bank accounts, PAN and personal data to what the answer needs.

Part of the free AI-powered GCCs agent kits. See `START-HERE.md` in the all-kits pack.
Free to use, provided as-is, without warranty. Not tax, legal or accounting advice.
