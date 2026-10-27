---
title: Pricing benchmarks
summary: Price points and licensing structures per vendor from the August to October 2026 competitive research, each with source, date and evidence flag, plus the conflicts between documents.
sources: [competitive-analysis-forticasb-sspm-2026-08, casb-sspm-ci-newsletter-2026-08-17, casb-sspm-newsletter-2026-08-24, casb-sspm-newsletter-september-2026, casb-sspm-newsletter-sep2026, forticasb-sspm-vs-market-2026, vs-defender-for-cloud-apps-2026-10, sspm-casb-true-players-2026-08]
updated: 2026-10-26
status: current
---

# Pricing benchmarks

Rule applied by all sources: never present a third-party estimate as an official vendor price. No vendor in the set publishes a numeric CASB or SSPM list price for the full product; the only published figures are Netskope CASB API seat prices and Microsoft's standalone MDCA price (the latter flagged differently by different documents). [src: competitive-analysis-forticasb-sspm-2026-08] [src: forticasb-sspm-vs-market-2026]

## Fortinet FortiCASB-SSPM

| Statement | As of | Flag | Source |
|---|---|---|---|
| Per-SaaS-user subscription; two tiers (Basic "FortiCASB", Full "FortiCASB-SSPM"); four user bands 50 to 499, 500 to 1,999, 2,000 to 9,999, 10,000+; 50-user minimum; 12/24/36-month terms; FortiCare Premium included | 2026-08-13 | Verified (structure; no dollar figure) | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Same structure, billed on customer-declared employee count validated by Fortinet; ordering guide revision R03 dated 2026-01-19; basic tier covers shadow discovery, data discovery, DSPM, GenAI for shadow apps only; Full tier adds SaaS Graph, third-party app control, identity posture, threat/activity management, workflows, business-user justification, SSPM, ticketing | 2026-08-17 | Verified (structure); price not published | [src: casb-sspm-ci-newsletter-2026-08-17] |
| Four user bands; terms "1/3/5 yr"; "Enterprise quote required" | 2026-08-24 | Verified (bands), Not found (price) | [src: casb-sspm-newsletter-2026-08-24] |
| "Typically included within a FortiSASE subscription or sold as a separate add-on SKU"; no per-seat list price located | 2026-09-16 | Vendor claim / Not found | [src: casb-sspm-newsletter-september-2026] |
| FortiSASE about $90/user/year list; real TCO about $33/user/month after add-ons; minimum 50 users; channel-only (this is FortiSASE, not FortiCASB-SSPM) | 2026-09-21 | Third-party estimate | [src: casb-sspm-newsletter-sep2026] |
| Pricing model and MOQ not publicly disclosed; enterprise-quote-only; speculative range $100K to $130K/yr for 1,000 users and 50 apps, derived by assuming a 20 to 30% bundling discount against Netskope plus AppOmni | 2026-09-22 | Not found; the range is inference only | [src: forticasb-sspm-vs-market-2026] |
| Quote-only; no public pricing transparency | 2026-10-07 | Not found | [src: vs-defender-for-cloud-apps-2026-10] |
| "Quote via partner/NSE" | August 2026 | spreadsheet entry | [src: sspm-casb-true-players-2026-08] |
| G2 "Perceived Cost Rating" $$$$$ (highest tier) | 2026-08-13 | Third-party sentiment, not a price | [src: competitive-analysis-forticasb-sspm-2026-08] |

**Conflict (needs-review)**: the August documents describe a verified tier and user-band structure with a 50-user minimum, while the September and October documents state the pricing model is not publicly disclosed or that the product is bundled with FortiSASE. The two are not strictly contradictory (structure vs price) but the minimum, terms (12/24/36 months vs 1/3/5 years) and packaging statements differ. Newer documents: September 2026 and the October comparison. See [licensing and SKUs](../product/licensing-and-skus.md) for the product-side view.

## Competitor price points

### Microsoft Defender for Cloud Apps

| Statement | As of | Flag | Source |
|---|---|---|---|
| Not published as standalone SKU; commonly bundled in M365 E5 / E5 Security add-on | 2026-08-13 | Third-party / user-reported | [src: competitive-analysis-forticasb-sspm-2026-08] |
| $3.50/user/month (about $42/user/yr), standalone SKU | August 2026 | spreadsheet entry | [src: sspm-casb-true-players-2026-08] |
| Included in M365 E5 / EMS E5; standalone about $3.50/user/month | 2026-08-24 | Third-party | [src: casb-sspm-newsletter-2026-08-24] |
| Included in E5 / EMS E5 (Verified); standalone price "not separately itemized in public sources" | 2026-09-16 | Verified / Not found | [src: casb-sspm-newsletter-september-2026] |
| $3.50/user/month standalone, bundled in M365 E5; sets the price floor | 2026-09-21 | Verified (list price from reseller sources) | [src: casb-sspm-newsletter-sep2026] |
| Included in E5 at no extra cost (Verified); about $3.50/user/month standalone and about $12/user/month Defender Suite add-on for E3 (Third-party estimate); M365 E5 about $57/user/month not primary-confirmed | 2026-10-07 | Mixed | [src: vs-defender-for-cloud-apps-2026-10] |

Disagreement: the same $3.50 figure is Verified in 09-21, Third-party in 08-24 and October, and "not separately itemized" in 09-16. Newest source: October comparison (Third-party estimate).

### Netskope

| Statement | As of | Flag | Source |
|---|---|---|---|
| Base SWG+CASB about $4 to $8/user/month; full platform $15+/user/month (3-year commit, procurement-aggregator estimate) | 2026-08-13 | Third-party estimate | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Base about $50 to $98/user/yr plus CASB API add-on about $52.50/seat/yr | August 2026 | spreadsheet entry | [src: sspm-casb-true-players-2026-08] |
| Mid-tier about $9 to $14/user/month; full $15+; standalone SSPM not listed | 2026-08-24 | Third-party | [src: casb-sspm-newsletter-2026-08-24] |
| Published bundle tiers $4 to 8 (base, 3-year), $9 to 14 (mid, adds ZTNA, DLP, basic SSPM), $15+ (full): Vendor claim. CASB API: $52.50/app seat/yr (100 to 999 users), $19.44 (1K to 2.5K), $12.40 (5K to 10K): Verified | 2026-09-16 | Mixed | [src: casb-sspm-newsletter-september-2026] |
| Same bands classed Third-party est.; CASB API about $52.50/app-seat/yr | 2026-09-21 | Third-party est. | [src: casb-sspm-newsletter-sep2026] |
| $4 to 8 base (1,000 users), $9 to 14 mid, $15+ full; 3-year terms common; est. $48K to $84K/yr base for 1,000 users; $150K to $170K/yr mid-tier pilot scenario | 2026-09-22 | Third-party estimate | [src: forticasb-sspm-vs-market-2026] |

Disagreement: the same price bands carry Third-party estimate flags in four documents and Vendor claim in 09-16; the CASB API seat price is Verified in 09-16 but Third-party in the others.

### Zscaler

| Statement | As of | Flag | Source |
|---|---|---|---|
| ZIA base about $8 to $12/user/month; separate CNAPP "Posture Control" about $15K to $50K/yr mid-size | 2026-08-13 | Third-party estimate | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Base CASB about $72/user/yr; Advanced $160/user/yr; Sandbox up to $325/user/yr; minimum 50 users for CASB Advanced; 35% price increase on some SKUs in 2025; 1,000-user pilot $120K to $180K/yr (est. $72K to $325K+) | 2026-09-22 | Third-party estimate | [src: forticasb-sspm-vs-market-2026] |

### Palo Alto Networks

| Statement | As of | Flag | Source |
|---|---|---|---|
| Prisma Access broadly estimated $1,000 to $10,000+/yr depending on scope | 2026-08-13 | Third-party, low confidence | [src: competitive-analysis-forticasb-sspm-2026-08] |
| 5,000 seats over 3 years about $8.0M total | August 2026 | spreadsheet entry | [src: sspm-casb-true-players-2026-08] |
| Enterprise quote | 2026-08-24, 09-16 | Not found | [src: casb-sspm-newsletter-2026-08-24] [src: casb-sspm-newsletter-september-2026] |
| Prisma SASE $60 to $200/user/yr by tier; seven-figure contracts typical at 5,000+ seats | 2026-09-21 | Third-party est. | [src: casb-sspm-newsletter-sep2026] |
| Prisma Cloud credit-based: Business Edition 100 credits = $9K/yr; Enterprise 100 credits = $18K/yr; pilot estimate $18K to $36K/yr | 2026-09-22 | Vendor claim | [src: forticasb-sspm-vs-market-2026] |

Disagreement: estimates range from $1K to $10K+ per year to about $8.0M over three years for 5,000 seats; the scopes differ (Prisma Access vs Prisma SASE vs Prisma Cloud credits) and cannot be reconciled. Newest: 09-22 market comparison.

### Skyhigh Security

| Statement | As of | Flag | Source |
|---|---|---|---|
| Three unnamed tiers (Essential, Advanced, Complete), no dollar figures; TrustRadius lists no pricing plans or free trial | 2026-08-13 | Not found | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Starting about $160/user/yr; custom per-user tiers | 2026-09-21 | Third-party est. | [src: casb-sspm-newsletter-sep2026] |

### AppOmni

| Statement | As of | Flag | Source |
|---|---|---|---|
| Average contract value about $96,612/yr, deals up to about $100K | 2026-08-13 | Third-party estimate | [src: competitive-analysis-forticasb-sspm-2026-08] |
| About $7,500 per 12 months per 100 users/app; enterprise custom | August 2026 | spreadsheet entry | [src: sspm-casb-true-players-2026-08] |
| Three packages (Foundations, Advanced, Enterprise); 90-day Foundations trial plus a free attack-surface assessment | 2026-08-17 | Verified | [src: casb-sspm-ci-newsletter-2026-08-17] |
| About $75/user/yr (AWS Marketplace reference), average deal about $97K/yr | 2026-09-21 | Third-party est. | [src: casb-sspm-newsletter-sep2026] |
| Per-user-per-app; about $75/user example; pilot estimate $75K to $100K/yr (assumes $1.50 per user-app pair) | 2026-09-22 | Third-party estimate | [src: forticasb-sspm-vs-market-2026] |

### Others

- CrowdStrike Falcon Shield: bundled into Falcon module pricing; enterprise quote; no public per-seat price (Not found). [src: casb-sspm-newsletter-sep2026] Pre-acquisition tracker "Custom plan" is stale 2021 data. [src: competitive-analysis-forticasb-sspm-2026-08]
- Obsidian Security: demo or quote only (Not found); 100+ customers above $100K and 14+ above $1M annual contract value (Verified, per Series D statements). [src: casb-sspm-ci-newsletter-2026-08-17]
- Valence Security: quote only; revenue estimate about $5.8M (2025), flagged low-confidence. [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-sep2026]
- Grip Security: about $300,000/yr (0 to 50,001+ users). [src: sspm-casb-true-players-2026-08]
- Zluri: tiered, mid-market accessible. [src: sspm-casb-true-players-2026-08]
- SME SSPM band: roughly $5,000 to $15,000/yr entry vs $50,000 to $200,000 for enterprise (Third-party, directional only). [src: casb-sspm-ci-newsletter-2026-08-17]

## 1,000-user, 50-app scenario (2026-09-22)

| Vendor | Estimated annual cost | Flag |
|---|---|---|
| Netskope mid-tier | $150K to $170K | Third-party estimate |
| Zscaler (Posture module) | $120K to $180K | Third-party estimate |
| Palo Alto Prisma Cloud | $18K to $36K | Vendor claim |
| AppOmni | $75K to $100K | Third-party estimate |
| FortiCASB-SSPM | Not found; $100K to $130K speculative | Inference only |
| Adaptive Shield / CrowdStrike | Not found | Not found |

[src: forticasb-sspm-vs-market-2026] Microsoft: E5 about $0 incremental; E3 about $42K/yr standalone or about $144K/yr via Defender Suite add-on (Third-party estimate). [src: vs-defender-for-cloud-apps-2026-10]

## Pricing dynamics noted

- Microsoft's bundled or $3.50 standalone price "sets the price floor" for SSPM. [src: casb-sspm-newsletter-sep2026]
- Netskope and Zscaler: 3-year terms and add-on modules; Zscaler 35% increase in 2025; industry trend 5 to 10% annual increases (not publicly disclosed). [src: forticasb-sspm-vs-market-2026]
- Fortinet's lack of a published starting price prevents fair TCO modelling in RFPs (Documented gap). [src: forticasb-sspm-vs-market-2026]

## Related

- [vs-microsoft-defender-for-cloud-apps.md](vs-microsoft-defender-for-cloud-apps.md)
- [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md)
- [../product/licensing-and-skus.md](../product/licensing-and-skus.md)
