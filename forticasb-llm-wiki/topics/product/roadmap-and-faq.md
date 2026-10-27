---
title: FortiCASB-SSPM roadmap items and FAQ answers from enablement decks
summary: Roadmap snapshots from the Nov 2025 and early-2026 decks (ETA only), the POC flow, and FAQ answers on licensing basis, deployment, frameworks, GenAI and workflows.
sources: [deck-intro-to-forticasb-sspm-nov25, deck-techtalk-forticasb-sspm-v1-1, deck-forticnapp-and-forticasb-sspm, deck-cnapp-and-sspm-techexpo, deck-forticasb-sales-unofficial-2026-09]
updated: 2026-10-26
status: current
---

# Roadmap items and FAQ answers

Roadmap slides state "All schedules are ETA and subject to change". Nothing here is a commitment.

## Roadmap snapshot A: Nov 2025 deck (periods Q3/Q4 2025, Q1 2026, Q2 2026)
New UI framework; enhanced dashboard; ML applications (self-learning application integration connector); advanced reporting; identities access-permissions audit; enhanced integration to Fortinet Fabric products (for example FortiAI, FortiProxy); enhanced FortiSASE integration (SSPM); CNAPP integration; identities activities and threat management; enhanced DSPM (ML/LLM data classification); malware protection. The slide does not map items to individual quarters in the extracted text. `[src: deck-intro-to-forticasb-sspm-nov25, slide 15]`

## Roadmap snapshot B: TechTalk v1.1 (2026, Q1-Q3)
New UI framework; enhanced dashboard; advanced reporting; FortiFlex licensing; enhanced integration to Fabric products (FortiAI, FortiProxy); non-human identities; agentic AI security; enhanced DSPM (ML/LLM classification); activities ML anomaly detection; identities actions; identities access-permissions audit; shadow SaaS enrichment (one variant: "Shadow SaaS Deep Assessment"); ML auto connector. Per-quarter placement: not captured in text. `[src: deck-techtalk-forticasb-sspm-v1-1, slides 28-29]`

Differences between A and B: B adds FortiFlex licensing, non-human identities, agentic AI security and activities ML anomaly detection; A lists CNAPP integration and malware protection, which B does not repeat. Status `needs-review`: which items shipped is not found in sources.

## POC flow (TechExpo and FortiCNAPP+FortiCASB-SSPM decks)
"POC - Simple and Fast - Initial results within 24h": (1) Kick-off - planning meeting defining success criteria, scope and timeline; (2) Onboarding - connect the solution to selected applications and data points; (3) Initial results and touch point - status meeting; (4) POC summary - results, recommendations and risk analysis. `[src: deck-cnapp-and-sspm-techexpo, slide 29]`, `[src: deck-forticnapp-and-forticasb-sspm, slide 30]`

## FAQ answers (TechTalk v1.1 "Demystifying" slides and notes)
- **How is it licensed?** Per number of SaaS users. (Tier boundaries and minimum in the deck conflict with the SKU tables; see [Licensing](licensing-and-skus.md).)
- **Admin-level API access needed?** In most cases read-only permissions; fewer than 10% of connectors need admin-level access for full functionality, and a reduced-functionality mode exists.
- **Cloud-only?** Yes: SaaS-native, agentless, cloud service; no on-prem or VM deployment. The slide states SOC 2 Type 2 attestation and ISO 27001 certification.
- **Frameworks?** Maps risks and controls to NIST CSF, SOC 2, ISO 27001, GDPR and MITRE ATT&CK (other slides: "over 12 security frameworks").
- **Remediation workflows?** Yes: no-code workflows for ticketing, access revocation, misconfiguration fixes and business-justification steps. (The User Guide's documented workflow actions are Send Notification (Slack, Email) and Assign; see [Workflows](../sspm-user-guide/workflows.md).)
- **GenAI monitoring?** Detects GenAI apps through OAuth tokens (which AI apps have access to corporate data), service accounts (automated/backend GenAI usage) and endpoint-level traffic (AI tools accessed from user devices); lets teams govern usage and revoke unauthorized tools.

`[src: deck-techtalk-forticasb-sspm-v1-1, slides 26, 32-33]`

## Onboarding prerequisite questions (unofficial Sept 2026 sales deck)
The jhurley sales deck's "How it works / Prerequisite Questions" slide lists what to collect before onboarding: corporate IdP (Okta, Entra ID, JumpCloud, Google, OneLogin, etc.); network/endpoint sources (EDR, proxy or CASB — CrowdStrike, SentinelOne, Microsoft Sentinel, FortiGate, etc.); telemetry aggregation platforms (FortiAnalyzer, Azure Event Hub); 3-5 key SaaS applications with a table per app (SSO mandatory/optional/none, IP restricted/behind firewall, custom domain); online file storage (SharePoint, OneDrive, Google Drive); list of internal domains; collaboration platform (Slack, Teams); ticketing tool (Jira, ServiceNow); SIEM (Splunk, etc.); preferred AWS region for the tenant (US/EU); and company name for the dedicated URL. Integration guides with required permissions per application are provided on forticloud.com. Notes on the slide define the Protected User concept (see [Licensing](licensing-and-skus.md)). `[src: deck-forticasb-sales-unofficial-2026-09, slide 13]`

## Related
- [Product overview](overview-and-use-cases.md)
- [Licensing and SKUs](licensing-and-skus.md)
- [Workflows](../sspm-user-guide/workflows.md)
