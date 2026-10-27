---
title: Policy Actions
summary: Actions a FortiCASB Data Security Policy can take: quarantine, change access permission, write label, email and FortiAnalyzer alerts.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Data Security Policy Actions

All incidents matched by the policy trigger the enabled actions. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.375-376]

## Quarantine Files
Moves targeted files from the original directory to a quarantine directory for later review. Available only for Office 365, Google Workspace, Box, Egnyte and Dropbox.

Types:
- **Malware Based**: malware (including virus and ransomware) detected by Fortinet Security Fabric during AV scan and Ransomware Encrypted File Detection is moved.
- **Sensitive Data Based**: any sensitive data type selected in the activated policy and detected during a DLP file scan is moved.

Directories:
1. Default: `forticasb_quarantine_directory~`, placed at the root/top level of the file owner's account.
2. Shared account directory: if the file is in a shared directory, it is removed from there and placed in `forticasb_quarantine_directory~` at the root of the file owner's account.

The file owner is recommended to review and remove infected files from the quarantine directory.

| Platform | Quarantine location |
|---|---|
| Google Workspace | Root/top level of file owner's account |
| Office 365 OneDrive | Root/top level of file owner's account |
| Office 365 SharePoint | Root/top level at the SharePoint site of the file owner |
| Box | Root/top level of file owner's account |
| Dropbox | Root/top level of file owner's account |
| Egnyte | Root/top level of file owner's account |
[src: forticasb-admin-guide-24-4-b, p.376-379]

## Change Access Permission (Google Workspace only)
Options:
1. **Change to Private**: file access permission becomes Private.
2. **Change to Private + Read Only For Users in Trusted List**: Private, and read-only for users in the Trusted List.

Trusted List is configured in Overview > Trusted List by FortiCASB username or e-mail.
[src: forticasb-admin-guide-24-4-b, p.379-380]

## Write Label to Files
Supported: Google Workspace and Office 365. FortiCASB attaches labels to files matched by the policy. Prerequisites are the same as for Label Triggers (Drive Labels API enabled and Google Workspace account updated on first use; Office 365 metered API enabled): see [label-and-metered-api-prerequisites.md](label-and-metered-api-prerequisites.md).

Procedure:
1. In Write Labels To Files, click **On**.
2. Click **+Add Another** and select a SaaS account.

Google Workspace: select Google Workspace in the SaaS drop-down, then a label name.
- Label Name: name of the Google file label. Label Field/Value: field name and value separated by "/".
- Existing labels are not deleted; only new labels are created.
- Same label name with a different field name creates a new label.
- Maximum of 5 user-applied labels per Google Drive file; check the file before applying.
- Example: label name "Animal", field "Fish", value "Tuna".

Office 365: select Office 365 in the SaaS drop-down, then a label name.
- An existing label is replaced by the selected label; there is no option to remove the current label.
- Due to Microsoft API limitation, labels attached by FortiCASB take 24 hours to take effect.
[src: forticasb-admin-guide-24-4-b, p.380-383]

## Send Email Notifications
Alert types:
1. Email Notification: to FortiCASB Users or the affected File Owners.
2. FortiAnalyzer alerts: Syslog messages to FortiAnalyzer. A FortiAnalyzer must first be added in Overview > Fabric Integration (guide "Fabric Integration Configuration", p.342).

The relevant toggle must be enabled in the policy.

### Configure email notification
1. Go to Data Protection > Policies > Scan Policies.
2. Click **+Add New**.
3. After Data Security Policy Name and Match Criteria are filled, go to the Action section.
4. In Send Email Notification, click **On**.
5. Enter the recipient's e-mail address.
6. In Notify File Owners, click **On**.
7. Edit the alert notification fields; parameters sent to the file owner: Activity Name (activity on the file), File Name (file containing the DLP pattern), DLP Pattern Name (pattern that triggered the alert).
8. Click **Add New Data Security Policy**.

### Configure FortiAnalyzer notification
1-3. As above (Scan Policies, +Add New, Action section).
4. In Send Alerts to FortiAnalyzer, click **On**.
5. Click **Add New Data Security Policy**.
[src: forticasb-admin-guide-24-4-b, p.383-385]

## Related
- [policy-match-criteria.md](policy-match-criteria.md)
- [policy-example.md](policy-example.md)
- [data-security-policy.md](data-security-policy.md)
