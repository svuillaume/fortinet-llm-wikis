---
title: Native Apps Support and Scan Scope
summary: Which cloud application native apps are monitored and what data is in scope for scanning.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Native Apps Support and Scan Scope

Enterprise-scale cloud applications (Google Workspace, Office 365, AWS S3, etc.) are sold as packages that include other native apps (e.g. Google Workspace: drive, gmail, meet). FortiCASB does not monitor all native apps; it monitors only areas close to its fundamentals, and support varies per cloud application. [src: forticasb-admin-guide-24-4-b, p.21]

## What cloud data is scanned
- Data scan and monitoring start only after the cloud application is onboarded. Data residing on the cloud application before onboarding is not supported for data scan.
- All user activities, including but not limited to file access, are supported through Data Security, Threat Protection, and Compliance policies.

[src: forticasb-admin-guide-24-4-b, p.21]

## Google Workspace native apps
Supported: Google Drive and Google Workspace Marketplace. File activities and file access on these two are monitored by API polling every 15 minutes. (Note: the polling table lists Google Workspace at 1 minute; see [Polling intervals](polling-intervals.md). The guide does not reconcile the two figures.) [src: forticasb-admin-guide-24-4-b, p.22-23]

Native app details for other cloud applications: not found in sources (pages 16-57).

## Related
- [Polling intervals](polling-intervals.md)
- [Licensing](licensing.md)
- [Introduction and features](introduction-and-features.md)
