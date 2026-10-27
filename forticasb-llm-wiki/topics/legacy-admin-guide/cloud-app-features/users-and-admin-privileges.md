---
title: Users and Administrative Privileges
summary: Users page, user property types, and which roles FortiCASB treats as privileged per cloud application.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Users and Administrative Privileges

## Users page

The Users page displays user access privilege to the cloud application and the files shared or shared by the users. Click a user name for details. The user type is shown in the **Property** column. [src: forticasb-admin-guide-24-4-b, p.420-421]

| Type of user | Description |
|---|---|
| Privileged User | Any user with specific administrative privileges (see below). |
| Dormant User | Any user that has not accessed the cloud application for at least 30 days. |
| Guest User | Any user from an external company with access to your cloud application. |

If the Users page cannot retrieve privileged role information from an Office 365 account, make sure you have Global Administrator privileges and Azure Active Directory Premium P2. [src: forticasb-admin-guide-24-4-b, p.421]

## Administrative privileges (privileged user definition)

| Cloud application | Privileged user is a user with |
|---|---|
| Box | All of: Manage users and groups; Make calls on behalf of users; View all data |
| Confluence | Any of: Site Admin; Administrator; Trusted User |
| Dropbox Business | Team Admin |
| Egnyte | Any of: Administrator; Power User |
| Google Workspace | Any of: Super Administrator; Groups Administrator; User Management Administrator; Help Desk Administrator; Services Administrator; User Customized Administrator |
| Jira | Any of: Site Admin; Administrator; Jira-Administrator |
| GitHub | Account owner only |
| Office 365 | Any of: global administrator; billing administrator; password administrator; service administrator; user management administrator; Exchange administrator; SharePoint administrator; Skype for Business administrator |
| SAP IAS | Admin user, or user with user type: Public |
| Salesforce | Any of: Assign Permission Sets; Manage Sharing; Modify All Data; Manage Encryption Keys; View All Data; View All Users |
| ServiceNow | Administrative user (any user with admin role) |
| Webex Teams | Any of: User Administrator; Read-only Administrator; Support Administrator; Device Administrator; Sales Administrator; Help Desk Administrator; Full Administrator |
| Zoom | Any of: Owner; Admin; custom role user with all privileges of an Admin role |

[src: forticasb-admin-guide-24-4-b, p.422-424]

## Related

- [Files](files.md)
- [Alerts](alerts.md)
- [Cloud application features index](index.md)
