---
title: Licensing, SKUs and pricing for FortiCASB / FortiCASB-SSPM
summary: SKU families, user bands and list prices from three document generations, with the conflicts between them recorded.
sources: [forticasb-commercial-platform-update-v1-5, deck-intro-to-forticasb-sspm-nov25, deck-techtalk-forticasb-sspm-v1-1, expert-talks-forticasb-sspm-suridata, forticasb-legacy-lifecycle-notice, deck-forticasb-sales-unofficial-2026-09]
updated: 2026-10-26
status: current
---

# Licensing, SKUs and pricing

Three generations of documents give different SKU names and prices. The newest (Sept 2026, v1.5) is treated as authoritative; older values are kept for reference. Status is `needs-review` because the documents disagree.

## Current: FortiCASB subscriptions (Sept 2026, commercial update v1.5)

The four FCSSM-1278 SKUs are reactivated for FortiCASB. Original user-volume bands are retained with updated annual list prices. **Minimum order: 50 protected users.** All include the full FortiCASB capability set and FortiCare Premium Support.

| SKU | Protected users | Annual list price per user | Previous |
|---|---|---|---|
| FC1-10-FCSSM-1278-02-DD | 50-499 | $65 | $60 |
| FC2-10-FCSSM-1278-02-DD | 500-1,999 | $59 | $54 |
| FC3-10-FCSSM-1278-02-DD | 2,000-9,999 | $52 | $42 |
| FC4-10-FCSSM-1278-02-DD | 10,000 or more | $45 | $35 |

`[src: forticasb-commercial-platform-update-v1-5]`

Order lines in examples use the `-02-12` suffix (12-month term), for example `FC2-10-FCSSM-1278-02-12`; the SKU tables use `-02-DD`. Both forms appear in the same source.

### Purchase routes
- Standalone FortiCASB through FCSSM-1278 subscription SKUs.
- FortiCASB included with FortiSASE Advanced and Comprehensive subscriptions.
- FortiCASB as an add-on within the FortiCNAPP portfolio; commercial and entitlement implementation "in progress".

See [FortiSASE entitlements and order examples](fortisase-entitlements.md).

### Data-scanning model (under development)
A model focused on new and modified content from customer onboarding onward (rather than automatically scanning all historical data) is being developed. Final behavior and capacity need engineering validation; until confirmed, the current scanning model applies. `[src: forticasb-commercial-platform-update-v1-5]`

### Corroboration from the unofficial Sept 2026 sales deck
The jhurley sales deck (as of 9/5/2026) repeats the same four FCSSM-1278 SKUs with the same bands (50-499 / 500-1,999 / 2,000-9,999 / 10,000+), the 50-user minimum, full capability set and FortiCare Premium Support, and confirms FortiCASB user licenses are included with FortiSASE Advanced and Comprehensive. Its BOM examples use the `-02-DD` suffix. However, the band labels in its BOM examples disagree with the SKU tables ("250-2,499" for FC2, "2,500+" for FC3). `[src: deck-forticasb-sales-unofficial-2026-09, slides 25-29]`

**Protected user definition (deck, slides 13 and 26 notes):** a protected user is a unique user discovered by FortiCASB whose email domain is configured as an internal domain for the customer tenant; counted once across all connected applications. Users on any other domain are external and do not consume a Protected User license.

**Data scanning SKUs removed:** the deck notes (slide 26) that "Data Scanning mentions/skus has been removed entirely from FortiCASB (SSPM/Suridata) latest updates 9/4/2026" — in tension with the v1.5 data-scanning model above; the deck is unofficial so v1.5 stands until confirmed.

**FortiFlex / ELA:** FortiFlex/ELA licensing creates only a FortiSASE entitlement; FortiCASB is a feature of the Advanced/Comprehensive entitlement, so the customer receives the same quantity of FortiCASB protected users; additional protected users require standalone FortiCASB licensing. `[src: deck-forticasb-sales-unofficial-2026-09, slide 30]`

**Deployment:** the tenant is hosted on AWS with the customer's choice of US or EU region, and the customer gets a dedicated URL (example in the deck: `CustomerName.app.suridata.ai` — Suridata domain still in use). `[src: deck-forticasb-sales-unofficial-2026-09, slide 13]`

## Earlier: FortiCASB (Basic) and FortiCASB-SSPM SKUs (Nov 2025 and 2026 TechTalk decks)

| Edition | SKU (deck spelling) | Users | Price |
|---|---|---|---|
| FortiCASB (Basic) | FC1-10-FCSSM-1277-02-DD | 50-499 | $30 |
| | FC2-10-FCSSM-1277-02-DD | 500-1,999 | $27 |
| | FC3-10-FCSSM1277-02-DD | 2,000-9,999 | $23 |
| | FC4-10-FCSSM-1277-02-DD | 10,000+ | $20 |
| FortiCASB-SSPM | FC1-10-FCSSM-1278-02-DD | 50-499 | $60 |
| | FC2-10-FCSSM-1278-02-DD | 500-1,999 | $54 |
| | FC3-10-FCSSM-1278-02-DD | 2,000-9,999 | $42 |
| | FC4-10-FCSSM-1278-02-DD | 10,000+ | $35 |

All described as SaaS multi-tenant with FortiCare Premium Support included. `[src: deck-intro-to-forticasb-sspm-nov25, slide 14]`, `[src: deck-techtalk-forticasb-sspm-v1-1, slide 27]`

An earlier deck (Expert Talks) shows the same prices and bands but with SKU prefix `FCASB` (for example `FC1-10-FCASB-1278-02-DD`, `FC1-10-FCASB-1277-02-DD`). `[src: expert-talks-forticasb-sspm-suridata]`

## Legacy FortiCASB SKUs
- `FC2-10-FCASB-145-02-DD` (500-user SaaS-only licence) and `FC1-10-FCASB-145-02-DD` (100-user SaaS-only licence) are listed for discontinuation with replacement SKU `FCx-10-FCSSM-1278-02-DD`. See [Lifecycle and migration](lifecycle-and-migration.md).
- The commercial update names FCASB-145 and FCASB-307 as SKUs that will not be converted or reused.
- Legacy Admin Guide licence descriptions (SaaS Protection, Data Protection, FortiClient ZTNA users) are in [Legacy licensing](../legacy-admin-guide/licensing.md).

## Conflicts and open points

| Topic | Source A | Source B | Treatment |
|---|---|---|---|
| Price per user | Nov 2025 / 2026 decks: $60 / $54 / $42 / $35 (SSPM) | Commercial update v1.5 (Sept 2026): $65 / $59 / $52 / $45 | Use v1.5 (newer). |
| SKU prefix | `FCASB-1277/1278` (Expert Talks) | `FCSSM-1277/1278` (Nov 2025 deck, v1.5 for 1278) | Use `FCSSM`. |
| Minimum users | TechTalk v1.1 FAQ note: "min 25 users" | v1.5: minimum order 50 protected users; SKU bands start at 50 | Use v1.5. |
| Tier boundaries | TechTalk v1.1 FAQ note: tiers "50-100, 101-1000, 1001-5000, 5001-10000, and 10,000+" | SKU bands 50-499 / 500-1,999 / 2,000-9,999 / 10,000+ | Use SKU bands. |
| BOM band labels (sales deck) | SKU tables: FC2 = 500-1,999; FC3 = 2,000-9,999 | Sales deck BOM examples: FC2 = "250-2,499", FC3 = "2,500+" | Use SKU tables; the deck's own SKU list (slide 26) agrees with the tables. |
| FortiCASB (Basic) | Listed with 1277 SKUs in decks | Not mentioned in v1.5; "full FortiCASB capability set" is attached to 1278 | Availability of Basic after the rename: not found in sources. |

## Related
- [Product names and the rebrand](naming-and-rebrand.md)
- [FortiSASE entitlements](fortisase-entitlements.md)
- [Lifecycle and migration](lifecycle-and-migration.md)
