---
title: Connector types, integration methods and permission scopes
summary: Three connector categories (network/EDR/proxy, core SaaS, IdP), their integration methods, outcomes and read/write permission types.
sources: [deck-intro-to-forticasb-sspm-nov25, deck-techtalk-forticasb-sspm-v1-1, forticasb-sspm-user-guide-2026-02, deck-forticasb-sales-unofficial-2026-09]
updated: 2026-10-26
status: current
---

# Connector types, integration methods and permission scopes

## Connector categories

| | FortiAnalyzer / EDR / Proxy | Core SaaS applications | IdP |
|---|---|---|---|
| Data collected | HTTP/S telemetry and devices | Configurations, third parties (non-human identities) and identities | Identities |
| Integration methods | API | API / Service Account / OAuth | API / OAuth |
| Outcome | Shadow SaaS applications, users, devices and interactions | Misconfigurations; third parties (APIs, tokens, service accounts); identities (activities, permissions, MFA, etc.) | Identity information and posture findings (SSO, MFA, permissions, provisioning, devices) |
| Scopes / permissions | Read-only admin | **Type A** (remediation disabled): read-only for information gathering. **Type B** (remediation enabled): write permissions for remediation, read permissions for information gathering | Read-only admin |

In rare cases (fewer than 10% of integrations) admin privileges are needed for full information gathering; a reduced-functionality connector that does not require admin privileges is offered for those. `[src: deck-intro-to-forticasb-sspm-nov25, slide 12]`, `[src: deck-techtalk-forticasb-sspm-v1-1, slide 24]`, `[src: deck-forticasb-sales-unofficial-2026-09, slide 20]`

The TechTalk v1.1 deck labels the first category "EDR / Proxy / CASB"; the Nov 2025 deck labels it "FortiAnalyzer / EDR / Proxy". The newer label is used in the table.

## Connection methods in the App Store
- **API**: direct communication between the platform and the SaaS app with granular access to application data.
- **Service Account**: dedicated service accounts or service principals configured in the SaaS app.
- **OAuth**: token-based authorization.
- **External Link**: each connector has a "Create External Link" button (bottom left) that generates a link and copies it to the clipboard. An application administrator can complete the integration on their own workstation without logging in to the platform.
- Per-connector setup guides are opened from the connector in the App Store using the icon at the top left.

`[src: forticasb-sspm-user-guide-2026-02]`

## Permission dependencies for actions
- Revoking third-party app or token access requires **write** permission granted at connection time. Example: Microsoft 365 can be connected read-only or in admin mode; admin mode needs write permission. `[src: forticasb-sspm-user-guide-2026-02]` See [Third-party apps](../sspm-user-guide/third-party-apps.md).
- Blocking a shadow SaaS application from its Overview tab currently works only for SentinelOne customers (policy is generated in the EDR). See [Shadow SaaS](../sspm-user-guide/shadow-saas.md).

## Related
- [Product overview](overview-and-use-cases.md)
- [Dashboard and App Store](../sspm-user-guide/dashboard-and-app-store.md)
- [Settings: shared accounts and SSO](../sspm-user-guide/settings-and-rbac.md)
