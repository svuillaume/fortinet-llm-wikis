---
title: FortiCASB Licensing
summary: License types, SKUs, FortiClient ZTNA entitlement and scan-capacity rules for legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# FortiCASB Licensing

Two license subscription types exist: **FortiCASB SaaS Protection License** and **FortiCASB Data Protection License**. Usage is based on the number of protected users and the volume of DLP data scanning. Data scans are triggered by the Data Security Policy applied to protected SaaS applications. [src: forticasb-admin-guide-24-4-b, p.19]

## SaaS Protection License
Provides license seats to monitor SaaS application user activities and detect suspicious behavior, plus data protection scanning capacity for DLP and malware/AV scanning. After DLP scan capacity is depleted, only additional DLP scan capacity (Data Protection License) is required.

| Serial number | Description |
|---|---|
| FC1-10-FCASB-145-02-DD | Protection and monitoring of 100 SaaS users including Data Scanning of 1TB |
| FC2-10-FCASB-145-02-DD | Protection and monitoring of 500 SaaS users including Data Scanning of 5TB |

If the number of users in onboarded cloud applications exceeds the total user capacity of the SaaS Protection license, onboarding of new cloud applications is temporarily suspended until an additional license is purchased. This is expected during onboarding; already-onboarded cloud applications remain unaffected. [src: forticasb-admin-guide-24-4-b, p.19-20]

## Data Protection License
Scans triggered by Data Security Policies consume scan capacity by volume of scanned files. Once the initial capacity included with the SaaS Protection license is depleted, the Data Protection license must be added to continue scanning. It is an add-on for existing SaaS Protection users and/or FortiClient ZTNA users.

| Serial number | Description |
|---|---|
| FC1-10-FCASB-307-02-DD | 100GB Data scan add-on for FortiCASB SaaS Protection users or FortiClient ZTNA users |
| FC5-10-FCASB-307-02-DD | 1TB Data scan add-on for FortiCASB SaaS Protection users or FortiClient ZTNA users |

[src: forticasb-admin-guide-24-4-b, p.20]

## FortiClient ZTNA users
- FortiClient ZTNA license holders are entitled to an equivalent number of FortiCASB SaaS Protection seats (500 ZTNA seats = 500 protected SaaS users).
- Entitlement includes the equivalent of 1GB of data scanning per user seat (e.g. 500 seats = 500GB).
- For more scan capacity, only the Data Protection license is needed; the SaaS Protection license need not be purchased for ZTNA users.

[src: forticasb-admin-guide-24-4-b, p.20]

## Applications and license requirements
AWS S3, Google Workspace, and Azure Storage require only the Data Protection License for DLP scan. All other SaaS applications require both user license seats and DLP scan capacity licenses. [src: forticasb-admin-guide-24-4-b, p.21]

## Purchase
Via a local Fortinet sales representative or the partner finder (https://www.fortinet.com/partners/partner-program/find-a-partner). [src: forticasb-admin-guide-24-4-b, p.21]

## Related
- [Introduction and features](introduction-and-features.md)
- [Company and first-time setup](company-and-first-time-setup.md) (License Purchased / Data Protection Usage views)
- [Supported apps and scan scope](supported-apps-and-scan-scope.md)
