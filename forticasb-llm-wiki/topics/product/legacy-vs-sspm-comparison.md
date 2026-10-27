---
title: FortiCASB Legacy vs FortiCASB-SSPM, and Basic vs SSPM editions
summary: Side-by-side of the Legacy 24.4.b platform and the SSPM platform as documented, plus the Basic/SSPM edition capability table.
sources: [forticasb-admin-guide-24-4-b, forticasb-sspm-user-guide-2026-02, deck-intro-to-forticasb-sspm-nov25, expert-talks-forticasb-sspm-suridata, forticasb-commercial-platform-update-v1-5]
updated: 2026-10-26
status: current
---

# FortiCASB Legacy vs FortiCASB-SSPM

This is a documented-differences table. It is not an official feature-parity statement; the commercial update asks teams to confirm capability availability with the CSE team.

| Area | FortiCASB Legacy (Admin Guide 24.4.b) | FortiCASB-SSPM / FortiCASB (User Guide Feb 2026) |
|---|---|---|
| Tenant model | Company, business units (BU), FortiCloud primary account; local IAM users and OU IAM users | Single platform tenant; Users and Roles tabs with 4 built-in roles (Owner, Admin, User, Operator) and custom roles |
| Onboarding | Per-app wizards, cloud-side policies/roles/OAuth apps, polling or webhook (for example AWS S3, Azure Storage, Box, Google Workspace, Office 365, Salesforce, ServiceNow, Zoom) | App Store of ready-made connectors (>100 sources) using API, service account or OAuth; External Link for delegating to app admins |
| Core model | Per-account dashboards, files, users, policies (threat protection, compliance), alerts, activity | SaaS Graph, Applications (managed/unmanaged), Risks, Identities, 3rd-party apps and tokens, Activities, Workflows |
| Data protection | Data Security Policies with match criteria and actions (quarantine, change permission, write label, email); predefined and custom data patterns (regex, exact data match) | Search with advanced query builder over file metadata and access-control fields; saved queries become Risks; PII search; workflow actions Quarantine, Revoke permissions, Delete, Notify |
| Shadow IT | FortiGate/FortiAnalyzer log-based Shadow IT discovery and reports | Shadow SaaS discovered through EDR, firewalls, VPNs and other telemetry; business justification requests; Block Application (SentinelOne only) |
| Third-party apps | Not a documented feature area | Inventory of OAuth apps and tokens, vendor reputation, revoke access (Microsoft, Google, Okta, Salesforce, Atlassian) |
| Identities | User lists and administrative privileges per cloud account | Identity profiles aggregated across apps, EDR and IdPs; six finding types |
| Automation | Policies with alerts/actions; REST API | No-code Workflows (trigger, condition, action); Jira/ServiceNow ticketing; Slack/Teams/email assignment |
| Reporting | C-Level, Compliance, Alert, Activity and Shadow IT reports | Executive report; export to CSV |
| Fabric integration | FortiAnalyzer (view FortiCASB alerts), FortiGate/FAZ for Shadow IT | FortiAnalyzer/EDR/proxy connector category; roadmap items for FortiAI, FortiProxy, FortiSASE, CNAPP integration |
| API | REST API with client credential, username/password, refresh-token auth | API Integrations tab for API keys (documentation referenced in product; endpoint list: not found in sources) |
| Portal | `www.forticasb.com` ("FortiCASB Legacy portal") | FortiCloud portal |
| Licensing | FCASB-145 / FCASB-307 (legacy) | FCSSM-1278 user-band subscriptions |

Sources: `[src: forticasb-admin-guide-24-4-b]`, `[src: forticasb-sspm-user-guide-2026-02]`, `[src: forticasb-commercial-platform-update-v1-5]`. Detailed pages: [Legacy Admin Guide](../legacy-admin-guide/introduction-and-features.md), [SSPM User Guide](../sspm-user-guide/index.md).

## Editions: Basic vs SSPM

| Capability | FortiCASB (Basic) | FortiCASB-SSPM |
|---|---|---|
| Shadow SaaS discovery | Yes | Yes |
| Data discovery | Yes | Yes |
| DSPM | Yes | Yes |
| Gen-AI identification and control | Yes (marked V* in the Expert Talks and one Nov 2025 variant, footnote not captured; plain V in another Nov 2025 variant) | Yes |
| SaaS Graph | No | Yes |
| 3rd-party applications control | No | Yes |
| Identities security posture management | No | Yes |
| Threat management and activities | No | Yes |
| Workflow and automation | No | Yes |
| Business users justification | No | Yes |
| SSPM | No | Yes |
| Ticketing and collaboration | No | Yes |

`[src: deck-intro-to-forticasb-sspm-nov25, slide 13]`, `[src: expert-talks-forticasb-sspm-suridata]`. The Sept 2026 commercial update refers only to "the full FortiCASB capability set" on the FCSSM-1278 SKUs, so the status of the Basic edition after the rename is not found in sources. See [Licensing](licensing-and-skus.md).

## Related
- [Product names and the rebrand](naming-and-rebrand.md)
- [Lifecycle and migration](lifecycle-and-migration.md)
- [Product overview](overview-and-use-cases.md)
