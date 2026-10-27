---
title: Competitive section index
summary: Entry point for the FortiCASB / FortiCASB-SSPM competitive research pages, with source inventory, evidence flags and the register of cross-document disagreements.
sources: [competitive-analysis-forticasb-sspm-2026-08, casb-sspm-ci-newsletter-2026-08-17, casb-sspm-newsletter-2026-08-24, casb-sspm-newsletter-september-2026, casb-sspm-newsletter-sep2026, vs-defender-for-cloud-apps-v1, vs-defender-for-cloud-apps-v2, vs-defender-for-cloud-apps-2026-10, forticasb-sspm-vs-market-2026, sspm-casb-true-players-2026-08]
updated: 2026-10-26
status: current
---

# Competitive section: FortiCASB / FortiCASB-SSPM

This section compiles the Fortinet SE competitive-research products produced August to October 2026 on the CASB and SSPM market. The SSPM product is being renamed FortiCASB; see [naming and rebrand](../product/naming-and-rebrand.md) and [licensing and SKUs](../product/licensing-and-skus.md) for the product-side view.

## Pages

| Page | Contents |
|---|---|
| [market-landscape.md](market-landscape.md) | Category definitions, vendor groups, analyst placement, market size |
| [vendor-profiles.md](vendor-profiles.md) | One profile per vendor (Netskope, Zscaler, Palo Alto, Skyhigh, Microsoft, CrowdStrike Falcon Shield, AppOmni, Obsidian, Valence, others) |
| [vs-microsoft-defender-for-cloud-apps.md](vs-microsoft-defender-for-cloud-apps.md) | Head-to-head with Defender for Cloud Apps (MDCA), including differences between the three versions |
| [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md) | Documented strengths, weaknesses and UNVERIFIED items |
| [newsletter-digest-2026.md](newsletter-digest-2026.md) | Dated chronological digest of market events |
| [pricing-benchmarks.md](pricing-benchmarks.md) | Price points per vendor with source, date and evidence flag |
| [capability-matrix.md](capability-matrix.md) | Capability comparisons that the text extracts contain |

## Source inventory

| Source name | Document | Date | Notes |
|---|---|---|---|
| competitive-analysis-forticasb-sspm-2026-08 | CASB + SSPM Competitive Analysis (9 vendors, OAuth deep dive) | 2026-08-13 | Uses the FortiCASB-SSPM User Guide dated 2026-02-10 and the Ordering Guide |
| casb-sspm-ci-newsletter-2026-08-17 | CI Newsletter (9 vendors) | 2026-08-17 | Includes a verification-pass correction table |
| casb-sspm-newsletter-2026-08-24 | CI Newsletter (10 vendors, GenAI deep dive) | 2026-08-24 | |
| casb-sspm-newsletter-september-2026 | CI Newsletter (9 vendors, GenAI and Shadow AI) | 2026-09-16 | |
| casb-sspm-newsletter-sep2026 | CI Newsletter (9 vendors) | 2026-09-21 | Newer of the two September newsletters |
| forticasb-sspm-vs-market-2026 | FortiCASB-SSPM vs Market Leaders (6 vendors, pricing and MOQ deep dive) | published 2026-09-10, updated 2026-09-22 | Newest September source |
| vs-defender-for-cloud-apps-v1 | FortiCASB SSPM vs Defender for Cloud Apps SSPM, first version | 2026-10-07 | Contains an LQL vs KQL section |
| vs-defender-for-cloud-apps-v2 | Same title, second version | 2026-10-07 | LQL section replaced by "Search and investigation" |
| vs-defender-for-cloud-apps-2026-10 | FortiCASB-SSPM vs Microsoft Defender for Cloud Apps (E5), licensing focus | 2026-10-07 | Treated as newest of the three (file name and structure differ) |
| sspm-casb-true-players-2026-08 | SSPM_CASB_True_Players.xlsx shortlist | August 2026 | Spreadsheet shortlist |

## Evidence flags used in the sources

The research products tag each claim as Verified, Vendor claim, Analyst assessment, Third-party estimate, or Not found; the Microsoft comparison versions use Documented, Inferred, Marketing claim, Requires testing, Preview, Licensing requires validation, Other product, and Not found in reviewed docs. This wiki keeps those flags and as-of dates next to each claim. [src: casb-sspm-ci-newsletter-2026-08-17] [src: vs-defender-for-cloud-apps-v2]

Scores on the 0 to 5 scale mean 0 Not available, 1 Basic, 2 Limited, 3 Competitive, 4 Strong, 5 Market-leading, and are described by the sources as their own evidence-based synthesis, not vendor or Gartner scores. Low scores often mean "not publicly documented" rather than confirmed absence. [src: competitive-analysis-forticasb-sspm-2026-08]

## Extraction limitation: heatmap grids

The 0 to 5 heatmap grids are not present in the plain-text extracts (the August analysis, both August newsletters, both September newsletters, the market comparison and the October Microsoft comparison all render the grid as graphics). Only scores quoted in surrounding prose are recorded in this wiki; no other scores have been inferred. See [capability-matrix.md](capability-matrix.md).

## Disagreement register (status: needs-review)

Where documents disagree, both statements are recorded and the newer document is named. Details sit on the page named in the last column.

| # | Topic | Statement A (older) | Statement B (newer) | Newer | Page |
|---|---|---|---|---|---|
| 1 | FortiCASB-SSPM CASB score | CASB raised 2 to 3 [src: competitive-analysis-forticasb-sspm-2026-08] | Summary matrix shows CASB "Unknown" [src: forticasb-sspm-vs-market-2026]; the other September newsletter scores CASB 3 [src: casb-sspm-newsletter-sep2026] | forticasb-sspm-vs-market-2026 (2026-09-22) | [capability-matrix.md](capability-matrix.md) |
| 2 | FortiCASB-SSPM SSPM score | August documents describe SSPM as a real, documented capability without a quoted numeric score in prose [src: competitive-analysis-forticasb-sspm-2026-08] | Matrix "Unknown"; prose says heatmap raised SSPM 2 to 3, Posture Management 2 to 3, SaaS Discovery 1 to 2 [src: forticasb-sspm-vs-market-2026]; the 09-21 newsletter scores SSPM 3 [src: casb-sspm-newsletter-sep2026] | forticasb-sspm-vs-market-2026 | [capability-matrix.md](capability-matrix.md) |
| 3 | SaaS Discovery and API Security scores | August: SaaS Discovery stays 3, API Security stays 3 [src: competitive-analysis-forticasb-sspm-2026-08]; 08-17: API Security 1 [src: casb-sspm-ci-newsletter-2026-08-17] | Market doc: SaaS Discovery raised 1 to 2 [src: forticasb-sspm-vs-market-2026]; 09-16: API Security 1/5 [src: casb-sspm-newsletter-september-2026] | September documents | [capability-matrix.md](capability-matrix.md) |
| 4 | Licensing tiers and architecture | Basic/Full tiers, four user bands, 50-user minimum, 12/24/36 months, API-only [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-ci-newsletter-2026-08-17] | "Not found" / "typically included in FortiSASE or sold as add-on SKU" [src: casb-sspm-newsletter-september-2026] [src: forticasb-sspm-vs-market-2026] [src: vs-defender-for-cloud-apps-2026-10] | September and October documents | [pricing-benchmarks.md](pricing-benchmarks.md) |
| 5 | Contract terms | 12/24/36 months [src: casb-sspm-ci-newsletter-2026-08-17] | 1/3/5 years [src: casb-sspm-newsletter-2026-08-24] | casb-sspm-newsletter-2026-08-24 | [pricing-benchmarks.md](pricing-benchmarks.md) |
| 6 | Console and FortiCNAPP integration | Own console, Fabric bridges, no shared inventory with FortiCNAPP [src: competitive-analysis-forticasb-sspm-2026-08]; FortiCNAPP link "Verified" as cloud infra product [src: casb-sspm-newsletter-2026-08-24] | FortiCNAPP listed as Security Fabric integration (Vendor claim) [src: casb-sspm-newsletter-september-2026]; "no public evidence" [src: casb-sspm-newsletter-sep2026]; console unification Not found [src: forticasb-sspm-vs-market-2026] | forticasb-sspm-vs-market-2026 | [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md) |
| 7 | Gartner SSE placement | 2026 SSE MQ (2026-07-29): Fortinet 2026 status not confirmed [src: competitive-analysis-forticasb-sspm-2026-08], later "not among the eight vendors evaluated" [src: casb-sspm-ci-newsletter-2026-08-17] | Market doc cites SSE Leaders from the 2024 MQ [src: forticasb-sspm-vs-market-2026]; October doc cites the 2025 SSE MQ [src: vs-defender-for-cloud-apps-2026-10]; 09-21 says SSE MQ "placed Fortinet below Leaders" [src: casb-sspm-newsletter-sep2026] | Unresolved (different MQ years) | [market-landscape.md](market-landscape.md) |
| 8 | AppOmni founding year | 2018 [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-2026-08-24] | 2017 [src: forticasb-sspm-vs-market-2026] | forticasb-sspm-vs-market-2026 (unverified) | [vendor-profiles.md](vendor-profiles.md) |
| 9 | Vendor prices | See page | See page | Per row | [pricing-benchmarks.md](pricing-benchmarks.md) |
| 10 | Workflows capability | Workflows engine is Preview, notify/assign only [src: competitive-analysis-forticasb-sspm-2026-08] | No-code workflows automate ticketing and access revocation [src: casb-sspm-ci-newsletter-2026-08-17]; workflow canvas documented as notify/assign [src: vs-defender-for-cloud-apps-v2] | vs-defender-for-cloud-apps-v2 (User Guide dated 2026-09-16) | [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md) |
| 11 | GenAI capability | Verified [src: casb-sspm-newsletter-2026-08-24] | Vendor claim [src: casb-sspm-newsletter-september-2026]; Not found, score 1 [src: casb-sspm-newsletter-sep2026] | casb-sspm-newsletter-sep2026 | [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md) |
| 12 | Gartner CASB / SSPM claims | Last CASB MQ 2020; no SSPM Market Guide found [src: casb-sspm-ci-newsletter-2026-08-17] | Netskope "#1 CASB 4 years" [src: casb-sspm-newsletter-2026-08-24]; SSPM Market Guide exists [src: casb-sspm-newsletter-september-2026] | Unresolved | [market-landscape.md](market-landscape.md) |
| 13 | Acquisition facts (Adaptive Shield, Suridata) | $300M, announced Nov 2024 [src: casb-sspm-ci-newsletter-2026-08-17] | $214.4M [src: forticasb-sspm-vs-market-2026]; "closed early 2026" [src: casb-sspm-newsletter-2026-08-24]; Suridata "2026 acquisition" [src: casb-sspm-newsletter-september-2026] | Unresolved | [vendor-profiles.md](vendor-profiles.md) |

## Related

- [market-landscape.md](market-landscape.md)
- [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md)
- [../product/naming-and-rebrand.md](../product/naming-and-rebrand.md)
