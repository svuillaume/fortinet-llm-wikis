---
title: Activities
summary: The Activities page as a near-real-time audit trail across apps, its embedded pre-filtered tabs, and saving filters as risks.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Activities

Near-real-time visibility into user and file-level activity across all connected SaaS applications, acting as a centralized audit trail: logins (successful and failed), file/folder sharing and deletion, downloads, group changes, user provisioning and more. Each event is enriched with user email, timestamp, location (city, region, country), IP address and application context.

- Also embedded as an **Activities** tab inside Applications and Identities, pre-filtered to the selected app or identity.
- Advanced filters combine parameters (activity type, location, IP address, VPN/proxy) with AND/OR logic.
- Any filtered set can be **saved as a Risk** to monitor recurrence (mass downloads, repeated access from suspicious IPs, sharing anomalies).
- Per-application log fields and CSV export: see [Applications](applications.md).

`[src: forticasb-sspm-user-guide-2026-02, Activities]`

## Legacy comparison
Legacy activity monitoring, the activity map and per-app event lists: [Legacy activity](../legacy-admin-guide/cloud-app-features/activity.md), [App events overview](../legacy-admin-guide/overview-features/app-events-overview.md).

## Related
- [Risks](risks.md)
- [Identities](identities.md)
