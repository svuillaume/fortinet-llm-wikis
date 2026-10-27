---
title: Compliance Policies
summary: Compliance standards covered by FortiCASB policies, regex configuration, and configuration of the SOX-COBIT and PCI-DSS policies documented in the guide.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Compliance Policies

Compliance policies monitor cloud accounts against compliance standards. Only policies with an entry in the Alert column generate alerts; all others generate data in the compliance report only. Example: if a user accesses a file containing private health information and the corresponding HIPAA policy is enabled, access logs are added to the compliance report. The prerequisite for a compliance report is to enable and configure the required policies. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.426]

## Standards

| Standard | Guide description |
|---|---|
| SOX-COBIT | Track and show compliance with the Sarbanes-Oxley Act of 2002 using COBIT guidelines; use the Report feature to print a report. |
| PCI-DSS | Uses industry standard version 3.2.1 to track payment-card compliance; reports through the Reporting feature. (The guide text names "FortiCNP" here.) |
| HIPAA | Track and show compliance with the Health Insurance Portability and Accountability Act. |
| GDPR | Track and show compliance with the EU General Data Protection Regulation; personal data type can be set in the GDPR policy configuration. |
| ISO 270001 | Requirements for an ISMS (spelling as in the guide); manage security of assets such as financial information, IP, employee details, third-party information. |
| NIST 800-53 V4 | Recommended security controls for federal information systems and organizations. |
| NIST 800-171 | Protect controlled unclassified information in non-federal systems and organizations. |

[src: forticasb-admin-guide-24-4-b, p.426-427]

## Regex configuration

Regex is used in compliance policies to target specific data in files in the cloud accounts.

| Search query | Regex |
|---|---|
| Specific extension | `.*.(txt\|pdf\|doc\|docx\|xls\|xlsx)$` |
| Folder | `.*\/cucumber\/.*` |
| File name | `.*ssn.*` |
| All path | `.*` |

(The `\|` above is table escaping; the regex alternation is `|`.) [src: forticasb-admin-guide-24-4-b, p.445]

## Common procedure

1. Click a Cloud Account drop-down on the dashboard.
2. Go to **Policy > Compliance** and select the standard tab (for example PCI-DSS, SOX-COBIT).
3. Expand the policy with `>`; toggle **Enabled** on.
4. Choose the Severity level (Critical, Alert, Warning, Information).
5. Fill policy fields (below) and click **Save Changes**.

## PCI - Track all cardholder data access (example)

Generates both an alert and compliance report data.

- File Path Regex: `.*.(txt|pdf|doc|docx|xls|xlsx)$` tracks files with those extensions.
- Data Patterns: select DLP SSN, DLP Visa Credit Card, and DLP JCB.

Result: those files are checked for Social Security, Visa and JCB card numbers. [src: forticasb-admin-guide-24-4-b, p.446]

## SOX-COBIT - Access to Sensitive Data

Monitors access to sensitive data; location set by file path regex. Generates both alert and compliance report data.

| Field | Meaning |
|---|---|
| File Path Regex | e.g. `.*`, or `^(?:[\w]\:|\\)(\\[a-z_\-\s0-9\.]+)+\.(txt|gif|pdf|doc|docx|xls|xlsx)$` (matches `\\192.168.0.1\folder\file.pdf`, `c:\my folder\abc abc.docx`) |
| Data Patterns | Data patterns (financial, personal identity information, etc.) to monitor |

[src: forticasb-admin-guide-24-4-b, p.447-448]

## PCI - Failed Access Attempt Detection

Generates both alert and compliance report data. (The guide's description text is copied from Privileged Account Activity: monitors targeted users' activities.)

| Field | Meaning |
|---|---|
| Login Attempts | Threshold of failed login attempts before an alert |
| Interval (minute) | Time frame for failed attempts. Example: interval 3 minutes and attempts 5 means more than 5 failures in 3 minutes triggers an alert |

[src: forticasb-admin-guide-24-4-b, p.448-449]

## PCI - Privileged Account Activity

Monitors targeted users' activities; configure which users and activity types. Generates both alert and compliance report data.

| Field | Meaning |
|---|---|
| Event | Specific event(s) or **Select all events** |
| Monitored User | Select user(s) or **Select all users** |

[src: forticasb-admin-guide-24-4-b, p.450]

## PCI - Retention Violation for Cardholder Data

Checks whether designated cloud storage data exceeded the retention time set by the cardholder. Generates data in the Compliance Report only (no alert).

| Field | Meaning |
|---|---|
| File Path Regex | Target file path of data under retention restriction |
| Retention Time (day) | Retention days for the cloud storage data |
| Data Patterns | Patterns (financial, PII, etc.) under the retention restriction |

[src: forticasb-admin-guide-24-4-b, p.451-452]

The guide references "Generate Compliance Report on page 297" for the report; see the reporting pages from other sections of the wiki (not linked here). Configuration guides for HIPAA, GDPR, ISO, NIST policies: not found in sources.

## Related

- [Policies overview](policies-overview.md)
- [Customized policies](customized-policies.md)
- [Alerts](alerts.md)
