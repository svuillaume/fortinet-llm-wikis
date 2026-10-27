---
title: FortiCASB Legacy lifecycle and migration
summary: End-of-order notice for legacy SaaS-only SKUs, the Sept 2026 statement that no dates should be communicated yet, and the migration stance.
sources: [forticasb-legacy-lifecycle-notice, forticasb-commercial-platform-update-v1-5]
updated: 2026-10-26
status: needs-review
---

# FortiCASB Legacy lifecycle and migration

## Dated notice (Product Life Cycle Announcement)
A one-page notice dated **08/03/2026** (date format not stated; day/month order unknown) tells partners that Fortinet intends to discontinue sale of:

| Current SKU | Description | Replacement SKU |
|---|---|---|
| FC2-10-FCASB-145-02-DD | FortiCASB 500 User SaaS-only License | FCx-10-FCSSM-1278-02-DD (FortiCASB subscription for a number of protected users, full capability set, FortiCare Premium included) |
| FC1-10-FCASB-145-02-DD | FortiCASB 100 User SaaS-only License | FCx-10-FCSSM-1278-02-DD |

Milestones listed: End of Orders (EOO) **01 Nov 2026**; last date to purchase a new maintenance contract 01 Nov 2026; last date to extend an existing maintenance contract 01 Nov 2026; product support expires 01 Nov 2026 (or the service contract termination date, whichever is later).

`[src: forticasb-legacy-lifecycle-notice]`

## Stance in the Sept 2026 commercial update (v1.5)
- A formal End of Order and End of Support process "will be initiated separately; **no dates should be communicated until they have been approved and published**."
- FCASB-145 and FCASB-307 SKUs will not be converted or reused for FortiCASB.
- Existing FortiCASB Legacy customers continue to receive support under active subscriptions.
- Migration to FortiCASB is recommended, but customers may remain on Legacy until formal lifecycle guidance is issued.

`[src: forticasb-commercial-platform-update-v1-5]`

## Conflict
The lifecycle notice gives concrete 01 Nov 2026 dates for the FCASB-145 SKUs; the commercial update (September 2026) says no dates are to be communicated. Which document governs is **not resolved in sources**. The notice's issue date is ambiguous (08/03/2026), so ordering the two documents by date is also uncertain. Confirm with the CSE team or Product Management before quoting a date.

## Migration notes available in sources
- Capability parity between Legacy and FortiCASB is not documented in a single place; the commercial update says to contact the CSE team before committing a platform or migration approach where a capability may not yet exist. See [Legacy vs SSPM comparison](legacy-vs-sspm-comparison.md) for the documented differences.
- Migration tooling or data-migration procedures: not found in sources.

## Related
- [Product names and the rebrand](naming-and-rebrand.md)
- [Licensing and SKUs](licensing-and-skus.md)
- [Legacy vs SSPM comparison](legacy-vs-sspm-comparison.md)
