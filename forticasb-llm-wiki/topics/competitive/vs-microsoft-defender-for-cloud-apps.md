---
title: FortiCASB-SSPM vs Microsoft Defender for Cloud Apps
summary: Feature-by-feature, licensing and gap comparison of FortiCASB-SSPM and Microsoft Defender for Cloud Apps in Microsoft 365 E5, with the differences between the three October 2026 versions of the comparison.
sources: [vs-defender-for-cloud-apps-v1, vs-defender-for-cloud-apps-v2, vs-defender-for-cloud-apps-2026-10, competitive-analysis-forticasb-sspm-2026-08, casb-sspm-newsletter-2026-08-24, sspm-casb-true-players-2026-08]
updated: 2026-10-26
status: current
---

# FortiCASB-SSPM vs Microsoft Defender for Cloud Apps (MDCA)

Three documents dated 2026-10-07 compare the products. They differ in scope, evidence base and conclusions (see "Differences between the three versions" below). The file vs-defender-for-cloud-apps-2026-10 is treated as the newest. No hands-on testing of either product was performed in any version. [src: vs-defender-for-cloud-apps-v2]

## Bottom line stated by the sources

- For an organisation that already owns Microsoft 365 E5, MDCA provides SaaS posture recommendations, OAuth app governance, Cloud Discovery, governance actions and KQL hunting. The documented FortiCASB differences are mostly in operating model (business-owner collaboration on third-party apps, an app-relationship graph, a cross-SaaS identity view), not in detection depth. [src: vs-defender-for-cloud-apps-v2]
- "No area is proven stronger on technical depth" for FortiCASB; the documented differentiators are each "Not found in reviewed docs" on the Microsoft side, which is a weaker statement than "stronger". [src: vs-defender-for-cloud-apps-v2]
- Newest version: Microsoft holds the structural advantage in any E5 account because MDCA is already paid for; Fortinet competes on reach outside Microsoft 365 and on avoiding single-vendor concentration. [src: vs-defender-for-cloud-apps-2026-10]

## Product scope compared

| Item | FortiCASB-SSPM | MDCA |
|---|---|---|
| Documentation basis | FortiCASB-SSPM User Guide dated 2026-09-16 (Documented) [src: vs-defender-for-cloud-apps-v2] | Microsoft Learn pages retrieved 2026-10-07 (Documented) [src: vs-defender-for-cloud-apps-v2] |
| Data plane | API-based, daily scan with on-demand "Trigger Scan" (Documented) [src: vs-defender-for-cloud-apps-v2] | API connectors (about 26) plus log and endpoint sources; inline reverse proxy through Conditional Access App Control (Verified) [src: vs-defender-for-cloud-apps-2026-10] |
| Connection methods | API, Service Account, OAuth; "Create External Link" lets a remote admin finish a connector; supported-app list not in guide [src: vs-defender-for-cloud-apps-v2] | App connectors; multi-instance except M365/Azure; API throttling means large scans take hours to days [src: vs-defender-for-cloud-apps-v2] |
| Packaging | Separate Fortinet subscription; pricing not in guide [src: vs-defender-for-cloud-apps-v2] | Included in M365 E5/A5/G5 and several other suites; also sold standalone [src: vs-defender-for-cloud-apps-v2] |

## Feature-by-feature comparison (version 2, documentation-based)

Result key as used by the source: Microsoft advantage, FortiCASB advantage, Parity, Different approach. [src: vs-defender-for-cloud-apps-v2]

| Area | FortiCASB SSPM (User Guide) | MDCA + E5 (Microsoft Learn) | Result |
|---|---|---|---|
| SaaS discovery | Managed apps via App Store connectors; unmanaged via EDR and other channels (Documented) | Managed via app connectors; unmanaged via Cloud Discovery (Documented) | Parity |
| Shadow SaaS | Sources EDR, firewalls, VPNs; 5-factor priority; Block Application only for SentinelOne; business-justification request to users | Catalog of 31,000+ apps scored on 90+ factors; unsanction and block via Defender for Endpoint (up to about 3 hours), Zscaler, iboss, block script | Microsoft |
| SaaS inventory | Applications page: Managed, Unmanaged, Approved, Rejected, Pending; owner assignment; CSV | SaaS apps tab and OAuth apps tab | Parity |
| SSPM configuration assessment | "Misconfiguration" pillar with per-app risks and Resolve steps; individual checks and benchmarks not enumerated (Requires testing) | Assessments on connected apps with Microsoft benchmarks; 11 GA SSPM connectors, 3 Preview | Microsoft (on evidence) |
| Recommendations | Risks page: Resolve, assign, ticket, history | Secure Score and Exposure Management with Implementation tab | Parity |
| Application risk scoring | Weighted risk average (managed); 5-factor priority (unmanaged); custom "Save as Risk" 1 to 100 | OAuth identity risk score 1 to 100 and privilege level; catalog risk score; SaaS Security Initiative score | Different approach |
| Relationship view | SaaS Graph of core, third-party and shadow apps | Attack surface map and attack paths including OAuth apps (Preview) | Different approach |
| Third-party apps | "3rd Party Apps" page: apps and tokens prioritised by permissions, vendor risk, sensitive-data access, marketplace verification, user activity | App governance inventory for Entra, Google and Salesforce apps | Parity (breadth: test) |
| OAuth permissions | Descriptions and priority; filter by scope | Graph and legacy permissions, delegated vs application, usage (unused 90 days = overprivileged), consent grants (30 days) | Microsoft |
| API tokens | Inventory with roles, type, creation, expiry, last active; expired and never-expire filters | Connector table lists view and revoke permissions; token-expiry inventory not found in reviewed pages | FortiCASB (documented, low confidence) |
| OpenID | Not described (Not found) | Not found | Not comparable |
| Non-human accounts | Identities include "human and non-human entities" but no dedicated detection; "Service Account" is a connection method (Requires testing) | Non-human identities inventory (Entra) | Microsoft |
| Application identity | Identities keyed on a user | Service principals and app registrations are first-class | Different approach |
| Activity | Logins, sharing, deletion, downloads, group changes, provisioning; geo, IP, VPN/proxy; AND/OR filters; save filter as Risk | Activity log, policies with thresholds, anomaly detections, CloudAppEvents | Microsoft (analytics depth) |
| Data access by apps | "Access to sensitive data" derived from permissions and app type | Apps that accessed labelled content (30 days) by sensitivity label | Microsoft |
| PII exposure | PII discovery and classification on file SaaS | Data scan and DLP with Purview labels | Parity (test) |
| Application governance | Saved-filter risks, status automation, workflows | Predefined and custom app policies, ML detections, auto-disable | Microsoft |
| OAuth revocation | Revoke Access for Microsoft, Google, Okta, Salesforce, Atlassian; needs write permission at connect time; irreversible; may lag up to 24 hours | Revoke OAuth app permission for Microsoft 365, Google Workspace, Salesforce | Parity (FortiCASB lists Okta and Atlassian) |
| Business justification | Slack/Teams requests, responses compiled, "Know / Don't know this app" filter | Not found in reviewed pages | FortiCASB |
| Workflow | Triggers, AND/OR conditions, actions; execution log | Activity-policy governance actions; Power Automate playbooks (extra plan) | Different approach |
| Ticketing | Jira and ServiceNow built in; closing a ticket updates the risk | ServiceNow through Power Automate playbook in pages reviewed | Different approach |
| Compliance | Framework tags, executive report; named benchmarks not listed | CIS M365 Foundations, Ransomware, Identity Security, BEC, Zero Trust initiatives | Microsoft |
| Advanced search | Query builder on file metadata and access-control fields; save as Risk; trigger workflow | KQL advanced hunting (up to 30 days raw XDR data; Sentinel for longer) | Different approach (Microsoft more flexible) |
| API | API keys and API documentation | DfCA API tokens; Defender XDR APIs | Parity (test) |
| Entra / Microsoft 365 integration | Entra ID as SSO provider for the console; Microsoft connector read-only or admin mode | Native | Microsoft |
| Defender integration | Microsoft Defender for Endpoint integration not found; SentinelOne block action | Defender for Endpoint, XDR queue, Sentinel | Microsoft |
| Multi-SaaS breadth | Connector list not documented in guide (Requires testing) | 11 GA SSPM connectors, 3 Preview; about 26 API connectors | Microsoft (low confidence) |
| Operations | Cloud console; 4 built-in roles plus custom; SSO | Defender portal with unified RBAC; app governance needs up to 10 hours after enablement | Different approach |

All rows from [src: vs-defender-for-cloud-apps-v2].

### Scenario tally (18 real-world scenarios)

FortiCASB advantage 1, Microsoft advantage 8, Parity 5, Different approach 4; "this reflects documentation depth, not tested product quality". The single FortiCASB win is the business-justification workflow. [src: vs-defender-for-cloud-apps-v2]

### Documented FortiCASB differentiators (version 2, section 4)

1. D1 third-party app collaboration workflow (justification via Slack/Teams, owner assignment, templates, automated status changes): possible edge if business-owned review is required; test.
2. D2 SaaS Graph: different object model, not proven as risk reduction.
3. D3 unified third-party app and token inventory with revoke on five named apps: parity on M365, breadth-only upside elsewhere.
4. D4 cross-SaaS identity profile with six finding types (Shadow SaaS, Admin, Account management, Authentication/MFA, SSO, Inactive): possible, unproven.
5. D5 Shadow SaaS from EDR, firewalls, VPNs: Microsoft wins for an E5 plus Defender for Endpoint shop.
6. D6 workflow canvas (actions: notify via Slack/email, assign) with bi-directional Jira/ServiceNow: different, not a reason to add a product.
7. D7 file-SaaS data protection (quarantine, revoke permissions, delete, notify): parity at best.

[src: vs-defender-for-cloud-apps-v2]

Not counted as differentiators: OpenID relationships (not described), non-human account detection (Requires testing), and SSPM benchmark depth (checks not enumerated). [src: vs-defender-for-cloud-apps-v2]

## MDCA facts relevant to the comparison

- SSPM GA connectors: Microsoft 365, Google Workspace, Salesforce, ServiceNow, GitHub, Okta, Atlassian, Citrix ShareFile, DocuSign, Dropbox, Zendesk; Preview: NetDocuments, Workplace, Zoom; no SSPM listed for Slack, Box, Asana, AWS, Azure (Documented). [src: vs-defender-for-cloud-apps-v2] The 08-13 analysis puts it as "11 of 28+ apps" with Slack, Workday and AWS/Azure/GCP excluded. [src: competitive-analysis-forticasb-sspm-2026-08]
- The SSPM view "recommendations surface in Security Exposure Management via the SaaS Security Initiative (12 metrics)". [src: vs-defender-for-cloud-apps-2026-10]
- The Files page was deprecated on 2024-09-01; older material referencing it is outdated. [src: vs-defender-for-cloud-apps-v2]
- OAuth attack paths, the attack surface map and OAuthAppInfo are Preview; app governance is unavailable when the billing address is in Singapore, Poland, Italy, Qatar, Israel, Spain, Mexico or Taiwan. [src: vs-defender-for-cloud-apps-v2]
- Inline Conditional Access App Control caveats: 50 MB file-inspection cap, IPv4-only, requires Entra ID P1 (Verified, newest version). [src: vs-defender-for-cloud-apps-2026-10]

## Licensing and economics

| Topic | Statement | Source |
|---|---|---|
| E5 inclusion | MDCA CASB, SSPM and OAuth App Governance ship inside M365 E5 and the Microsoft Defender Suite with no separate SSPM or OAuth add-on (Verified) | [src: vs-defender-for-cloud-apps-2026-10] |
| App Governance | Free since June 2023; must be switched on in the Defender portal | [src: vs-defender-for-cloud-apps-2026-10] |
| Hidden dependencies | Inline CAAC needs Entra ID P1; automatic client-side labelling needs AIP P2 (both in E5) | [src: vs-defender-for-cloud-apps-2026-10] |
| Not free for | E3 or sub-E5 customers: standalone MDCA about $3.50/user/month, Defender Suite add-on path about $12/user/month (Third-party estimate) | [src: vs-defender-for-cloud-apps-2026-10] |
| Scenario 1,000 users, 50 apps | E5: about $0 incremental (covers M365 plus about 11 posture apps; remaining about 39 apps only Cloud Discovery). E3: about $42K/yr standalone or about $144K/yr via Defender Suite add-on | [src: vs-defender-for-cloud-apps-2026-10] |
| M365 E5 list price | About $57/user/month commonly cited; not primary-confirmed | [src: vs-defender-for-cloud-apps-2026-10] |
| Items needing validation | Power Automate plan for playbooks (extra licence), Security Exposure Management entitlement, per-service Microsoft 365 licences, Defender for Endpoint network protection for blocking | [src: vs-defender-for-cloud-apps-v2] |
| FortiCASB side | Separate subscription; "Pricing not researched" (v2); "None (quote-only)" (newest); older Fortinet SKU structure is on [pricing-benchmarks.md](pricing-benchmarks.md) | [src: vs-defender-for-cloud-apps-v2] [src: vs-defender-for-cloud-apps-2026-10] |
| Standalone price disagreement | $3.50/user/month appears as a Third-party estimate (newest), as Third-party (08-24), and as "Verified list price" in the 09-21 newsletter | [src: casb-sspm-newsletter-2026-08-24] |

## When each is stronger (version 2 recommendation)

- FortiCASB is strongest when the customer runs many non-Microsoft SaaS apps and wants one neutral view, needs a user-facing business-justification workflow with ticketing, or already runs Fortinet EDR/firewall/VPN telemetry as a discovery source (Other product). [src: vs-defender-for-cloud-apps-v2]
- MDCA is strongest when the estate is centred on Microsoft 365 and Entra and KQL hunting, XDR correlation, Secure Score and catalog-based discovery matter. [src: vs-defender-for-cloud-apps-v2]
- An E5 customer probably does not need FortiCASB when SaaS is mostly Microsoft 365 plus a few Defender-supported apps, or when discovery and inventory are the only drivers. [src: vs-defender-for-cloud-apps-v2]
- Newest-version approach: lead with non-Microsoft SaaS reach, separation of duties (the "Microsoft grading its own homework" concern; Vendor claim), and fabric consolidation; target sub-E5 and mixed-SaaS accounts. [src: vs-defender-for-cloud-apps-2026-10]

## Gaps recorded in the newest version

- No public pricing, detector count, architecture documentation or analyst coverage for FortiCASB-SSPM (Documented gap). [src: vs-defender-for-cloud-apps-2026-10]
- Console unification, single inventory and shared risk scoring are not publicly documented (Not found). [src: vs-defender-for-cloud-apps-2026-10]
- The relationship between FortiDLP and FortiCASB-SSPM DLP scope is not clarified (Not found). [src: vs-defender-for-cloud-apps-2026-10]
- Recommendations: publish a named-app posture list, an architecture note, and a FortiGate/FortiSASE attach price. [src: vs-defender-for-cloud-apps-2026-10]

## Differences between the three versions

| Aspect | v1 (vs-defender-for-cloud-apps-v1) | v2 (vs-defender-for-cloud-apps-v2) | Newest (vs-defender-for-cloud-apps-2026-10) |
|---|---|---|---|
| Title and scope | FortiCASB SSPM vs Defender for Cloud Apps SSPM; SaaS-only, excludes other Fortinet products | Same title and scope | Head-to-head including CASB, SSPM, OAuth governance and licensing economics |
| Fortinet evidence | FortiCASB-SSPM User Guide (2026-09-16) | Same User Guide | Product page and "documentation"; states architecture, detector counts, pricing and analyst coverage are not public |
| Query-language section | Section 9 "LQL vs KQL"; LQL is the FortiCNAPP (Lacework) query language, not credited to FortiCASB; the TEC LQL deck could not be retrieved (bot detection), so any LQL role in FortiCASB is unverified | Replaced by "Search and investigation" (Advanced Search builder vs KQL); LQL material removed; "no free-form query language documented" for FortiCASB | Not discussed |
| Scenario tally | 18 scenarios; tally 1 FortiCASB, 8 Microsoft, 5 parity, 4 different | Same tally | Not applicable (capability table with Strong/Limited ratings) |
| Licensing | "Pricing not researched"; flags needing validation | Same | Models E5 vs E3 economics with estimates |
| Conclusion style | No FortiCASB advantage proven on depth | Same | Microsoft default in E5; Fortinet competes on scope and independence |

Sources for the table: [src: vs-defender-for-cloud-apps-v1] [src: vs-defender-for-cloud-apps-v2] [src: vs-defender-for-cloud-apps-2026-10]

Note: all three files are dated 2026-10-07; this wiki treats the 2026-10 file as the newest. The evidence basis differs: v1 and v2 treat the FortiCASB-SSPM User Guide (dated 2026-09-16) as available, while the newest version states that architecture documentation is not public. Both views are retained and the status is needs-review. The August analysis used an earlier User Guide dated 2026-02-10. [src: competitive-analysis-forticasb-sspm-2026-08]

## Related

- [fortinet-fit-and-gaps.md](fortinet-fit-and-gaps.md)
- [pricing-benchmarks.md](pricing-benchmarks.md)
- [vendor-profiles.md](vendor-profiles.md)
- [../product/licensing-and-skus.md](../product/licensing-and-skus.md)
