---
title: Policies Overview
summary: Policy types per cloud application, how to enable a policy, and the general configuration parameters shared by policies.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Policies Overview

Screenshots were not extracted from the source guide.

In addition to the Data Security policy from Data Protection, each SaaS application has Threat Protection and Compliance policies. Threat protection policies track suspicious user behavior. Compliance policies monitor cloud accounts against compliance standards (SOX-COBIT, PCI, HIPAA, etc.). [src: forticasb-admin-guide-24-4-b, p.424]

## Threat protection policy catalog

Threat Protection is available only for Salesforce, Office 365, Box, Dropbox, Confluence, Egnyte, GitHub, Jira, SAP IAS, ServiceNow, Webex Teams, and Zoom. Example: with Excessive Login Failures active, repeated failed password entries produce an alert. [src: forticasb-admin-guide-24-4-b, p.425]

| Group | Policy | Triggers an alert when |
|---|---|---|
| Access | Excessive Login Failures | Failed logins for a user exceed a set threshold |
| Access | Password Change | Passwords are changed |
| Access | Suspicious Movement | A change in a user's geographic location exceeds threshold parameters |
| Access | Unapproved Login Location | A user logs in from an unapproved geographic location |
| Suspicious Activity | Restricted User | A monitored user performs select activities |
| Suspicious Activity | Suspicious IP | There is activity from a suspicious IP |
| Suspicious Activity | Suspicious Time | There is activity outside of work hours |
| Suspicious Activity | Suspicious Location | There is activity from suspicious locations |
| Sensitive Activity | Sensitive Event | A sensitive event occurs |
| Sensitive Activity | Sensitive File | A specified sensitive file is accessed |
| Sensitive Activity | Ransomware Behavior Detection | The directory's file(s) have been replaced |
| Abnormal Traffic | Large File Upload | A file upload exceeds a size threshold |

Details per policy: [threat-protection-policies.md](threat-protection-policies.md). [src: forticasb-admin-guide-24-4-b, p.425-426]

## Compliance policy catalog

Compliance policies cover SOX-COBIT, PCI-DSS, HIPAA, GDPR, ISO 270001 (spelling as in guide), NIST 800-53 V4, NIST 800-171. Only policies with an entry in the Alert column generate alerts; all others generate data in the compliance report only. Details: [compliance-policies.md](compliance-policies.md). [src: forticasb-admin-guide-24-4-b, p.426-427]

## Enable a policy

Only a policy that is turned On can trigger alerts or generate reports.

1. Select a cloud application from the FortiCASB main dashboard.
2. Click the **Policy** drop-down and select a policy type (Data Analysis, Threat Protection or Compliance).
3. Click a policy drop-down, for example "Sensitive Event".
4. Set the policy to **On**.
5. Click **Save Changes**.

The policy becomes active after a few minutes. For compliance policies, only those with an entry in the Alert column generate alerts. [src: forticasb-admin-guide-24-4-b, p.427-429]

## General configuration parameters

Every policy has different parameters; not all appear in every policy.

| Parameter | Description |
|---|---|
| Enabled | Whether the policy triggers alerts. Active when On. |
| Severity Level | Critical, Alert, Warning, or Information. |
| Matching Threshold | Minimum threshold for an alert. Example: DLP Visa Card policy with threshold 2 alerts when 2 or more credit card numbers are detected. |
| Interval (minute) | Minimum threshold between each time the policy is triggered by user activity. Example: Sensitive Event with interval 5 minutes alerts when a sensitive event occurs every 5 minutes. |
| Data Pattern | DLP or customized data pattern associated with the policy; FortiCASB searches for it during Discovery scans. |
| File Path Regex | Regular expression of cloud storage files FortiCASB runs DLP scan on. |
| Email Notification (Notify FortiCASB Users) | Adds FortiCASB users to be notified when the policy triggers an alert. |
| Email Notification (Notify File Owners) | Only in customized Threat Protection policies; notifies the file owner of file exposure with an editable notification. |

[src: forticasb-admin-guide-24-4-b, p.429]

## Related

- [Threat protection policies](threat-protection-policies.md)
- [Compliance policies](compliance-policies.md)
- [Customized policies](customized-policies.md)
- [Alerts](alerts.md)
- [Data protection](../data-protection/index.md)
