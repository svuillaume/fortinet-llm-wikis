---
title: Audit Logs and Data Analysis Logs
summary: Overview > Audit log records administrative and user activity in FortiCASB; Data Analysis Logs show file download/scan/delete activity.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Audit Logs and Data Analysis Logs (Legacy FortiCASB 24.4.b)

## Audit log
- Records all administrative and user activities in FortiCASB.
- Access: **Overview > Audit log**.
- Filter searches with **+Add Filter**.
- For a description of each operation/event see [App events overview](app-events-overview.md).
- File Download events are monitored within the FortiCASB Audit log (**Overview > Audit Log**).

[src: forticasb-admin-guide-24-4-b, p.306-307, 324]

## Data Analysis Logs
FortiCASB accesses your information by downloading files, scanning them, then deleting the downloads at regular intervals. FortiCASB does not retain files. To see when and which files were downloaded, scanned and deleted, click the **Data Analysis Logs** button (icon at the top-right of the Audit log page). Screenshots were not extracted.

[src: forticasb-admin-guide-24-4-b, p.307]

## Related
- [App events overview](app-events-overview.md)
- [Reports](reports.md)
- [Overview Features index](index.md)
