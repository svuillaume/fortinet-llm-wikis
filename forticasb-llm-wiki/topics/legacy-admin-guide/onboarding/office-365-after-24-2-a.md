---
title: Office 365 onboarding (after 24.2.a)
summary: Service-account onboarding for Office 365 using a Microsoft Entra ID app registration (client ID, tenant ID, client secret) with Graph and Office 365 Management API application permissions.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Office 365 onboarding (after 24.2.a update)

Note: screenshots in the guide were not extracted. Older flow: [office-365-before-24-2-a.md](office-365-before-24-2-a.md).

## Overview
Same API-based design (RESTful API, OAuth2.0, activity monitoring, DLP Data Analysis). After the 24.2.a update, Office 365 performance improved by supporting higher file scanning rates using a dedicated service account instead of a user account. A client application must be registered in Microsoft Entra ID on Azure to onboard Office 365. Supported Microsoft online apps (since 21.2): Yammer (monitors all shared files at SharePoint sites), OneDrive (all files shared privately or publicly), SharePoint (files in Document and "user-created" folders), Azure Active Directory (all user activities). [src: forticasb-admin-guide-24-4-b, p.208-209]

## Prerequisite order
1. Office 365 account and license; 2. Activate audit log; 3. Register FortiCASB with Microsoft Identity Platform; 4. Add Office 365 account in FortiCASB. [src: forticasb-admin-guide-24-4-b, p.209]

## Account and license
- Existing or new account; new accounts need at least 24 hours before granting access.
- License plan must include Active Directory integration: Office 365 Business, Business Essentials, Business Premium, ProPlus, Enterprise E1, E3, E5, K1.
- Microsoft Entra ID P2 recommended. Without it, Discovery cannot access user entitlements (onboarding status errors; Office 365 > Users shows "This users has no Advanced Permission" even for global admins; no Privileged User data). Other major functions are unaffected.
- Microsoft Entra Privileged Identity Management must be activated. Links: https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-get-started-premium and https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-configure
- Determine license: office.com > Apps button > Admin > Billing > Your Products.
- Unlike the old flow, no Global Administrator requirement is stated for the FortiCASB add step, and no SharePoint site-admin step is documented; Global Administrator is needed to register the app.

[src: forticasb-admin-guide-24-4-b, p.210-212]

## Activate audit log
1. Log in to https://www.office.com/ as admin.
2. Office 365 menu > Admin portal (Microsoft 365 admin center).
3. Left menu > Security (Microsoft 365 Defender).
4. Left menu > Audit.
5. Click Start recording and admin activity (if absent, already enabled; new tenants see it only 24 hours after creation).
6. Allow 24 hours for auditing to become available. It may take several hours before FortiCASB receives logs. Errors adding Office 365 may mean auditing is not yet enabled.

[src: forticasb-admin-guide-24-4-b, p.212-214]

## Register FortiCASB with Microsoft Identity Platform
Requires a Microsoft Entra ID tenant and an Office 365 account with Global Administrator role.

### App registration
1. Sign in to Microsoft Entra Admin Center with a Global Administrator account.
2. With multiple tenants: Settings icon (top menu) > Directories + subscriptions, select the tenant.
3. Search for and open App registrations.
4. Click New registration.
5. Enter an application name.
6. Supported account types: "Accounts in this organizational directory only".
7. Leave Redirect URI (optional) empty.
8. Click Register.
9. On the Overview pane record Application (client) ID and Directory (tenant) ID.
10. Side panel Certificates & secrets > Client secrets: create a client secret if none exists and record the Value.

[src: forticasb-admin-guide-24-4-b, p.214-216]

### Add API permissions
1. Side panel API Permissions.
2. +Add a permission > Microsoft Graph > Application permissions; add the Graph permissions below.
3. +Add a permission > Office 365 Management APIs > Application permissions; add the permissions below.
4. Click "Grant admin consent for <tenant>" (guide example: "fortinet"). All permissions must show "Granted for <tenant>".

| API | Permissions (application type) |
|---|---|
| Microsoft Graph | Directory.Read.All; Domain.Read.All; Files.ReadWrite.All; Group.Read.All; GroupMember.Read.All; PrivilegedAccess.Read.AzureAD; PrivilegedAccess.Read.AzureResources; Sites.ReadWrite.All; User.Read; User.Read.All; InformationProtectionPolicy.Read.All (for Azure Information Protection) |
| Office 365 Management APIs | ActivityFeed.Read; ActivityFeed.ReadDlp; ServiceHealth.Read |

Oddity: the guide's two-column table is garbled in the extracted text; column assignment above follows the permission naming (InformationProtectionPolicy.Read.All appears after the table with its Azure Information Protection note). [src: forticasb-admin-guide-24-4-b, p.216-218]

## Add Office 365 account in FortiCASB
1. Log in to FortiCASB.
2. Overview > Dashboard > Add New > select Office 365 > Add Selected Cloud App.
3. Click Next Step once audit log activation and app registration are done.
4. Fill in Application (client) ID, Directory (tenant) ID and Client Secret Value from the app registration.
5. Click Grant Access @Microsoft.

You are redirected to the Office 365 dashboard; the Cloud Account value shows the Office 365 tenant ID. Allow up to 15 minutes. [src: forticasb-admin-guide-24-4-b, p.218-220]

## Update Office 365 account
Redo the same configuration with the same account (license, audit log, app registration), then:
1. Log in to FortiCASB, Overview > Dashboard.
2. Open the Office 365 Account menu > Update Cloud Account.
3. Confirm configuration complete, click Next Step.
4. Fill in Application (client) ID, Directory (tenant) ID, Client Secret Value.

5. Click Grant Access @Microsoft to complete the update.

Status and the installation checklist show in the Office 365 dashboard; allow up to 15 minutes for the account to be fully updated. [src: forticasb-admin-guide-24-4-b, p.221-223]

## Comparison: before vs after 24.2.a
| Aspect | Before 24.2.a | After 24.2.a |
|---|---|---|
| Identity used | User account (Global Administrator) via OAuth consent | Dedicated service account via Entra ID app registration |
| Performance | Standard | Higher file scanning rates |
| Microsoft-side setup | License, audit log, add admin to SharePoint sites | License, audit log, app registration + API permissions + admin consent |
| SharePoint site admin step | Required (Company Administrator site, Add site admins) | Not documented |
| Permissions model | Delegated permissions accepted at consent screen (long list) | Application permissions: 11 Graph + 3 Office 365 Management API |
| FortiCASB add fields | None; click Grant Access @Office 365 and log in | Application (client) ID, Directory (tenant) ID, Client Secret Value; Grant Access @Microsoft |
| FortiCASB wizard | Add Selected Cloud App then Grant Access | Add Selected Cloud App, Next Step, fill fields |
| Update | Update Cloud Account, Grant Access, re-consent | Update Cloud Account, Next Step, re-enter ID/secret, Grant Access @Microsoft |
| New-user OneDrive gotcha | New users' OneDrive/SharePoint need site admin added | Not documented for this flow |
| Cloud Account value | not found in sources | Tenant ID |

[src: forticasb-admin-guide-24-4-b, p.191-222]

## Related
- [office-365-before-24-2-a.md](office-365-before-24-2-a.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
- [../user-management-and-permissions.md](../user-management-and-permissions.md)
