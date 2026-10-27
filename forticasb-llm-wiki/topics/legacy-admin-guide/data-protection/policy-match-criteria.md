---
title: Policy Match Criteria
summary: The eight match criteria of a customized FortiCASB Data Security Policy, including label triggers.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Data Security Policy Match Criteria

Eight match criteria can be customized when a customized Data Security Policy is created. [src: forticasb-admin-guide-24-4-b, p.364-365]

| Criterion | Behavior |
|---|---|
| Files Created After | Only files created after the designated day are targeted for data scan. |
| File Types | Text/compressed types: doc, ppt, pptx, xls, xlsx, txt, rtf, js, pdf, zip, tar, 7z, gz, exe. Image types for OCR: jpg, jpeg, png, tif, tiff; the OCR toggle must be On to activate OCR scan. |
| Access Permissions | Target share permissions: Private Access, Public Editable, Group Editable, Group Readable, Public Readable. |
| File Activity Triggers | Activities: Create File, Modify File, Access File, Share File. Configurable threshold on number of times the activity is detected in a specified time frame. |
| Microsoft Entra ID Group | If a group is selected, only its users are scanned and trigger alerts; if none selected, all users. |
| Files Shared With Users/Domains NOT In Trust List (Google Workspace only) | Users/domains selected from the User Trust List and Domain Trust List are monitored; alert when a trusted user/domain shares a file with an external user. Example: trusted user John Meyer shares with Mike Taylor, who is not in the Trust List, triggers an alert. Lists are configured in Overview > Trusted List. |
| SaaS Applications | Only onboarded applications appear; select those to be DLP scanned. SAP IAS is not supported in Data Security policy. |
| Data Patterns | Predefined and customized patterns can be selected. See [predefined-data-patterns.md](predefined-data-patterns.md), [customized-data-patterns.md](customized-data-patterns.md). |
| Label Triggers | See below. |

Note: the guide says "eight" criteria but lists nine items (Label Triggers included); the guide's ordering lists Label Triggers before SaaS Applications.
[src: forticasb-admin-guide-24-4-b, p.365-368]

## Label Triggers

### Introduction
Labels are metadata on files in cloud accounts. They can be used as metadata to search files in DLP search, and new labels can be attached to matched files using Write Label to Files ([policy-actions.md](policy-actions.md)). If no label is added in the criteria, the policy scans all files whether labeled or not. Label Triggers supports only Google Workspace and Office 365.
- Google Drive Label: customizable label attached to Google Drive files (Google "Get Started as a Drive Labels admin").
- Office 365 Sensitivity Label: part of Azure Information Protection (Microsoft "Learn about sensitivity labels").
[src: forticasb-admin-guide-24-4-b, p.369]

### Prerequisites
Google Workspace:
1. Enable Google Drive Labels API ([label-and-metered-api-prerequisites.md](label-and-metered-api-prerequisites.md)).
2. On first use of Label Triggers, update the Google Workspace account in FortiCASB (guide "Update Google Workspace Account", p.174).

Office 365:
1. Enable Metered API from Microsoft Graph (to attach Sensitivity Labels via the policy).
2. If the Sensitivity Label has Access Control enabled, FortiCASB cannot scan files with that label; ensure Access Control is not enabled.
[src: forticasb-admin-guide-24-4-b, p.370]

### Using Label Triggers
When label names and field/value are entered, only files with the matching labels are scanned.
- **Label Name**: name of the Google file label or Office 365 Sensitivity label.
- **Label Field/Value** (Google Workspace only): field name and value, separated by "/".

Office 365 has one label type (standard). Google has four:

| Label type | Inputs | Matching |
|---|---|---|
| Standard Label | Label Name, Label Field/Value | Label name, field name and value must all match. |
| Standard Label | Label Name, Field | Matches file with same label name and field name only. Same name and field but with a value: ignored. |
| Standard Label | Label Name | Matches only files with same label name without any field name/value. |
| Badged Label | Label Name, /Value | Both label name and value must match; same name without value: not matched. |
| Badged Label | Label Name | Matches same label name only; same name with a value: ignored. |

Examples:
1. Standard, Name + Field/Value (Google only): name "Automobile", field/value "Honda/Accord".
2. Standard, Name + Field (Google only): name "Mouse", field "Test"; a different or missing field, or the same field with a value, is not matched.
3. Standard, Name (Google and Office 365): name "Airplane"; with a field or value, not matched.
4. Badged, Name/Value (Google only): name "New Badged Label", value " /New Option"; without value, not matched.
5. Badged, Name (Google only): name "New Badged Label 2"; with a value, not matched.
[src: forticasb-admin-guide-24-4-b, p.370-372]

## Related
- [label-and-metered-api-prerequisites.md](label-and-metered-api-prerequisites.md)
- [data-security-policy.md](data-security-policy.md)
- [policy-actions.md](policy-actions.md)
