---
title: CASB and SSPM market landscape
summary: Category definitions, vendor groupings, analyst placement and market-size data for the CASB, SSPM and SSE/SASE market as of August to October 2026.
sources: [competitive-analysis-forticasb-sspm-2026-08, casb-sspm-ci-newsletter-2026-08-17, casb-sspm-newsletter-2026-08-24, casb-sspm-newsletter-september-2026, casb-sspm-newsletter-sep2026, forticasb-sspm-vs-market-2026, vs-defender-for-cloud-apps-2026-10]
updated: 2026-10-26
status: current
---

# CASB and SSPM market landscape

## Category definitions used by the research

- **CASB**: traffic-layer visibility and control for SaaS (discovery, inline or API enforcement, DLP, threat detection). API-mode-only connectivity is not inline CASB. [src: casb-sspm-ci-newsletter-2026-08-17]
- **SSPM**: continuous assessment of a SaaS tenant's configuration, identity and access posture (misconfiguration, excessive permissions, dormant accounts, MFA gaps, OAuth/token risk, compliance mapping). Shadow-SaaS discovery is an input to SSPM, not SSPM itself. [src: casb-sspm-ci-newsletter-2026-08-17]
- **SSE / SASE**: the network-security-edge platforms where Gartner now evaluates CASB. SSE or SASE Magic Quadrant placement is not treated as evidence of CASB or SSPM strength by any of the sources. [src: competitive-analysis-forticasb-sspm-2026-08]
- **CNAPP vs SSPM**: CNAPP covers cloud infrastructure; DSPM and CIEM exist in infrastructure and SaaS flavours that feed different product lines. [src: casb-sspm-ci-newsletter-2026-08-17]
- **"SaaS Security"** is a marketing umbrella, not a formal analyst category. [src: casb-sspm-newsletter-september-2026]
- **"Integrated CASB + SSPM"**: the test applied is one inventory, one risk score, one policy engine, one remediation workflow, not two SKUs behind one login. [src: casb-sspm-ci-newsletter-2026-08-17]
- The October Microsoft comparison adds two boundary rules: do not confuse inline enforcement with API-connector governance applied after the fact, and do not confuse SSPM depth (named-app posture checks) with Shadow-IT discovery breadth (a catalog size). [src: vs-defender-for-cloud-apps-2026-10]

## Vendor groupings (differ by document)

| Document (date) | Groups |
|---|---|
| competitive-analysis-forticasb-sspm-2026-08 (2026-08-13) | SSE incumbents (Netskope, Zscaler, Palo Alto Networks); platform incumbents (Microsoft, Skyhigh); SSPM specialists (AppOmni, Adaptive Shield, Obsidian, Valence) [src: competitive-analysis-forticasb-sspm-2026-08] |
| casb-sspm-ci-newsletter-2026-08-17 | SSE platforms with attached SSPM (Netskope, Palo Alto, Skyhigh); SaaS-security specialists (AppOmni, Obsidian, Valence); platform consolidators (Microsoft, CrowdStrike Falcon Shield); Fortinet treated as structurally distinct (single SKU, agentless) [src: casb-sspm-ci-newsletter-2026-08-17] |
| casb-sspm-newsletter-2026-08-24 | SSE/SASE platform vendors (including Fortinet); XDR/platform acquirers (CrowdStrike, Microsoft); SSPM specialists [src: casb-sspm-newsletter-2026-08-24] |
| casb-sspm-newsletter-september-2026 (2026-09-16) | Platform SSE/SASE consolidators (Netskope, Palo Alto, Skyhigh, Fortinet); Microsoft as ecosystem incumbent; SSPM-native specialists (AppOmni, CrowdStrike, Obsidian, Valence) [src: casb-sspm-newsletter-september-2026] |
| casb-sspm-newsletter-sep2026 (2026-09-21) | Platform SSE/SASE players; security platform acquirers (CrowdStrike, Microsoft, Skyhigh); SSPM specialists; Fortinet "straddles the platform and acquirer categories" [src: casb-sspm-newsletter-sep2026] |

The documents place Skyhigh, CrowdStrike and Fortinet in different groups; none of the placements is an analyst classification.

## Analyst placement

### What analysts do and do not cover

- Gartner last published a standalone CASB Magic Quadrant on 2020-10-28; CASB was superseded by the SSE Magic Quadrant from 2022. Flag: Verified. [src: casb-sspm-ci-newsletter-2026-08-17] The 2026-08-13 analysis gives the same history (last MQ 2020, folded into SSE from 2022). [src: competitive-analysis-forticasb-sspm-2026-08]
- No Gartner Magic Quadrant for SSPM exists. [src: casb-sspm-ci-newsletter-2026-08-17] [src: vs-defender-for-cloud-apps-2026-10]
- **Disagreement on a Gartner SSPM Market Guide**: the 08-17 newsletter says no Market Guide for SSPM was found for 2025 or 2026 and cites only Emerging Tech research (doc 5635091) [src: casb-sspm-ci-newsletter-2026-08-17]; the 08-24 newsletter says AppOmni and Obsidian are "recognized in Gartner SSPM Market Guide", flag Not found because the detail is paywalled [src: casb-sspm-newsletter-2026-08-24]; the 09-16 newsletter states SSPM is covered only by a Market Guide [src: casb-sspm-newsletter-september-2026]; the 09-21 newsletter lists "Gartner Market Guide for SaaS Security Posture Management, 2025 (doc #5635091)" as a source [src: casb-sspm-newsletter-sep2026]; the October comparison could not confirm a Market Guide naming Microsoft [src: vs-defender-for-cloud-apps-2026-10]. Newer documents (September, October) lean toward a Market Guide existing; the document number 5635091 is described differently by two sources. Status: needs-review.
- **Disagreement on "Gartner #1 CASB"**: the 08-24 and 09-16 newsletters say Netskope is named #1 CASB by Gartner for four consecutive years (Analyst flag) [src: casb-sspm-newsletter-2026-08-24] [src: casb-sspm-newsletter-september-2026]; the 08-17 newsletter says citing a Gartner CASB leader position cites a retired document [src: casb-sspm-ci-newsletter-2026-08-17]. Status: needs-review.

### Gartner Magic Quadrant for Security Service Edge (SSE)

| Item | Statement | Source |
|---|---|---|
| Edition | 2026 edition published 2026-07-29 (Analyst) | [src: casb-sspm-ci-newsletter-2026-08-17] |
| Vendors evaluated | Eight: Broadcom, Cisco, Cloudflare, iboss, Netskope, Palo Alto Networks, Skyhigh Security, Zscaler | [src: casb-sspm-ci-newsletter-2026-08-17] |
| Leaders | Zscaler (5th year), Netskope (5th year), Palo Alto Networks (4th year, per the 08-24 and 09-16 documents); Netskope highest on Completeness of Vision, Zscaler first on Ability to Execute | [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-2026-08-24] |
| Fortinet | 08-13: "2025: Challenger; 2026 SSE MQ status not confirmed" (Not found). 08-17: "not evaluated in this document" (Fortinet is assessed in the SASE Platforms MQ). 09-21: "The SSE MQ also placed Fortinet below Leaders" (Analyst) | [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-sep2026] |
| Skyhigh | Named in 2026 edition; exact quadrant not disclosed (08-13). 09-16 calls it "Named Leader-tier"; 08-13 cites a secondary source for Visionary 2024 and Niche Player 2025 | [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-september-2026] |
| Document ID | 8192429 (08-17) vs #6495271 (09-21) | [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-sep2026] |
| Older-year references | forticasb-sspm-vs-market-2026 cites Netskope, Zscaler and Palo Alto as Leaders in the 2024 SSE MQ; vs-defender-for-cloud-apps-2026-10 says Microsoft is not named in the 2025 SSE MQ (secondary sources) | [src: forticasb-sspm-vs-market-2026] [src: vs-defender-for-cloud-apps-2026-10] |

The newer documents (market comparison, October comparison) cite earlier MQ years, so the disagreement is partly a difference of edition rather than of fact. Status: needs-review.

### Gartner Magic Quadrant for SASE Platforms (2026-07-28)

- Fortinet: Challenger, down from Leader in 2025 (Verified in 08-17; Analyst flag in September documents). [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-september-2026]
- Leaders per 08-13: Zscaler (first year in this MQ), Palo Alto Networks (4th year), Cato Networks (3rd year); Cloudflare Visionary; Netskope "not found" in vendor pages reviewed. [src: competitive-analysis-forticasb-sspm-2026-08]
- Leaders per 09-16 and 08-24: Netskope also a Leader (highest Ability to Execute); Zscaler and Cato Leaders; Fortinet, Cisco and Versa Networks Challengers. [src: casb-sspm-newsletter-september-2026] [src: casb-sspm-newsletter-2026-08-24]
- Trade press (Third-party): Netskope leading, Cato advancing, Palo Alto declining in position; 12 vendors met inclusion criteria. [src: casb-sspm-ci-newsletter-2026-08-17]
- Fortinet counter-points (Vendor-cited): #1 Secure Branch Network Modernization and #2 Sovereign SASE in the 2026 Gartner Critical Capabilities for SASE Platforms. [src: casb-sspm-ci-newsletter-2026-08-17]
- Other SASE references in the 09-21 newsletter: Forrester Wave SASE Solutions Q3 2025 and IDC MarketScape SASE 2026 (Cisco Leader), listed as sources only. [src: casb-sspm-newsletter-sep2026]

### SSPM-specific analyst coverage

| Document | Finding | Flag | Source |
|---|---|---|---|
| Forrester Wave SSPM, Q4 2023 | Zscaler sole Leader; AppOmni, Obsidian Strong Performers (top score in 5 sub-criteria); Spin.AI, Zluri Strong Performers; Fortinet, Netskope, Palo Alto, Microsoft, Skyhigh, Adaptive Shield, Valence not evaluated or not found; 15 vendors evaluated | Analyst assessment | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Frost Radar SSPM 2024 | Adaptive Shield (CrowdStrike) named Leader, announced 2024-12-09 (Innovation 4.8/5, Growth 4.5/5) | Vendor + analyst | [src: casb-sspm-ci-newsletter-2026-08-17] |
| Frost Radar SSPM 2025 | Adaptive Shield / CrowdStrike Leader; AppOmni Growth leader (2nd consecutive year). The 09-16 newsletter says no Frost Radar placement found for AppOmni | Analyst assessment | [src: forticasb-sspm-vs-market-2026] [src: casb-sspm-newsletter-september-2026] |
| GigaOm Radar SSPM 2024 | Valence Security Leader and Fast Mover | Analyst | [src: casb-sspm-ci-newsletter-2026-08-17] |
| Gartner Critical Capabilities for SSE 2026 | Skyhigh #1 of 8 in "Advanced SSE" use case (4.2/5); 4.12/5 Private Application Access; 4.06/5 SaaS and AI Enablement | Analyst | [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-september-2026] |
| Omdia Universe DSPM 2025 | Skyhigh "Best in Class" (via vendor site) | Analyst | [src: casb-sspm-newsletter-sep2026] |
| FortiCASB-SSPM | No Gartner, Frost or Forrester SSPM/CASB placement found; absent from at least one independent 2026 "Top 10 SSPM Tools" roundup that listed pre-acquisition Suridata | Not found | [src: forticasb-sspm-vs-market-2026] [src: competitive-analysis-forticasb-sspm-2026-08] |

## Market size and share

Public market-share data for a combined CASB + SSPM category is not available; every source says so. [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-2026-08-24] [src: casb-sspm-newsletter-september-2026] [src: forticasb-sspm-vs-market-2026]

| Segment | Data point | Source and flag |
|---|---|---|
| CASB size | $11.10B (2025) to $13.12B (2026) to $30.27B (2031E), 18.2% CAGR (Mordor Intelligence, 2026) | Third-party estimate [src: competitive-analysis-forticasb-sspm-2026-08] |
| CASB size | About $15.5B (2025) to about $18.6B (2026), 19.9% CAGR; another estimate $19.6B to $23.3B | Third-party [src: casb-sspm-ci-newsletter-2026-08-17] |
| CASB size | $18.63B (2026) from $15.53B (2025), 19.9% CAGR; $39.15B by 2030 at 20.4% (The Business Research Company) | Third-party [src: casb-sspm-newsletter-2026-08-24] |
| CASB size | $1.5B to $5.8B, 25.82% CAGR 2024 to 2029 (Zluri, Cyberhaven, 2025); Netskope #1 | Third-party estimate [src: forticasb-sspm-vs-market-2026] |
| SSPM size | $484.4M (2025) to $3.53B (2030), 48.7% CAGR (Frost & Sullivan); Kings Research alternative $2.6B (2025) to $7.5B (2032), 16.2% CAGR | Analyst / Third-party [src: casb-sspm-newsletter-september-2026] [src: casb-sspm-newsletter-sep2026] |
| SSPM consolidation | 40+ vendors expected to fall to 6 to 8 by 2030 | Third-party, industry estimate [src: casb-sspm-newsletter-2026-08-24] |
| SASE share | Top six SASE vendors own 72% of a $2.4B 3Q2024 market (Dell'Oro); not CASB/SSPM-specific | Verified headline [src: competitive-analysis-forticasb-sspm-2026-08] |
| Review-site mindshare | Netskope SSPM 5.0% in May 2026 (from 3.8%); AppOmni SSPM 11.7% in July 2026 (from 22.6%) (PeerSpot) | Third-party estimate [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-september-2026] |
| Declined figure | A "~16% AppOmni share" blog figure has no traceable methodology and is not used | Not credible [src: casb-sspm-ci-newsletter-2026-08-17] |
| AI governance spend (adjacent) | $492M (2026) to over $1B by 2030 (Gartner forecast) | Analyst [src: casb-sspm-newsletter-september-2026] |
| Broader network security | Palo Alto 28.4% share (Omdia, Q4 2024); wrong category, listed only to flag conflation | Verified, wrong category [src: competitive-analysis-forticasb-sspm-2026-08] |
| Fortinet scale | Q2 FY2026 revenue $2.05B (+26%), billings +33%, unified SASE billings +35% | Verified [src: casb-sspm-ci-newsletter-2026-08-17] |

## Market direction (as stated by the sources)

- CASB has finished folding into SSE; SSPM is becoming a module inside platforms or a specialist depth play. [src: casb-sspm-ci-newsletter-2026-08-17]
- Differentiation moved from SaaS app counts to AI-agent governance and cross-domain risk correlation; the August and September newsletters name agentic-AI SaaS security as the fast-moving axis. [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-sep2026]
- Table stakes: third-party/OAuth inventory, misconfiguration detection with framework mapping, shadow SaaS discovery, GenAI app identification, Jira/ServiceNow ticketing, agentless API onboarding. [src: casb-sspm-ci-newsletter-2026-08-17]
- Events that could reset the landscape: a Gartner SSPM MQ, a breach through an AI agent's SaaS permissions, Palo Alto fusing CyberArk identity with SaaS posture, Netskope or Palo Alto acquiring an SSPM specialist. [src: casb-sspm-ci-newsletter-2026-08-17]

## Related

- [vendor-profiles.md](vendor-profiles.md)
- [newsletter-digest-2026.md](newsletter-digest-2026.md)
- [index.md](index.md)
