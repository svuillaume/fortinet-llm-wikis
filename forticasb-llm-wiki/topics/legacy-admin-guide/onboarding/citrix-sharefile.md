---
title: Onboarding Citrix ShareFile
summary: ShareFile user-access setup, subdomain entry, and OAuth add/update steps for Citrix ShareFile in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Citrix ShareFile

FortiCASB pulls data from Citrix ShareFile via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and provides DLP Data Analysis for files on ShareFile. No separate prerequisites section exists in the guide; the user must be an administrator (see step 3). Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.91]

## Add Citrix ShareFile account
1. Log into Citrix ShareFile.
2. Left navigation: **People** drop-down > **Browse Employees**.
3. Click the user with administrator privilege to be added to FortiCASB.
4. Scroll to **Employee User Settings**, expand **User Access**, check **Select All** to include all permissions.
5. Scroll down and click **Save Changes**.
6. In FortiCASB: **Overview > Dashboard** > **Add New** > **Citrix ShareFile** > **Add Selected Cloud App**.
7. Enter the **ShareFile Subdomain**, e.g. `https://SUBDOMAIN.sharefile.com`.
8. Click **Grant Access@ShareFile**; you are redirected to the ShareFile OAuth page.
9. Enter your ShareFile domain and credentials to complete validation.

Important: the user added to FortiCASB must be the same user currently logged into ShareFile; otherwise log out and log back in with the right user. Adding may take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.91-94]

## Update Citrix ShareFile account
1. Log into ShareFile. 2. **People** > **Browse Employees**. 3. Click the administrator user. 4. **Employee User Settings** > **User Access** > **Select All**. 5. **Save Changes**.
6. In FortiCASB go to **Overview > Dashboard**.
7. Open the Citrix ShareFile account menu, select **Update Cloud Account**.
8. Enter the **ShareFile Subdomain** (same user-match warning applies).
9. Click **Grant Access@ShareFile** (redirect to ShareFile OAuth page).
10. Enter ShareFile domain and credentials.

The guide again notes a possible 15-minute completion time; status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.94-97]

## Related
- [Onboarding index](index.md)
- [Egnyte](egnyte.md)
- [Polling intervals](../polling-intervals.md)
