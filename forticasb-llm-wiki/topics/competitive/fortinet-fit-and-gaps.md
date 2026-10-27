---
title: Fortinet fit and documented gaps
summary: Documented strengths, weaknesses, integration status and UNVERIFIED items for FortiCASB-SSPM according to the competitive research, with the points on which the research documents disagree.
sources: [competitive-analysis-forticasb-sspm-2026-08, casb-sspm-ci-newsletter-2026-08-17, casb-sspm-newsletter-2026-08-24, casb-sspm-newsletter-september-2026, casb-sspm-newsletter-sep2026, forticasb-sspm-vs-market-2026, vs-defender-for-cloud-apps-v2, vs-defender-for-cloud-apps-2026-10, sspm-casb-true-players-2026-08]
updated: 2026-10-26
status: current
---

# Fortinet fit and documented gaps

This page records what the competitive documents say about FortiCASB-SSPM (the SSPM product, being renamed FortiCASB; see [naming and rebrand](../product/naming-and-rebrand.md)). The documents are evidence-flagged research, not product specifications; anything flagged Vendor claim, Not found or UNVERIFIED should be confirmed with the product team before it is quoted to a customer.

## Product facts as documented

| Fact | Detail | Flag and source |
|---|---|---|
| Origin | Built on the Suridata acquisition, announced May 2025; Israeli SSPM startup | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| Architecture | Agentless, API-based (OAuth 2.0 and SSO connections, REST APIs, webhooks); SaaS-native; no on-premises deployment; no agents or traffic rerouting | Verified (Ordering Guide, User Guide) [src: casb-sspm-ci-newsletter-2026-08-17] |
| Connection types | Exactly three per connector: API, Service Account, OAuth; no proxy/inline type | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| Permission footprint | Read-only in most cases; fewer than 10% of connectors need admin-level access, with a reduced-functionality mode | Verified [src: casb-sspm-ci-newsletter-2026-08-17] |
| Single SKU scope | Shadow-SaaS discovery, SSPM, SaaS DSPM, identity posture, third-party/OAuth control, GenAI governance, threat and activity monitoring, no-code remediation workflows | Verified against ordering guide FCSSM-OG-R03-20260119 [src: casb-sspm-ci-newsletter-2026-08-17] |
| Platform attestations | SOC 2 Type 2 and ISO 27001; mapping to NIST CSF, NIST 800-53, SOC 2, ISO 27001, GDPR, HIPAA, MITRE ATT&CK for SaaS | Verified [src: casb-sspm-ci-newsletter-2026-08-17] |
| Compliance frameworks (product page) | 12+ frameworks including NIST, SOC 2, ISO 27001, CIS, MITRE ATT&CK | Vendor claim [src: forticasb-sspm-vs-market-2026] |
| Identity findings | Six named types: Shadow SaaS, Admin, Account Management, Authentication (MFA), SSO, Inactive (default 180 days) | Verified (User Guide dated 2026-02-10) [src: competitive-analysis-forticasb-sspm-2026-08] |
| Third-party/OAuth | Per-token type, roles, creation, expiry, last active; 5 prioritisation factors (permissions, vendor risk, sensitive-data access, marketplace verification, activity); Vendor Reputation profile | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| Token revocation | One-click Revoke Access for five named apps: Microsoft, Google, Okta, Salesforce, Atlassian; needs Write permission; Owner/Admin only | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| Enforcement outside Workflows | Quarantine, Revoke Permissions, Delete, Notify on saved data-risk queries; EDR-triggered Block Application for SentinelOne only | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| Integrations | FortiSIEM, FortiSOAR, FortiAnalyzer, FortiGate and Security Fabric; Splunk, QRadar, Jira, ServiceNow, Slack; bidirectional ticket sync | Verified [src: casb-sspm-ci-newsletter-2026-08-17] |
| Roles and SSO | 4 built-in roles (Owner, Admin, User, Operator); console SSO via Okta, OneLogin, AD FS, Entra ID, Google Workspace, JumpCloud | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| UI branding | Feb 2026 User Guide screenshots show the "suridata" logo, read as acquired-and-integrating | Observation [src: competitive-analysis-forticasb-sspm-2026-08] |
| Shadow-SaaS discovery source | EDR and other data channels, not inline proxy logs | Verified [src: casb-sspm-ci-newsletter-2026-08-17] |
| Scan cadence | Daily scan with on-demand Trigger Scan | Documented [src: vs-defender-for-cloud-apps-v2] |
| Residency | EU data residency documented for the FortiCASB lineage; no Canadian region documented | Verified / Not found [src: casb-sspm-ci-newsletter-2026-08-17] |

## Documented strengths

- Single-SKU consolidation for existing FortiGate / FortiSASE / Security Fabric customers; described as the most defensible differentiator. [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-ci-newsletter-2026-08-17]
- Read-only-leaning permission footprint, which counters the application-owner objection that blocks SSPM deals. [src: casb-sspm-ci-newsletter-2026-08-17]
- Identity-finding taxonomy and 180-day dormancy default are documented, comparable in transparency to Palo Alto's named detectors (as of 2026-08-13). [src: competitive-analysis-forticasb-sspm-2026-08]
- Endpoint-sourced shadow discovery is architecturally independent of the account email used (Inference to test in a POC; no Fortinet document claims personal-email detection, flag Not found). [src: casb-sspm-ci-newsletter-2026-08-17]
- FortiSOAR 8.0 (GA 2026-06-22): native Agentic AI framework with 19 pre-built agents and MCP support (Verified); this is a separate product, not a FortiCASB-SSPM feature, and the research scores SOAR/Automation separately. [src: competitive-analysis-forticasb-sspm-2026-08]
- Business-justification workflow and SaaS Graph are documented operational edges versus Microsoft (see [vs-microsoft-defender-for-cloud-apps.md](vs-microsoft-defender-for-cloud-apps.md)). [src: vs-defender-for-cloud-apps-v2]
- Fortinet financial momentum: Q2 FY2026 revenue $2.05B, +26% (Verified). [src: casb-sspm-ci-newsletter-2026-08-17] 2026 Cloud Security Report cited for tool sprawl (69%) and 88% hybrid/multi-cloud; FortiCNAPP named Google Cloud Partner of the Year for Workload Security 2026. [src: casb-sspm-newsletter-2026-08-24]

## Documented weaknesses and gaps

| Gap | Detail | Flag and source |
|---|---|---|
| No inline / proxy enforcement | API-only; real-time blocking exists only in the separate FortiSASE-bundled module, which is out-of-band and notification-based per the 08-13 analysis | Architecture gap [src: competitive-analysis-forticasb-sspm-2026-08]. The 08-24 newsletter says inline enforcement is delegated to FortiSASE (Verified) [src: casb-sspm-newsletter-2026-08-24] |
| Workflows engine | 08-13: labelled Preview, only Send Notification and Assign to Security Team; real enforcement lives in separate features | Verified [src: competitive-analysis-forticasb-sspm-2026-08]. 08-17: ordering guide documents no-code workflows that automate ticketing and access revocation [src: casb-sspm-ci-newsletter-2026-08-17]. User Guide 2026-09-16 reading: canvas actions notify/assign (and quarantine/revoke/delete/notify on file searches) [src: vs-defender-for-cloud-apps-v2]. Newer sources agree the canvas is limited; needs-review on the marketing wording |
| Revocation scope | Five named apps; EDR block limited to SentinelOne | Verified [src: competitive-analysis-forticasb-sspm-2026-08] |
| FortiCNAPP link | No shared inventory or risk score; FortiSOAR connectors exist for FortiCNAPP ("Lacework FortiCNAPP") and FortiAnalyzer separately, but no FortiCASB-SSPM connector for FortiSOAR documented | Not found [src: competitive-analysis-forticasb-sspm-2026-08] |
| App connector catalog | No published full list or count; competitors cite 100 to 200+ apps | Gap [src: casb-sspm-newsletter-2026-08-24] |
| Agent identity / behaviour monitoring | No equivalent to AppOmni Agent Inventory / AgentGuard or Marlin AI | Gap [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-2026-08-24] |
| Analyst coverage | No Gartner, Frost or Forrester SSPM/CASB placement; Challenger (down from Leader) in 2026 SASE Platforms MQ, which is not a CASB/SSPM rating | Analyst assessment [src: forticasb-sspm-vs-market-2026] |
| Incident-cluster content | No Fortinet content on the Salesloft/Drift, Gainsight, Klue OAuth cluster; five of nine competitors have it | Marketing-content gap, not a product gap [src: competitive-analysis-forticasb-sspm-2026-08] |
| Risk-score scale | No published numeric OAuth risk-score scale (5 qualitative factors only) | Gap [src: competitive-analysis-forticasb-sspm-2026-08] |
| Pricing transparency | Quote-only, no public list price | Documented gap [src: forticasb-sspm-vs-market-2026] |
| Naming | Three differently architected products carry the "FortiCASB" name: legacy standalone FortiCASB, the FortiSASE-bundled module, and the Basic/Full tiers of the new SKU; FortiDLP "SaaS Data Security" overlaps and is not reconciled | Clarity gap [src: competitive-analysis-forticasb-sspm-2026-08]. See [naming and rebrand](../product/naming-and-rebrand.md) |
| Two DSPM implementations | FortiCASB-SSPM SaaS DSPM is GA; FortiCNAPP cloud DSPM entered Public Preview in March 2026 | Verified [src: casb-sspm-ci-newsletter-2026-08-17] |
| Canadian residency | No Canadian region documented for FortiCASB-SSPM although Fortinet is #2 for Sovereign SASE; escalate to product management | Not found [src: casb-sspm-ci-newsletter-2026-08-17] |
| API Security | OAuth/token governance is a subset of API security; scored low because of narrow scope or sparse documentation | Scored 3 (08-13) vs 1 (08-17, 09-16) [src: competitive-analysis-forticasb-sspm-2026-08] [src: casb-sspm-newsletter-september-2026] |

## UNVERIFIED items

- **Identity governance depth**: documented capability is admin role sprawl detection plus OAuth app risk scoring; full access-review and offboarding automation is "not confirmed. Confirm with product team before quoting". The spreadsheet shortlists SASE/CASB platforms as Partial and pure-plays (AppOmni, Grip, Zluri) as Yes, and shows Fortinet as UNVERIFIED rather than Partial. [src: sspm-casb-true-players-2026-08] The 09-16 and 09-21 newsletters, by contrast, describe automated business justification, risk assignment, ticketing, access revocation and offboarding workflows as a Vendor claim, and 09-16 rates SSPM identity detectors "Partial". [src: casb-sspm-newsletter-september-2026]
- **Personal-email SaaS account detection**: architectural inference only. [src: casb-sspm-ci-newsletter-2026-08-17]
- **GenAI SaaS security**: Verified in 08-17 and 08-24 (GenAI app identification via OAuth tokens, service accounts, endpoint traffic; revoke unauthorised tools); Vendor claim in 09-16 and in the market comparison; "No public documentation found" with a score of 1 in 09-21. In the basic tier GenAI control applies to shadow-SaaS apps only. Newest document (09-21) is the most pessimistic. Status: needs-review. [src: casb-sspm-ci-newsletter-2026-08-17] [src: casb-sspm-newsletter-sep2026]
- **Non-human identity detection**: User Guide says identities include non-human entities but describes no dedicated detection; "Service Account" is a connection method (Requires testing). [src: vs-defender-for-cloud-apps-v2]
- **SSPM check depth and benchmark names**: checks and benchmark names are not enumerated in the guide (Requires testing); no detector count or false-positive rate found. [src: vs-defender-for-cloud-apps-v2] [src: forticasb-sspm-vs-market-2026]
- **FortiSOAR role in FortiCASB-SSPM remediation**: "can consume FortiCASB-SSPM alerts; orchestration roadmap claimed" (Vendor claim in 09-22 and October); 09-21 says "architecturally plausible, not specifically documented" (Not found). [src: forticasb-sspm-vs-market-2026] [src: casb-sspm-newsletter-sep2026]
- **Integration depth with FortiDSPM / FortiCIEM / FortiWeb / FortiAppSec Cloud**: Not found; the 08-17 newsletter notes FortiCSPM, FortiCIEM and FortiDSPM appear as functions inside FortiCNAPP and FortiCASB-SSPM rather than as separate SKUs, so they should not be used as product names. [src: casb-sspm-ci-newsletter-2026-08-17]
- **Detection quality**: no independent detector count, false-positive rate or third-party validation. [src: vs-defender-for-cloud-apps-2026-10]

## Points where the documents disagree

| Topic | Older statement | Newer statement |
|---|---|---|
| Integration with FortiCNAPP | Not found; two of three legs plumbed via connectors (2026-08-13) | 09-16: listed as integrated via Security Fabric (Vendor claim); 09-21 and 09-22: no public evidence / console unification Not found |
| Single console | "Own console, partial" (08-13); "Yes, plus Security Fabric" Verified (08-24) | "Not found" (09-22, October) |
| Product architecture availability | Verified from User Guide and Ordering Guide (08-13, 08-17) | "Not found" (09-22), "not publicly detailed" (October) |
| Genuine automation | "Mostly marketing sleight-of-hand across the market, but not for Fortinet" (08-17) | Workflows Preview, notify/assign only (08-13 and User Guide reading in v2) |

Status of this page: needs-review. Newest documents are the market comparison (2026-09-22) and the October Microsoft comparison (2026-10-07), but they rely on public product pages and so under-report features documented in the User Guide.

## Related

- [capability-matrix.md](capability-matrix.md)
- [vs-microsoft-defender-for-cloud-apps.md](vs-microsoft-defender-for-cloud-apps.md)
- [index.md](index.md)
