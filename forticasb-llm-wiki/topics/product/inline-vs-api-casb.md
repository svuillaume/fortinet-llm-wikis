---
title: Inline vs API CASB (FortiGuard CASB dual-mode)
summary: How inline CASB (FortiGate/FortiSASE) and API CASB (FortiCASB) divide the work, the four API CASB use-case groups, Shadow IT reporting and on-demand reports.
sources: [deck-tdm-presentation-casb, deck-techtalk-forticasb-sspm-v1-1]
updated: 2026-10-26
status: current
---

# Inline vs API CASB (FortiGuard CASB dual-mode)

From the Technical Decision Maker deck "Securing your Cloud Applications - FortiGuard CASB". The deck predates the FortiCASB-SSPM rename; "API CASB" here refers to FortiCASB (the Legacy-style API CASB with Shadow IT reports and data analysis).

## Two modes

| | Inline CASB | API CASB (FortiCASB) |
|---|---|---|
| Data state | Data in motion | Data at rest |
| Deployment | Part of ZTNA and SASE; needs an agent (posture assessment) or FortiGate in path | Agentless |
| Locations | Managed and unmanaged locations | Unmanaged locations (BYOD) |
| Focus | Visibility and remediation; user experience and privacy | Visibility and compliance; user experience and security |

Pillars covered by the combined offering: visibility, data security, threat protection, compliance, and tenant control. `[src: deck-tdm-presentation-casb, slides 9-11]`

## Inline CASB use cases
- Control sanctioned and unsanctioned applications; configure applications by risk level with granular cloud-application configuration.
- **Tenant control** for cloud applications: allow the corporate tenant and block personal tenants, using custom headers.

`[src: deck-tdm-presentation-casb, slides 18-21]`

## API CASB use-case groups
1. **Risk management / security posture**: risk trends, events, user insights and behavior, severity statistics for data stored in SaaS and public cloud.
2. **Data security and compliance**: scans for sensitive and malicious files; predefined compliance policies and reports.
3. **Shadow IT discovery**: insight into sanctioned and unsanctioned cloud applications.
4. **Threat detection and response**: user entity behavior analytics (UEBA) for account-centric threats and anomalies with alert policies.

`[src: deck-tdm-presentation-casb, slide 24]`

## Shadow IT reports
- Built-in (real-time) report imports and aggregates log data; on-demand report lists sanctioned and unsanctioned applications, risky applications, sessions created and file insights.
- A FortiGuard Shadow IT report via FortiAnalyzer adds executive summary, malware detected, cloud services, managed and unmanaged app risk, app vulnerabilities, DLP events, upload and compliance, and user activity. The slide notes this is available with FortiAnalyzer 7.4.
- Operational configuration of Shadow IT discovery is in [Shadow IT discovery](../legacy-admin-guide/overview-features/shadow-it-discovery.md).

`[src: deck-tdm-presentation-casb, slides 26-31]`

## On-demand reports
C-Level, Compliance (PCI, HIPAA, SOX, GDPR, NIST, ISO), Alert, Activity and Shadow IT. See [Reports](../legacy-admin-guide/overview-features/reports.md). `[src: deck-tdm-presentation-casb, slide 37]`

## Related
- [FortiSASE entitlements](fortisase-entitlements.md)
- [CASB, SSPM and related concepts](casb-sspm-concepts.md)
- [Product names and the rebrand](naming-and-rebrand.md)
