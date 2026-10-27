---
title: Identities
summary: Identity profiles aggregated from apps, EDR and IdPs; list columns, priority factors, six finding types and the Overview, Risks and 3rd Party Apps tabs.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Identities

Identities represent human and non-human entities with access to one or more SaaS applications. Data is gathered from the applications, EDR tools and identity providers, then aggregated into a profile per identity (typically keyed by email address). `[src: forticasb-sspm-user-guide-2026-02, Identities]`

## Identities screen
Ranked by default in descending **investigation priority**. Columns: Risks (total), Findings (color-coded: dark red critical, yellow medium), Applications, Priority.

Priority factors named: authorized 3rd-party apps and activities (thresholds on file/folder activities). Supported activity types fall in three categories: **Data Management, Authentication, User Management**.

## Overview tab
- **Findings** (interactive): six types:
  1. Shadow SaaS: number of unapproved SaaS apps associated with the identity.
  2. Admin: number of applications with administrative access.
  3. Account Management: issues such as inadequate password complexity.
  4. Authentication: issues such as missing MFA.
  5. SSO: identity lacks SSO or is not federated by the IdP.
  6. Inactive: inactive in a specific application.
- **Identity's priority over time**: timeline of Critical/High/Medium/Low classification driven by privileges, activity, exposure.
- **Applications**: accessible apps with roles, license status, local vs IdP account, groups.
- **Shadow SaaS applications**: unmanaged apps with recent interactions, app risk score, last activity.
- **Activities**: file and folder operation log with filters by Application, Time, Action; clicking a file shows full path and sharing information and links to Search.

## Risks tab
Risks associated with the identity; same actions as the main Risks page.

## 3rd Party Apps tab
Third-party apps and tokens the identity authorized; same actions as the main 3rd Party Apps page.

## Documentation gap
Full access-review and offboarding automation is not described in this guide; a competitive data sheet flags identity-governance depth as unverified (see [Fortinet fit and gaps](../competitive/fortinet-fit-and-gaps.md)).

## Related
- [Risks](risks.md)
- [Third-party apps](third-party-apps.md)
- [Activities](activities.md)
