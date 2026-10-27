---
title: FortiCASB (SSPM platform) overview and use cases
summary: What the FortiCASB-SSPM / FortiCASB platform does, its six use-case areas, data-collection architecture and capability pillars.
sources: [forticasb-sspm-user-guide-2026-02, forticasb-data-sheet-v0-10, expert-talks-forticasb-sspm-suridata, deck-intro-to-forticasb-sspm-nov25, deck-intro-to-forticasb-sspm, deck-saas-security-sspm-final, deck-techtalk-forticasb-sspm-v1-1, deck-forticasb-sales-unofficial-2026-09]
updated: 2026-10-26
status: current
---

# FortiCASB (SSPM platform) overview and use cases

## What it is
A cloud-delivered, agentless platform that connects to SaaS applications, identity providers and network/endpoint telemetry sources to map the SaaS stack, find risks, prioritize them and drive remediation. The data sheet draft describes it as unifying **SaaS Security Posture Management (SSPM)** and **SaaS Security Detection and Response (SSDR)**, connecting to supported applications "through API, OAuth, or service-account methods" `[src: forticasb-data-sheet-v0-10]`, `[src: deck-saas-security-sspm-final, slide 13]`.

Data collection is described as non-intrusive and agentless "from over 100 sources"; an AI engine maps interconnections to build the SaaS graph; a correlation engine adds context; workflows implement protection and compliance `[src: deck-intro-to-forticasb-sspm-nov25, slide 11]`.

## Use-case areas (as listed in enablement decks)
1. **Shadow and third-party SaaS discovery and visibility**: discover unknown apps that did not go through Security/IT; identify connected plug-ins, add-ons, third-party APIs and tokens; uncover third-party permissions, data, usage and compliance risks; offboard unsanctioned and inactive apps by removing access.
2. **SaaS misconfiguration management (SSPM)**: identify misconfigurations, monitor configuration drift and new security settings.
3. **Identity posture management**: visibility into identities across SaaS apps; onboard users to the IdP while enforcing SSO and MFA; offboard inactive users and revoke permissions.
4. **Gen-AI application management**: control GenAI apps, revoke unauthorized third-party app access, no-code workflows for analysis and control.
5. **Data security posture management (DSPM) and compliance**: mapping to "over 12 security frameworks" (NIST, SOC 2, MITRE, ISO and others); monitor PII sharing/downloading and data posture risks.
6. **Remediation and workflows**: request business justification from owners and authorized users; automate ticketing, notifications and risk assignment; revoke access and offboard users.

`[src: deck-intro-to-forticasb-sspm-nov25, slides 4-10]`, `[src: expert-talks-forticasb-sspm-suridata]`

The unofficial Sept 2026 sales deck lists the same six use cases and pairs each with a value statement and success criteria (shadow SaaS prioritization with risk/usage/user detail; a rich app store with quick integration; misconfiguration remediation per vendor best practices and certifications; third-party risk enforcement recommendations; identity posture with local-account and inactive-user identification; file access risk remediation for external shares, anonymous links and excessive downloads; ticketing/collaboration workflow integration). It frames the product as "FortiCASB: API-based CASB with SSPM". `[src: deck-forticasb-sales-unofficial-2026-09, slides 2-4, 22]`

## Why CASB alone leaves SaaS posture gaps (as presented in the TechTalk deck)
CASB (API, or inline in a SASE architecture) enforces access and data policies; SSPM checks the posture of the underlying SaaS configuration. The deck lists gaps that remain with CASB: misconfigured apps (for example public file shares), weak access controls (simple passwords, shared accounts), third-party integration risks that bypass CASB enforcement, and account lifecycle (CASB cannot remove inactive or orphaned accounts) `[src: deck-techtalk-forticasb-sspm-v1-1, slides 10-13]`. See [CASB, SSPM and related concepts](casb-sspm-concepts.md).

## Dashboard pillars
The dashboard summarizes priority and scores in three pillars: Misconfiguration, 3rd party apps and Access `[src: forticasb-sspm-user-guide-2026-02]`; see [Dashboard and App Store](../sspm-user-guide/dashboard-and-app-store.md).

## Sept 2026 data sheet draft (v0.10)
- Offered as a standalone subscription and through eligible FortiSASE offerings.
- Key benefits listed: complete SaaS ecosystem view; reduced configuration and access risk; risk-based prioritization; faster remediation through ticketing and supported automated responses.
- Features named: dashboard (connected applications, system risk, assets at risk, top risks, changes over time), SaaS Graph, risk views (active/accepted/remediated; filter by priority, type, application, framework, owner, ticket, affected asset), built-in App Store with API/OAuth/service-account connectors and read-only vs administrative permission choice where supported.
- The file is a draft with reviewer comments (one suggests adding a custom framework extension); only page 1 of 6 was captured in the saved copy. Treat as draft.

`[src: forticasb-data-sheet-v0-10]`

## Related
- [Product names and the rebrand](naming-and-rebrand.md)
- [Connector types and permissions](connector-types-and-permissions.md)
- [Licensing and SKUs](licensing-and-skus.md)
- [SaaS OAuth attack-path example](saas-oauth-attack-path-example.md)
- [SSPM User Guide index](../sspm-user-guide/index.md)
