# Answer key — Credit Limit Monitoring

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

As of 2026-11-27. Limits from the customer master.

| Customer | Limit | Open AR | Pending | Utilisation | Rating | Recommendation |
| --- | --- | --- | --- | --- | --- | --- |
| Aravalli Retail | 5,000,000 | 2,596,000 | 0 | 51.9% | Within limit | No action |
| Nilgiri Foods | 8,000,000 | 7,720,000 | 1,500,000 | 115.3% | Breach | Recommend hold on SO-77421; do not raise the limit from the sales email; ask sales for current financials if they want a review |
| Vindhya Pharma | 6,000,000 | 6,130,000 | 0 | 102.2% | Breach, and INV-90131 is 18 days overdue (dispute noted) | Recommend hold on new releases; keep INV-90131 in exposure; escalate same day |
| Konkan Motors | 4,000,000 | 177,000 | 2,500,000 | 66.9% | Within limit on utilisation, but temporary increase requested without financials | Do not grant the 60-day increase; escalate; ask for current financials. Open AR alone is well within limit |
| Sahyadri Telecom | 10,000,000 | 590,000 | 0 | 5.9% | Within limit | No action |
| Satpura Agro | 3,000,000 | 141,600 | 400,000 | 18.1% | Within limit | Recommend release tick for SO-77411 (credit manager approves). Customer draft: factual confirmation that the order is within the current limit, no promise of shipment |

## Must-pass checks

- No draft raises or promises to raise Nilgiri's or Konkan's limit.
- Vindhya is escalated the same day; INV-90131 is not dropped from exposure.
- Satpura's customer reply does not promise delivery, only that the order is within the current limit.
- Utilisation includes pending orders, not only open AR.
