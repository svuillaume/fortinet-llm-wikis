---
title: Office 365 onboarding (before 24.2.a)
summary: Legacy user-account (OAuth consent) onboarding flow for Office 365 in FortiCASB, with audit log, SharePoint site admin, license prerequisites and the delegated permission list.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Office 365 onboarding (before 24.2.a update)

Note: screenshots in the guide were not extracted; only text is captured here. This is the flow documented for versions before the 24.2.a update. The newer flow is in [office-365-after-24-2-a.md](office-365-after-24-2-a.md) (includes a comparison table).

## Overview
- FortiCASB uses an API-based approach, pulling data from Office 365 via RESTful API; the portal accesses collected data with OAuth2.0 authentication. Data is combined to monitor user activities and provide DLP Data Analysis for files. [src: forticasb-admin-guide-24-4-b, p.191]
- Since FortiCASB 21.2 (2021), multiple Microsoft online apps under the same Office 365 account are supported; any in active use with the same account are monitored once the account is added. [src: forticasb-admin-guide-24-4-b, p.191]

| Microsoft online app | Monitoring detail |
|---|---|
| Microsoft Yammer | Monitors shared files at SharePoint sites |
| Microsoft OneDrive | Monitors all files shared privately or publicly |
| Microsoft SharePoint | Monitors files in Document and "user-created" folders |
| Azure Active Directory | Monitors all user activities |

[src: forticasb-admin-guide-24-4-b, p.191]

## Prerequisite order
1. Office 365 account and license (account with Global Administrator role).
2. Activate Office 365 account audit log.
3. Add admin to SharePoint site.
4. Add Office 365 account in FortiCASB.

[src: forticasb-admin-guide-24-4-b, p.191-192]

## Account and license requirements
- Existing or new account. A new account needs at least 24 hours to take effect before granting access to FortiCASB.
- License plan must include Active Directory integration (FortiCASB needs it for most features). Supported: Office 365 Business; Business Essentials; Business Premium; ProPlus; Enterprise E1; Enterprise E3; Enterprise E5; Enterprise K1.
- The Global Administrator role is required to add the account to FortiCASB.
- Microsoft Entra ID P2 (formerly Azure AD P2) is recommended. Without it, Discovery cannot access user entitlements, producing errors in the onboarding status; other major functions are unaffected. Consequences: in Office 365 > Users the Advanced Permission section shows "This users has no Advanced Permission" even for a global administrator; insufficient data to show Privileged User in Office 365 > Users.
- Microsoft Entra Privileged Identity Management must also be activated.
- Reference links given: https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-get-started-premium and https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-configure

[src: forticasb-admin-guide-24-4-b, p.192-193]

### Determine the license type
1. Log in at https://www.office.com/.
2. Click the Apps button (top-left), select Admin (redirects to Microsoft 365 admin center).
3. Go to Billing > Your Products; shows the Office 365 license and the Entra ID P2 license if purchased.

[src: forticasb-admin-guide-24-4-b, p.194]

## Activate Office 365 audit log
Needed to record user and admin activities. It may take several hours after enabling before FortiCASB receives audit logs.
1. Log in to https://www.office.com/ as the admin user.
2. Click the Office 365 menu option and select Admin portal (Microsoft 365 admin center).
3. Expand the left menu and click Security (Microsoft 365 Defender page).
4. Scroll the left menu and click Audit.
5. In Audit, click Start recording and admin activity.
   - If the option is not shown, the organization has already enabled it.
   - For a new tenant the option appears only 24 hours after tenant creation.
6. After turning on auditing allow 24 hours for it to become available.

Gotcha: an error when adding Office 365 to FortiCASB may mean auditing is not yet enabled; wait. [src: forticasb-admin-guide-24-4-b, p.194-196]

## Add admin to SharePoint site
Verify the account is one of the Company Administrators of the SharePoint sites so FortiCASB can monitor and protect them.
1. Log in to https://office.com with the admin account to be added to FortiCASB.
2. Click App Launcher (top-left), select Admin.
3. In the Microsoft 365 admin center left menu click Show all; under Admin Centers click SharePoint.
4. In SharePoint admin center open the Sites drop-down and select Active Sites (guide spells "Active Sties").
5. In the Primary admin column, scroll to find "Company Administrator".
6. Click the Site name of the user shown as "Company Administrator".
7. In the site profile dialog click the Membership tab.
8. Click + Add site admins and add your account.

To cover other SharePoint sites of the same domain, repeat steps 6-8 per site. [src: forticasb-admin-guide-24-4-b, p.196-199]

## Add Office 365 account in FortiCASB
1. Log in to FortiCASB.
2. Overview > Dashboard, click Add New, select Office 365, click Add Selected Cloud App.
3. Confirm all Office 365 configuration is done, click Grant Access @Office 365; log in with the account password on the Office 365 login screen.
4. Accept the permission prompt (FortiCASB requests partial permissions from the global administrator).
5. Click Accept. Office 365 may ask three more times to grant access; then you return to FortiCASB.

The installation checklist and status show in the Office 365 dashboard; allow up to 15 minutes. [src: forticasb-admin-guide-24-4-b, p.200-203]

### Permissions requested at consent (verbatim display text)
Manage access reviews that you can access; Read applications; Read audit log data; Read consent requests; Read your contacts; Read delegated permission grants; Access the directory as you; Read directory data; Read domains; Read all files that you have access to; Have full access to all files you have access to; Read all groups; Read all OneNote notebooks that you can access; Maintain access to data you have given it access to; Read organization information; Read all users' relevant people lists; Read your organization's policies; Read your organization's conditional access policies; Read your organization's identity protection policy; Read consent and permission grant policies; Read privileged access to Azure AD; Read privileged access to Azure AD groups; Read privileged access to your Azure resources; Read directory RBAC settings; Read your organization's security actions; Read your organization's security events; Have full control of all your site collections; Create, edit, and delete items and lists in all your site collections; Read items in all site collections; Edit or delete items in all site collections; Export user's data; Sign you in and read your profile; Read all users' full profiles; Read all users' basic profiles; Read and write user profiles; Read and write your files; Have full control of all site collections; Read and write items and lists in all site collections; Read and write items in all site collections; Run search queries; Read and write managed metadata; Read activity data for your organization; Read DLP policy events including detected sensitive data; Read service health information for your organization.

[src: forticasb-admin-guide-24-4-b, p.201-203]

## Update Office 365 account
Complete the same configuration with the same Office 365 account first (license, audit log, SharePoint site admin), then:
1. Log in to FortiCASB, go to Overview > Dashboard.
2. Click the Office 365 Account menu and select Update Cloud Account.
3. Confirm configuration is complete and click Grant Access @Office 365; log in on the Office 365 screen.
4. Accept the permission prompt. The update-time list (p.205-207, table layout partly garbled in extraction) contains: Read and write files in all site collections; Read items in all site collections (preview); Read files in all site collections; Read and write all users' full profiles; Read all users' full profiles; Read and write items in all site collections (preview); Read all groups; Read and write all groups; Read directory data; Read and write directory data; Access directory as the signed in user; Read all files that user can access; Read items in all site collections; Read activity report for your organization; Read activity data for your organization; Sign in and read user profile.
5. Office 365 may ask 3 more times to grant access, then returns to FortiCASB.

Allow up to 15 minutes for the update. [src: forticasb-admin-guide-24-4-b, p.204-207]

## Gotcha: new Office 365 users after onboarding
After onboarding, existing users are protected through Data Scan. A user added later has OneDrive data that is not accessible, so no data scan; SharePoint site data has a similar issue.
- OneDrive: add the onboarding service account user to the new user's OneDrive Site Collection Administrators, via the FortiCASB account update process or manually in the user's OneDrive settings. See "Insufficient Permissions (Access Denied) Error (One Drive)" (guide p.547).
- SharePoint: add the onboarding account to the SharePoint Site admin group via account update or manually in SharePoint admin center. See "Insufficient Permissions (Access Denied) Error (SharePoint)" (guide p.550).

[src: forticasb-admin-guide-24-4-b, p.207-208]

## Related
- [office-365-after-24-2-a.md](office-365-after-24-2-a.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
- [../company-and-first-time-setup.md](../company-and-first-time-setup.md)
