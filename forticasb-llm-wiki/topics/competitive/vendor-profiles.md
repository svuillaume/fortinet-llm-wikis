---
title: Competitor vendor profiles
summary: Per-vendor profiles of CASB and SSPM competitors (architecture, SSPM origin, analyst standing, recent events) with evidence flags and the facts on which the sources disagree.
sources: [competitive-analysis-forticasb-sspm-2026-08, casb-sspm-ci-newsletter-2026-08-17, casb-sspm-newsletter-2026-08-24, casb-sspm-newsletter-september-2026, casb-sspm-newsletter-sep2026, forticasb-sspm-vs-market-2026, vs-defender-for-cloud-apps-2026-10, sspm-casb-true-players-2026-08]
updated: 2026-10-26
status: current
---

# Competitor vendor profiles

Profiles summarise what the research documents state. Vendor claims are not independently validated. Prices are on [pricing-benchmarks.md](pricing-benchmarks.md); capability comparisons on [capability-matrix.md](capability-matrix.md).

## Netskope

- Architecture: dual-mode CASB (inline via NewEdge plus API); 3,000+ DLP classifiers, 1,800+ file types (Vendor claim). [src: competitive-analysis-forticasb-sspm-2026-08]
- SSPM: native, delivered in Netskope One; 18 apps with prebuilt posture checks named; dormant/privileged-account mechanics not itemised publicly (as of 08-13). [src: competitive-analysis-forticasb-sspm-2026-08] R141 (Sept 2026) added SSPM findings visibility by app instance. [src: casb-sspm-newsletter-september-2026]
- Next-generation SSPM release with guided remediation mapped to CIS, PCI-DSS, NIST, HIPAA, CSA, GDPR, ISO (Vendor claim). [src: casb-sspm-ci-newsletter-2026-08-17]
- Financials: FY2026 revenue $709.0M (+32%), ARR $811M (+31%), first full year of positive free cash flow, results dated 2026-03-11 (Verified). IPO September 2025 with $992.2M net proceeds. [src: casb-sspm-ci-newsletter-2026-08-17] Listed on Nasdaq (NTSK) at about $8.79B (Verified). [src: casb-sspm-newsletter-sep2026]
- Acquisition and AI: acquired DSPM vendor Dasera; AI Guardrails launched April 2026; Cloud Confidence Index covers 370+ GenAI apps; GitHub third-party app discovery added February 2026 (Verified). [src: casb-sspm-newsletter-sep2026]
- Netskope One DSPM extends to how data stores feed LLMs through RAG and fine-tuning (Vendor claim). [src: casb-sspm-ci-newsletter-2026-08-17]
- Analyst: Leader in 2026 SSE MQ (5th year); Leader in SASE Platforms per the 08-24, 09-16, 09-21 documents but "not found" there in 08-13. [src: casb-sspm-newsletter-2026-08-24] [src: competitive-analysis-forticasb-sspm-2026-08]
- Reported weaknesses: large-enterprise focus, slower innovation pace (SSE MQ commentary); SSPM an add-on module and premium pricing (Third-party). [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-2026-08-24]
- Spreadsheet shortlist rates identity governance Partial: app risk scoring only, no native access-review or offboarding. [src: sspm-casb-true-players-2026-08]

## Zscaler

- Architecture: dual-mode through Zero Trust Exchange (ZIA proxy plus API); sandboxing informed by "200B transactions/day" (Vendor claim). [src: competitive-analysis-forticasb-sspm-2026-08]
- SSPM origin: acquired Canonic Security (February 2023), framed as its CASB+SSPM foundation. [src: competitive-analysis-forticasb-sspm-2026-08] The 08-24 and 09-21 documents describe SSPM as organic or integrated; flagged as a conflict in origin wording. [src: casb-sspm-newsletter-2026-08-24]
- Forrester Wave SSPM Q4 2023: sole Leader. Leader in 2026 SSE MQ (5th year) and, first time, the SASE Platforms MQ. [src: competitive-analysis-forticasb-sspm-2026-08]
- Publicly cites Drift and Gainsight incidents and uses the Klue incident as a worked example. [src: competitive-analysis-forticasb-sspm-2026-08]
- Pricing note: a 35% price increase on some SKUs in 2025 (Third-party). [src: forticasb-sspm-vs-market-2026]
- Not in the 09-16 and 09-21 vendor sets as a full profile (context only). [src: casb-sspm-newsletter-september-2026]

## Palo Alto Networks

- Architecture: inline via Prisma Access plus API; ML-based DLP covering screenshots and conversational AI (Verified per 08-24). [src: casb-sspm-newsletter-2026-08-24]
- SSPM: best-documented identity detectors of the SSE incumbents: Overprivileged, Dormant (30-day default), MFA Misconfiguration, Credential Rotation (30-day) (as of 08-13). [src: competitive-analysis-forticasb-sspm-2026-08] 100+ SaaS apps (Vendor claim). [src: casb-sspm-newsletter-2026-08-24]
- Origin wording conflicts: organic Prisma SASE-native [src: competitive-analysis-forticasb-sspm-2026-08]; "native SSPM added" with Prisma SASE 4.0 in September 2025, claims 90% remediation time reduction (Vendor claim) [src: casb-sspm-newsletter-sep2026]; organic from Prisma Cloud SaaS Security [src: forticasb-sspm-vs-market-2026].
- Closed the $25B CyberArk acquisition on 2026-02-11 (Verified); the 08-17 newsletter notes this does not automatically raise SaaS tenant identity posture. [src: casb-sspm-ci-newsletter-2026-08-17]
- CNAPP (Prisma Cloud) is a separate console; the Dig Security acquisition is infrastructure DSPM, not SaaS SSPM (Vendor claim). [src: competitive-analysis-forticasb-sspm-2026-08]
- Confirmed Drift victim (TechRadar). [src: competitive-analysis-forticasb-sspm-2026-08]
- Pricing weaknesses noted: complex pricing models, narrow use cases (SSE MQ commentary). [src: competitive-analysis-forticasb-sspm-2026-08]

## Skyhigh Security

- Original CASB lineage (McAfee Enterprise); forward and reverse proxy plus 40 API integrations; Unified DLP (EDM/IDM/OCR); FedRAMP High; discovery registry claimed 40,000+ apps and 75+ risk attributes (Vendor claim). [src: competitive-analysis-forticasb-sspm-2026-08] Cloud Registry 40,000+ (Verified in 08-24). [src: casb-sspm-newsletter-2026-08-24]
- SSPM is a CASB sub-feature ("Security Configuration Audit for SaaS"); thinnest public SSPM evidence base of the nine vendors (as of 08-13). [src: competitive-analysis-forticasb-sspm-2026-08]
- RSAC 2026 extensions: hybrid console, browser JavaScript-injection controls, DSPM bundled at base tier (Third-party). [src: casb-sspm-ci-newsletter-2026-08-17]
- 2026 Gartner Critical Capabilities for SSE: #1 in Advanced SSE use case (4.2/5). [src: competitive-analysis-forticasb-sspm-2026-08]
- Omdia Universe DSPM 2025 "Best in Class" (via vendor site). [src: casb-sspm-newsletter-sep2026]

## Microsoft Defender for Cloud Apps (MDCA)

- Four pillars: Cloud Discovery, API App Connectors, Conditional Access App Control (reverse proxy), SSPM (Verified in 08-24). [src: casb-sspm-newsletter-2026-08-24] Full head-to-head: [vs-microsoft-defender-for-cloud-apps.md](vs-microsoft-defender-for-cloud-apps.md).
- SSPM is connector-gated: full support for 11 of 28+ connected apps; Slack, Workday and AWS/Azure/GCP excluded (08-13). [src: competitive-analysis-forticasb-sspm-2026-08]
- Jan 2026: Workday connector moved to View permission only; Salesforce connector ingests Real-Time Event Monitoring; OAuth apps now in Attack Path and Attack Surface Map (Verified). [src: casb-sspm-ci-newsletter-2026-08-17] The 09-16 newsletter dates the Salesforce connector change to June 2026. [src: casb-sspm-newsletter-september-2026]
- SaaS Security Initiative consolidates SSPM into 12 metrics in Defender XDR (Vendor claim in 09-16; documented in October). [src: casb-sspm-newsletter-september-2026] [src: vs-defender-for-cloud-apps-2026-10]
- Entra Permissions Management (CIEM) is being retired. [src: competitive-analysis-forticasb-sspm-2026-08]
- OAuth capability rated best-documented of nine vendors in August: 0 to 100 risk scale extended to Salesforce in 2026, manual and policy revocation. [src: competitive-analysis-forticasb-sspm-2026-08]
- Catalog size differs by document: 33,000+ apps and 90+ risk indicators (08-13); 31,000+ apps and 90+ factors (October); 30,000+ (spreadsheet). [src: competitive-analysis-forticasb-sspm-2026-08] [src: vs-defender-for-cloud-apps-2026-10] [src: sspm-casb-true-players-2026-08]
- Microsoft is not named in the 2025 SSE MQ per secondary sources. [src: vs-defender-for-cloud-apps-2026-10]

## CrowdStrike Falcon Shield (ex-Adaptive Shield)

- Adaptive Shield (founded 2019) acquisition announced 2024-11-06, about $300M (08-17); no true CASB. [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-ci-newsletter-2026-08-17]
- **Conflicting acquisition details**: $300M, closed January 2025 [src: casb-sspm-newsletter-sep2026]; "closed early 2026" [src: casb-sspm-newsletter-2026-08-24]; $214.4M, Nov 2024 [src: forticasb-sspm-vs-market-2026]. The newest document (market comparison, 2026-09-22) gives $214.4M; the 09-21 newsletter gives $300M. Status: needs-review.
- Integration: 150+ out-of-the-box integrations and 200+ supported SaaS apps on the trial page; the 08-17 newsletter says expect a CrowdStrike SE to cite 200+. [src: casb-sspm-ci-newsletter-2026-08-17]
- 2026: first native SSPM plus Next-Gen SIEM integration; AI agent visibility (Vendor claim). [src: casb-sspm-newsletter-september-2026]
- Frost Radar SSPM Leader 2024 (announced 2024-12-09). [src: casb-sspm-ci-newsletter-2026-08-17]

## AppOmni

- Pure-play SSPM, no CASB. **Founded 2018** [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-2026-08-24] vs **2017** [src: forticasb-sspm-vs-market-2026]; the newest source (market comparison) says 2017, unverified.
- Marlin AI launched 2026-05-26 (Verified); AgentGuard (Nov 2025) for ServiceNow AI agents; AISPM; MCP server; connectors for Claude, ChatGPT Enterprise and OpenAI. [src: casb-sspm-ci-newsletter-2026-08-17]
- AppOmni Labs published BodySnatcher (CVE-2025-12420, CVSS 9.3) in January 2026; ServiceNow patched most hosted instances on 2025-10-30. [src: casb-sspm-ci-newsletter-2026-08-17]
- Funding: $126M (Verified, 08-24); $123M total including $70M Series C from Thoma Bravo (09-16). [src: casb-sspm-newsletter-2026-08-24] [src: casb-sspm-newsletter-september-2026]
- Compliance: FedRAMP Moderate (08-17, 08-13); "FedRAMP In Process" (09-21). [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-sep2026]
- Scale claims: 67M+ monitored users, 2B events/day, 43% YoY revenue growth in FY2025 (Verified in 09-21). [src: casb-sspm-newsletter-sep2026]
- Forrester Wave SSPM Q4 2023 Strong Performer. Forrester and Frost placements are listed on [market-landscape.md](market-landscape.md).
- Spreadsheet: identity governance rated Yes via Okta/Entra correlation. [src: sspm-casb-true-players-2026-08]

## Obsidian Security

- Series D: $85M led by Crescent Cove Advisors, $1.1B valuation, announced **2026-08-04**, total raised above $200M, 100+ customers above $100K, 14+ above $1M, 60 of the Fortune 500 (Verified). [src: casb-sspm-ci-newsletter-2026-08-17] The 08-13 analysis dates the $1.1B valuation to August 2025; the 08-17 newsletter is the newer and dates it 2026. [src: competitive-analysis-forticasb-sspm-2026-08]
- Funds earmarked for agentic-AI security across Claude, Copilot Studio and Salesforce Agentforce (the 08-17 verification pass corrected an earlier ChatGPT reference). [src: casb-sspm-ci-newsletter-2026-08-17]
- Named "Integration Risk Management" OAuth product; ISO 42001 certified. [src: competitive-analysis-forticasb-sspm-2026-08]
- September 2025: AI Agent Defense; January 2026: SaaS supply chain security. [src: casb-sspm-newsletter-sep2026]

## Valence Security

- Founded 2021; $32M raised, last a $25M Series A (M12, October 2022); no 2026 funding event confirmed. [src: casb-sspm-ci-newsletter-2026-08-17] [src: competitive-analysis-forticasb-sspm-2026-08]
- Research trap flagged: a February 2026 "Woven Solutions Announces Acquisition of Valence" release concerns a different company (Not found for the SSPM vendor). [src: casb-sspm-ci-newsletter-2026-08-17]
- Broadest non-human identity scope claimed (OAuth, API keys, service accounts); AI-SPM line; MCP server (Vendor claim). [src: casb-sspm-ci-newsletter-2026-08-17]
- Revenue estimate of about $5.8M ARR (2025) is flagged unreliable relative to funding raised. [src: competitive-analysis-forticasb-sspm-2026-08]

## Other vendors named

- **Grip Security** (pure-play SSPM): identity-first shadow IT discovery, access lifecycle automation; rated Yes on discovery and identity governance. [src: sspm-casb-true-players-2026-08]
- **Zluri**: 1,000+ app catalog claim, SaaS management plus security; rated Yes/Yes. [src: sspm-casb-true-players-2026-08]
- **Nudge Security**: documents that it does not directly detect SaaS accounts created with a personal email address (Verified). [src: casb-sspm-ci-newsletter-2026-08-17]
- **Cato Networks**: SASE Leader; acquired Aim Security (September 2025, AI-SPM). Wiz reportedly added SSPM through an acquisition in Q4 2025 (reported valuation $12B+). [src: casb-sspm-newsletter-sep2026]
- Excluded from the August shortlist for Partial/Limited ratings: Obsidian, Valence, Wing, Nudge, DoControl, Adaptive Shield, Reco. [src: sspm-casb-true-players-2026-08] Note: this spreadsheet excludes Obsidian and Adaptive Shield from its "true players" list, while the newsletters treat them as leading specialists. Status: needs-review.

## Fortinet (for reference)

Profile and gaps: [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md). Suridata acquisition details: announced May 2025, Israeli SSPM startup founded 2020 (08-13); about $11.5M raised (09-21) vs about $14M raised (09-22 market comparison); deal value undisclosed, "tens of millions" is an unconfirmed Third-party estimate; the 09-16 newsletter says "In 2026, Fortinet acquired Suridata", contradicting May 2025 elsewhere. [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-sep2026] [src: forticasb-sspm-vs-market-2026] [src: casb-sspm-newsletter-september-2026]

## Related

- [market-landscape.md](market-landscape.md)
- [pricing-benchmarks.md](pricing-benchmarks.md)
- [capability-matrix.md](capability-matrix.md)
- [index.md](index.md)
