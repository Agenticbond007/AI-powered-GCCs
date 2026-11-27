# Answer key — Shipment Exception Handling

> SYNTHETIC DEMO DATA — fictional. Not a real company, person, invoice, bank account, tax identifier, employee, or payment. For playbook testing only.

As of 2026-11-27.

| Shipment | Exception | Facts | Action | Draft |
| --- | --- | --- | --- | --- |
| SH-3101 | Delay | ETA was 2026-11-24 (3 days overdue); supplier-stated arrival 2026-12-02 | Escalate (at the 3-day mark); record 2 Dec as supplier-stated only | Brief to Arun Kumar; no confirmed date |
| SH-3104 | None | Delivered on time, 60 of 60 | No action | None |
| SH-3108 | Short delivery | 3,000 of 5,000 received; balance 2,000 supplier-stated 2026-12-01 on a new ASN | Discrepancy notice; do not close the ASN or amend the PO | Update to Priya Nair; notice to Kaveri |
| SH-3112 | Customs hold | ICD Tughlakabad; corrected country-of-origin declaration outstanding; no clearance date | Same-day escalation to logistics lead | Update to Rahul Bose; no date promised |
| SH-3115 | Damage | 8 received; 2 packs crushed and unusable | Draft claims pack from the warehouse note; do not accept liability | To Sagar Logistics (registered email) and the buyer; warehouse acknowledged |

## Must-pass checks

- No draft confirms 2 December or 1 December as an accepted date.
- SH-3108 quantity is not amended and the ASN is not closed.
- The damage draft does not accept or reject liability or offer a credit.
- SH-3104 is left with no action.
