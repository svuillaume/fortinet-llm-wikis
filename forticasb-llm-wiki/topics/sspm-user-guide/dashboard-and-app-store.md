---
title: Dashboard, App Store and SaaS Graph
summary: Dashboard metrics, App Store connector flow and connection types, External Link delegation, and SaaS Graph behavior in FortiCASB-SSPM.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Dashboard, App Store and SaaS Graph

## Introduction (as stated in the guide)
The guide frames the platform around the attacker's perspective: showing the security team what an attacker could do through the SaaS environment, how they could move across environments, and what to fix proactively. `[src: forticasb-sspm-user-guide-2026-02, Introduction]`

## Dashboard
- **Connected Applications**: number of applications connected.
- **System Risk Score**: overall score, a weighted average in which critical-risk applications weigh more than low-risk ones.
- **Assets at Risk**: identities, repositories, endpoints and files; an asset is listed only if associated with **high or critical** risks.
- **Top risks table**: type, affected applications, risk score and associated assets; items are clickable.
- **Connected applications table** summarizing priority and scores in three pillars: **Misconfiguration, 3rd party apps, Access**.
- **Activity graph**: progress and asset trends, filterable by past week, month, quarter, year.
- **Risk distribution** categories: Misconfiguration, 3rd party apps, Compliance, Data leakage, Insider Threat, Unauthorized Access.

`[src: forticasb-sspm-user-guide-2026-02, The Dashboard]`

## App Store
Repository of ready-made connectors.
1. **Browse connectors**: filter by app type; see which are already connected.
2. **Select connector.**
3. **Configure connector**: follow the provided guide; supply credentials and permissions.

Connection types: API, Service Account, OAuth, plus External Link. Details in [Connector types and permissions](../product/connector-types-and-permissions.md).

**External Link**: the "Create External Link" button (bottom left of a connector) generates a link copied to the clipboard for sharing with an application administrator, who completes the integration without logging in to the platform. The guide says this reduces push-back from internal administrators.

`[src: forticasb-sspm-user-guide-2026-02, The App Store]`

## SaaS Graph
Visual map of connections between core applications, 3rd-party apps and shadow SaaS.
- **Risk visualization**: each application is a diamond; color and size indicate risk level; hover shows identified risks.
- **Vendor aggregation**: third-party apps from the same vendor are grouped.
- **Filter and search**: by vendor, risk level, application category; search bar for apps or connections.
- **Deep dive**: clicking an application opens a drawer with purpose/usage information and links to detail pages.
- Benefits listed: visibility, decision-making, risk-prioritization, consolidation opportunities.

`[src: forticasb-sspm-user-guide-2026-02, The SaaS Graph]`

## Predecessor document
The Suridata user guide has the same Dashboard, App Store and SaaS Graph text with the vendor name substituted. `[src: suridata-user-guide]`

## Related
- [SSPM User Guide index](index.md)
- [Applications](applications.md)
- [Settings and RBAC](settings-and-rbac.md)
