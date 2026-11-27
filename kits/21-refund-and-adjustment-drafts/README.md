# Refund and Adjustment Drafts — Free Agent Kit

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

**What it does:** Reads refund and adjustment requests against invoices, prior refunds and policy, and drafts a recommended credit or an escalation for a named lead to approve.

**Module:** Customer service · Adjustments · **Access needed:** none — emails and exported files only.

## What's in this kit

| Path | What it is |
| --- | --- |
| `SKILL.md` | The playbook. Load it into your AI agent as its instructions. |
| `demo-data/` | Synthetic emails and exports for a safe dry run. |
| `expected-outputs/answer-key.md` | What a correct run should produce, scenario by scenario. |

**Inputs:** 5 emails; orders and invoices, prior refunds, refund policy and customer master (CSV).

**Outputs (drafts for human approval):** Adjustments log, internal recommendations, customer holding or explanation drafts.

## Run it in 10 minutes

1. Unzip this kit into a folder.
2. Open your AI agent (Grok Bot or any LLM agent that can read files).
3. Paste this prompt and attach or point it at the folder:

```
You are running the "Refund and Adjustment Drafts" agent kit. Read SKILL.md and follow it exactly.
Process every file in demo-data/. Produce the outputs SKILL.md lists as drafts only.
Do not send anything. End with the tracker table and a list of items needing human approval.
```

4. Compare the agent's drafts with `expected-outputs/answer-key.md`.
5. When the demo looks right, swap `demo-data/` for your own exports (masked) and run again.

## Scenarios covered

| Scenario | What a correct run does |
| --- | --- |
| In-window unused return | Recommend a proportionate credit, with working; do not process |
| Already refunded | Do not pay twice; cite the UTR |
| Duplicate invoice | Recommend a credit on the duplicate only |
| Out-of-window goodwill | Do not approve; route the dispute and any goodwill |
| Chargeback threat | Escalate to finance the same hour; do not also refund |

## Rules that never change

- Draft only. A named person approves and sends every message and posts every entry.
- No system writes. The agent never posts, pays, or changes master data.
- Mask bank accounts, PAN and personal data to what the answer needs.

Part of the free AI-powered GCCs agent kits. See `START-HERE.md` in the all-kits pack.
Free to use, provided as-is, without warranty. Not tax, legal or accounting advice.
