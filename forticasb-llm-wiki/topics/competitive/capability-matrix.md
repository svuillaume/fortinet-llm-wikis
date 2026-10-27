---
title: Capability matrix
summary: The capability comparisons and numeric scores that are present in the text extracts of the competitive research, with an explicit note that the 0-5 heatmap grids are missing.
sources: [competitive-analysis-forticasb-sspm-2026-08, casb-sspm-ci-newsletter-2026-08-17, casb-sspm-newsletter-2026-08-24, casb-sspm-newsletter-september-2026, casb-sspm-newsletter-sep2026, forticasb-sspm-vs-market-2026, vs-defender-for-cloud-apps-2026-10, sspm-casb-true-players-2026-08]
updated: 2026-10-26
status: current
---

# Capability matrix

## Extraction limitation

The scored 0-5 heatmap grids (0 Not available, 1 Basic, 2 Limited, 3 Competitive, 4 Strong, 5 Market-leading) are rendered as graphics in the source HTML and are missing from the plain-text extracts of the 2026-08-13 analysis, the 08-17, 08-24, 09-16 and 09-21 newsletters, the 09-22 market comparison and the October Microsoft comparison. No grid values are invented here. The only numeric scores recorded below are those quoted in surrounding prose, and for several vendors no score is available. Scores are described by the sources as their own synthesis, not vendor or Gartner scores. [src: competitive-analysis-forticasb-sspm-2026-08]

## Fortinet FortiCASB-SSPM scores quoted in prose

| Dimension | Score and context | As of | Source |
|---|---|---|---|
| CASB | Raised 2 to 3 ("Competitive") because the Ordering Guide documents data classification, external-sharing controls, activity monitoring and remediation workflows | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| CASB | 3 (based on FortiSASE CASB capabilities in vendor guides) | 2026-09-21 | [src: casb-sspm-newsletter-sep2026] |
| CASB | "Unknown" in the summary matrix (the 09-22 update's heatmap text does not state a CASB score) | 2026-09-22 | [src: forticasb-sspm-vs-market-2026] |
| SSPM | 3 ("reflecting the Suridata acquisition's documented capabilities") | 2026-09-21 | [src: casb-sspm-newsletter-sep2026] |
| SSPM | Raised 2 to 3 in the heatmap while the summary matrix says "Unknown" (internal inconsistency in the same document) | 2026-09-22 | [src: forticasb-sspm-vs-market-2026] |
| Posture Management | Raised 2 to 3 | 2026-09-22 | [src: forticasb-sspm-vs-market-2026] |
| SaaS Discovery | Stays 3 (declined for higher; mechanism real, no breadth figure) | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| SaaS Discovery | Raised 1 to 2 | 2026-09-22 | [src: forticasb-sspm-vs-market-2026] |
| Inline Enforcement | 0 (documented architecture: no traffic rerouting) | 2026-08-13, 08-17 | [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-ci-newsletter-2026-08-17] |
| API Security | 3 (token governance only) | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| API Security | 1 (OAuth-token governance narrower than first-party API security) | 2026-08-17 | [src: casb-sspm-ci-newsletter-2026-08-17] |
| API Security | 1/5, "lowest among platform peers", attributed to sparse documentation | 2026-09-16 | [src: casb-sspm-newsletter-september-2026] |
| Single-Pane-of-Glass | Raised 1 to 2 (FortiAnalyzer, FortiGate, Security Fabric integration in Ordering Guide) | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| CNAPP Integration | 1 then raised to 2 (FortiSOAR connectors for FortiCNAPP and FortiAnalyzer found) | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| CNAPP Integration | 2 (FortiCNAPP exists, no shared inventory or risk score) | 2026-08-17 | [src: casb-sspm-ci-newsletter-2026-08-17] |
| SOAR/Automation | Raised to 5 (FortiSOAR 8.0.0, GA 2026-06-22; scores the separate FortiSOAR product) | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Automated Remediation | 2 (Preview-status Workflows engine; separate from SOAR/Automation) | 2026-08-13 | [src: competitive-analysis-forticasb-sspm-2026-08] |
| GenAI SaaS Security | 1 (no specific capabilities publicly documented) | 2026-09-21 | [src: casb-sspm-newsletter-sep2026] |
| Overall tier | "Mid-pack, Competitive-tier"; not yet top-tier on public documentation | 2026-09-16 | [src: casb-sspm-newsletter-september-2026] |

Scores for the other vendors that appear in prose: Palo Alto scored 3 rather than 5 on Identity / SaaS Access because CyberArk is privileged-access security and not SaaS tenant identity posture. [src: casb-sspm-ci-newsletter-2026-08-17] AppOmni, CrowdStrike, Obsidian and Valence score 0 on Inline Enforcement and SOAR/Automation because of category scope, not quality. [src: casb-sspm-newsletter-september-2026] The 09-16 prose also names AppOmni as strongest on Posture Management and Automated Remediation, Obsidian highest on Threat Protection, Valence highest on OAuth Security, and Microsoft strong on Identity/SaaS Access and Single-Pane-of-Glass, without quoting numbers. [src: casb-sspm-newsletter-september-2026]

## Verbal capability summaries in the text tables

### Summary matrix, 2026-08-13 (CASB / SSPM / integration)

| Vendor | CASB | SSPM | Integration |
|---|---|---|---|
| Netskope | Native, mature | Native, competitive | Single console (Netskope One) |
| Zscaler | Native, mature | Acquired (Canonic, 2023) | Same platform, depth unverified |
| Palo Alto | Native | Native, best-documented identity detectors | Single console for CASB+SSPM; CNAPP separate |
| Skyhigh | Native, mature | Thin, CASB sub-feature | Single console, shallow SSPM |
| Microsoft | Native, mature | Native, connector-gated (11/28 apps) | Fragmented (Entra, Purview, XDR, Secure Score) |
| Fortinet | Native, API-only (no inline) | Acquired (Suridata, 2025), 6 identity-finding types confirmed | Own console; bridges to FortiSIEM, FortiSOAR, third-party SIEM/ticketing; no confirmed FortiCNAPP link |
| AppOmni | None | Native pure-play | N/A |
| Adaptive Shield (CrowdStrike) | None | Native pure-play, acquired by CrowdStrike | SSPM+ITDR fused into Falcon via SIEM |
| Obsidian | None | Native pure-play | N/A |
| Valence | Browser-layer only | Native pure-play | N/A |

[src: competitive-analysis-forticasb-sspm-2026-08]

### Summary matrix, 2026-08-17 (selected columns)

| Vendor | CASB | SSPM | Pricing signal |
|---|---|---|---|
| Fortinet FortiCASB-SSPM | API-mode only; no inline (V) | Native, same SKU (V) | Per-user tiers, declared employee count (V, no public price) |
| Netskope | Native inline + API; mature (V) | Native product line, newer (Vendor claim) | Enterprise quote |
| Palo Alto | Native within Prisma Access (Vendor claim) | Present, not the strategic focus; depth not verified | Enterprise quote |
| Skyhigh | Original CASB lineage; inline + API (Vendor claim) | Thinnest of the SSE group | Enterprise quote |
| Microsoft MDCA | Native; Conditional Access App Control (V) | Native; feeds Security Exposure Management (V) | Bundled in E5 / Defender licensing |
| CrowdStrike Falcon Shield | No true CASB | Acquired, native to Falcon (V) | Falcon module pricing |
| AppOmni | No inline CASB | Native, deepest tier-1 SaaS coverage (V) | Foundations / Advanced / Enterprise |
| Obsidian | No inline CASB | Native, posture + ITDR (V) | Enterprise quote |
| Valence | No inline CASB | Native; SSPM + ITDR + remediation (Vendor claim) | Enterprise quote |

[src: casb-sspm-ci-newsletter-2026-08-17]

### Summary matrix, 2026-09-22 (market comparison, 6 vendors)

| Vendor | CASB | SSPM | Integration | Analyst SSPM | Price transparency |
|---|---|---|---|---|---|
| Netskope | Strong | Competitive | Unified | Not found | Partial |
| Zscaler | Strong | Competitive | Unified | Not found | Partial |
| Palo Alto | Strong | Competitive | Unified | Not found | Partial |
| AppOmni | None | Strong | Partner API | Growth leader (Frost) | Partial |
| Fortinet FortiCASB-SSPM | Unknown | Unknown | Native SKU | Not found | None |
| Adaptive Shield / CrowdStrike | None | Strong | Partner API | Leader (Frost) | None |

[src: forticasb-sspm-vs-market-2026]

### Summary matrix, 2026-10-07 (Microsoft vs Fortinet)

| Vendor | CASB (inline) | CASB (API/Discovery) | SSPM | OAuth governance | XDR/SOAR | Analyst | Pricing transparency |
|---|---|---|---|---|---|---|---|
| Microsoft MDCA | Strong (caveats) | Strong | Competitive (narrow apps) | Strong | Strong (native) | Not found | Bundled in E5 |
| Fortinet FortiCASB-SSPM | Limited (undocumented) | Limited | Competitive (unverified) | Limited | Limited (claimed) | Not found | None (quote-only) |

[src: vs-defender-for-cloud-apps-2026-10] Note the difference from the August view, which scored Fortinet's OAuth/token governance as confirmed and granular; the October document says "Limited" because public documentation is thin. Newer document: October. Status: needs-review.

### Shortlist spreadsheet: discovery and identity governance (August 2026)

| Vendor | Category | SaaS stack detection | Identity governance |
|---|---|---|---|
| Microsoft MDCA | SASE/CASB platform | Yes (network-traffic based, 30,000+ app catalog) | Partial (OAuth governance + UEBA; relies on Entra for IAM) |
| Netskope | SASE/CASB platform | Yes | Partial (app risk scoring only) |
| Palo Alto Prisma Access | SASE/CASB platform | Yes (App-ID based) | Partial (CIEM is infrastructure-focused) |
| AppOmni | Pure-play SSPM | Yes | Yes (Okta/Entra correlation) |
| Grip Security | Pure-play SSPM | Yes (SSO, finance, browser) | Yes (category strength) |
| Zluri | Pure-play SSPM + SaaS management | Yes (1,000+ app catalog) | Yes |
| FortiCASB-SSPM | CASB/SSPM (Security Fabric) | Yes (shadow IT from FortiGate/proxy log ingestion) | UNVERIFIED (admin role sprawl and OAuth risk scoring documented; access-review/offboarding not confirmed) |

[src: sspm-casb-true-players-2026-08] The spreadsheet says Fortinet's shadow-IT discovery comes from FortiGate/proxy log ingestion, while the User Guide readings say EDR and other channels (firewalls, VPNs) feed discovery; see [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md).

## SSPM identity detectors publicly documented (2026-08-13)

| Vendor | Named identity detectors | Source |
|---|---|---|
| Palo Alto | Yes: Overprivileged, Dormant (30-day default), MFA Misconfiguration, Credential Rotation (30-day) | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Zscaler | No | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Netskope | No; 18 apps with prebuilt posture checks | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Microsoft | Partial: MFA gaps via Secure Score; dormant/privileged SSPM detectors not found | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Skyhigh | No | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Fortinet | Yes: six finding types (User Guide dated 2026-02-10) | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Adaptive Shield | Yes: granted vs used OAuth scopes; ITDR | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Obsidian | Yes: Integration Risk Management with continuous scoring | [src: competitive-analysis-forticasb-sspm-2026-08] |
| Valence | Yes: NHI inventory (OAuth, API keys, service accounts) | [src: competitive-analysis-forticasb-sspm-2026-08] |

The 09-16 newsletter gives a different identity-detector column (e.g. Netskope Partial, Fortinet Partial, Skyhigh Partial, Palo Alto Yes), so the August and September views differ; the newer is 09-16 but is based on vendor claims. [src: casb-sspm-newsletter-september-2026]

## OAuth and third-party app risk (2026-08-13)

| Vendor | Inventory | Risk scoring | Revocation | Incident cluster content |
|---|---|---|---|---|
| Microsoft | Mature app drawer | 0-100 scale, extended to Salesforce in 2026 | Manual and policy-driven | Yes |
| Obsidian | Unified Integration Risk Management | Continuous, incl. publisher legitimacy | Workflow-oriented | Partial |
| Adaptive Shield | 3rd Party App Access Inventory, granted vs used scopes | Scope-severity; no numeric scale | Policy-based auto-remediation | Not found |
| Valence | OAuth + API keys + service accounts | Qualitative | Structured retirement workflow | Yes |
| AppOmni | SaaS-to-SaaS visibility incl. NHI | "Blast radius" framing | Not explicitly confirmed | Yes |
| Palo Alto | Third-party plugins dashboard | 1-5 scale (80 attributes, 55 used) | Explicit automated revocation | Yes |
| Netskope | Dedicated 3rd Party Apps view | Five-tier scale | Not confirmed | Not found |
| Zscaler | Canonic-derived | Methodology not detailed | Not explicitly confirmed | Yes |
| Fortinet | Granular: per-token type, roles, creation, expiry, last active | Qualitative, five factors + Vendor Reputation | One-click for five named apps | Not found |
| Skyhigh | "Connected Apps" (M365, Google Drive) | Not found | Not found | Not found |

[src: competitive-analysis-forticasb-sspm-2026-08]

## GenAI and AI-agent security (2026-08-24)

| Vendor | GenAI discovery | GenAI data controls | Autonomous AI | AI agent security |
|---|---|---|---|---|
| Fortinet | OAuth tokens, service accounts, endpoint traffic (Verified) | Data flow monitoring; automated revocation (Verified) | Not available (Gap) | Plugin/add-on discovery (Verified) |
| Netskope | ML-based risk categorisation (Vendor claim) | Inline DLP for GenAI (Vendor claim) | Not available | OAuth visibility (Verified) |
| Palo Alto | App and plugin detection (Vendor claim) | DLP for screenshots and AI (Verified) | Not available | AI agent security (Vendor claim) |
| AppOmni | SaaS + AI visibility (Verified) | Data exposure monitoring (Verified) | Marlin AI, May 2026 (Verified) | AI workflow monitoring (Vendor claim) |
| CrowdStrike | 150+ apps incl. GenAI (Verified) | NHI governance (Verified) | SSPM to Falcon SIEM (Verified) | AI agent visibility (Verified) |
| Valence | SaaS + AI discovery (Vendor claim) | Remediation (Vendor claim) | Not available | AI governance core (Vendor claim) |
| Obsidian | SaaS integration risk (Vendor claim) | Integration risk management (Verified) | Not available | SaaS supply chain (Verified) |
| Zscaler | Shadow SaaS discovery (Vendor claim) | Inline DLP + zero trust (Vendor claim) | Not available | AI controls add-on (Vendor claim) |
| Microsoft | Cloud Discovery (Verified) | DLP via Conditional Access (Verified) | Copilot for Security (separate, Vendor claim) | OAuth app governance (Verified) |

[src: casb-sspm-newsletter-2026-08-24] The 09-21 newsletter lists Fortinet GenAI capabilities as "not publicly documented" (Not found); newer; needs-review. [src: casb-sspm-newsletter-sep2026]

## Inline vs API architecture

| Vendor | Inline | API |
|---|---|---|
| Netskope | Yes (NewEdge) | Yes |
| Zscaler | Yes (ZIA) | Yes |
| Palo Alto | Yes (Prisma Access) | Yes |
| Skyhigh | Yes (forward/reverse proxy) | Yes (40 API integrations) |
| Microsoft | Yes via Conditional Access App Control (50 MB cap, IPv4-only, Entra ID P1) | Yes (about 26 connectors) |
| Fortinet FortiCASB-SSPM | No (inline via separate FortiSASE module) | Yes |
| AppOmni, Obsidian, Valence, CrowdStrike | No | Yes (SSPM) |

[src: competitive-analysis-forticasb-sspm-2026-08] [src: vs-defender-for-cloud-apps-2026-10] The 08-13 analysis recorded MDCA inline mode as "not independently confirmed"; the October comparison verifies it from Microsoft Learn (newer).

## Related

- [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md)
- [vendor-profiles.md](vendor-profiles.md)
- [index.md](index.md)
