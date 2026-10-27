---
title: Change Log and What's New (24.4.b)
summary: Document change log history and the FortiCASB 24.4.b release highlights.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Change Log and What's New

Screenshots were not extracted from the source guide. This guide documents the legacy FortiCASB platform (see [Introduction and features](introduction-and-features.md)).

## Change Log

| Date | Change description |
|---|---|
| 07/01/2020 | FortiCASB 20.2 Handbook release. Cloud Account Activity and Alert Reports are now available for export from Reports. |
| 04/03/2020 | FortiCASB 20.1 Handbook release. FortiCASB REST API reference added and Compliance Report feature upgraded in this revision. |
| 09/07/2019 | FortiCASB 4.2 Handbook release. IAAS applications and features migrated to FortiCWP. |
| 04/05/2019 | FortiCASB 4.1 Handbook release. Revised Getting Started documentation for Basic Setup and Install IAAS applications. Added documentation for Topology, Resource, Resource Profile, and Traffic. Configuration merged into Risk Assessment. |
| 01/08/2019 | FortiCASB 2.1 Handbook. First edition. Changed EU users IP address from 52.59.74.73 or 18.195.109.67 to 34.254.217.50 or 52.18.7.98, in the section "Show IT discovery". |
| 06/20/2023 | FortiCASB 22.2.b release |
| 08/11/2023 | FortiCASB 23.3.a release |

The log is listed in the order printed in the guide (not strictly chronological); no entry for 24.4.b itself appears in the change log table. [src: forticasb-admin-guide-24-4-b, p.16]

## FortiCASB 24.4.b release highlights

- Optical Character Recognition (OCR) scan is integrated into Data Security Policy to conduct Data Security Scan on sensitive data found in image sources.
- Microsoft Entra ID (formerly Azure AD) Administrative Units integration now supports integration at group level, in addition to user level, streamlining adding users to the same Administrative Unit.
- New features accompanying Entra ID AU group integration:
  - Data Security Policy: groups can be configured as one of the Match Criteria, so the policy targets specific users and reduces data scan time.
  - Compliance, Alert, and Activity Reports: support group selection, narrowing target users from all users to a subset.

See [Entra ID administrative units](entra-id-administrative-units.md). [src: forticasb-admin-guide-24-4-b, p.17]

## Related
- [Introduction and features](introduction-and-features.md)
- [Entra ID administrative units](entra-id-administrative-units.md)
- [FortiCASB naming and rebrand](../product/naming-and-rebrand.md)
