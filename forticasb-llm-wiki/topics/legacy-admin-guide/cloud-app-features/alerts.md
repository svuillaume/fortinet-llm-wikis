---
title: Alerts
summary: How FortiCASB alerts are produced by Data Analysis, Threat Protection and Compliance policies and where to view them.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Alerts

FortiCASB sends alerts when an enabled policy is triggered by user activity.

- Data Analysis policies pertain to the types of data stored in the cloud application.
- Threat protection policies pertain to suspicious user activity.
- Compliance policies pertain to specific regulations, such as HIPAA, PCI, and SOX.

To view alerts for a cloud application, open its drop-down menu and click **Alert**. All alerts are triggered by user activities that violated the corresponding policies. Click the right arrow of an alert to show its summary. [src: forticasb-admin-guide-24-4-b, p.456-457]

Policies must be enabled to trigger alerts (see [policies-overview.md](policies-overview.md)). Daily alerts can be compiled into Alert reports for export (guide: "Generate Alert Report", p.301; reporting pages not linked here). Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.457]

## Related

- [Policies overview](policies-overview.md)
- [Activity](activity.md)
- [Threat protection policies](threat-protection-policies.md)
