---
title: Troubleshooting - Office 365
summary: Symptom, cause and fix guidance for Office 365 site collection admin, users, groups, sync and Insufficient Permissions (OneDrive and SharePoint) errors.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Troubleshooting: Office 365

| Symptom | Cause | Fix |
|---|---|---|
| Add Site Collection Admin error | Feature supports only the default Azure domain format (abc.onmicrosoft.com); custom SharePoint homepage URL in use | Add site collection owner manually (below) |
| Add Users error | Users never logged into their Office 365 account, so SharePoint portal is not activated | Log into the account once, then add the user in FortiCASB |
| Add Groups error | Group does not generate or manipulate files, or site admin lacks permission to monitor it | None required; FortiCASB skips these groups and monitors the rest |
| "System Automatic Sync NOT Completed" | Listed users share the same O365 account but have not been granted permission to be monitored | Add global/SharePoint admin as Site Collection Administrator (below) |
| Insufficient Permissions (Access Denied), OneDrive file | Onboarding service account not a Site Collection Administrator of the user's OneDrive | Update Office 365 account in FortiCASB, or add manually |
| Insufficient Permissions (Access Denied), SharePoint file | Onboarding service account not a SharePoint site admin | Update Office 365 account in FortiCASB, or add manually |

## Add Site Collection Admin errors: customized SharePoint URL
1. Microsoft 365 Admin Center: Show all, then SharePoint.
2. SharePoint Admin Center: More features, under User profiles click Open.
3. User Profiles: Manage User Profiles.
4. Find the user, click the account name, select Manage site collection owners.
5. Enter your admin username in Site Collection Administrators, click Ok.

FortiCASB can then audit that user's OneDrive. Repeat for each user to audit.

[src: forticasb-admin-guide-24-4-b, p.542-544]

## Add Users errors
FortiCASB still monitors users that do not trigger the error (the guide's example: 37 users added successfully remain monitored). For brand-new Office 365 accounts, Office 365 activates the SharePoint portal on first login; log in once, then add the user.

[src: forticasb-admin-guide-24-4-b, p.544]

## Add Groups errors
FortiCASB does not monitor groups that do not generate or manipulate files, or groups the site administrator lacks permission to monitor. Other groups are still monitored.

[src: forticasb-admin-guide-24-4-b, p.544-545]

## System Automatic Sync NOT Completed
Click View Error Message on the Office 365 Dashboard to see the affected users. The error does not stop account monitoring and protection, but DLP (Data Analysis) scans cannot run on those users' OneDrive accounts.

Manually activate the site collection:
1. Log into https://admin.microsoft.com/ as global administrator.
2. Under Admin centers, click SharePoint.
3. Click More features, open User profiles.
4. Under People, select Manage User Profiles.
5. In Find profiles, enter a licensed user under the global administrator account and click Find.
6. Right-click the account name, select Manage site collections owners.
7. Add the global or SharePoint administrator username or e-mail to Site Collection Administrators and press Enter.
8. Click Ok.

[src: forticasb-admin-guide-24-4-b, p.545-547]

## Insufficient Permissions (Access Denied): OneDrive
This is a Data Scan Status in Office 365 > Files. Cause: the service account used for onboarding is not in the new user's OneDrive Site Collection Administrators.

- Solution 1: in FortiCASB, update the Office 365 account and follow the instructions; the service account is added automatically on success.
- Solution 2 (manual): log into the new user's Office 365 account, Apps menu > OneDrive; settings icon > OneDrive settings; More Settings > Manage access > Site Collection administrators; confirm the onboarding service account is listed, add it if not, click Ok.

[src: forticasb-admin-guide-24-4-b, p.547-550]

## Insufficient Permissions (Access Denied): SharePoint
Cause: the onboarding service account is not one of the SharePoint site's admins.

- Solution 1: update the Office 365 account in FortiCASB; the account is added automatically to SharePoint Site Administrators.
- Solution 2 (manual): first verify the account is a Company Administrator and is the one used for onboarding. Then:
  1. Log into https://office.com, open the App Launcher, select Admin.
  2. In Microsoft 365 admin center, Show all, Admin Centers > SharePoint.
  3. Sites > Active sites.
  4. Locate the target site under Site name and click it; open the Membership tab.
  5. Click +Add site admins and add the Company Administrator account.
  6. For other SharePoint sites in the same domain, repeat steps 4-5.

[src: forticasb-admin-guide-24-4-b, p.550-554]

## Related
- [Troubleshooting index](index.md)
- [Office 365 onboarding (after 24.2.a)](../onboarding/office-365-after-24-2-a.md)
- [Office 365 onboarding (before 24.2.a)](../onboarding/office-365-before-24-2-a.md)
