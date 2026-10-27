---
title: Onboarding GitHub
summary: Organization plan and Owner prerequisites plus OAuth add/update steps for GitHub in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding GitHub

FortiCASB pulls data from GitHub via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and provides DLP Data Analysis for files stored on GitHub. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.128]

## Prerequisites
- Organization plan: **Free**, **Team**, or **Enterprise**. Personal User accounts are NOT supported.
- The GitHub account added to FortiCASB must be the **Organization Owner**; other roles not supported.

[src: forticasb-admin-guide-24-4-b, p.128]

## Add GitHub account
1. Log into FortiCASB.
2. **Overview > Dashboard**.
3. **Add New** > **GitHub** > **Add Selected Cloud App**.
4. Verify the account meets the requirements; click **Next Step**.
5. Enter **GitHub Organization Name** and **Username or e-mail address** of the account; click **Grant Access@GitHub**.
6. You are redirected to the GitHub OAuth page requesting authorization of FortiCASB access to the organization.
7. Under **Organization Access**: (a) click **Grant** for the organization; (b) click **Authorize (username)**. You are redirected to FortiCASB.

Wait 15 minutes, then check the account status. (The guide's lead-in sentence says "update" for the add procedure; a typo.)

[src: forticasb-admin-guide-24-4-b, p.128-131]

## Update GitHub account
1. Log into FortiCASB; **Overview > Dashboard**.
2. Open the GitHub account menu, select **Update Cloud Account**.
3. Verify requirements; **Next Step**.
4. Enter **GitHub Organization Name** and username/e-mail; **Grant Access@GitHub**.
5. On GitHub OAuth page, under **Organization Access** click **Grant**, then **Authorize (username)**; redirected back to FortiCASB.

[src: forticasb-admin-guide-24-4-b, p.131-133]

## Related
- [Onboarding index](index.md)
- [Jira](jira.md)
- [User management and permissions](../user-management-and-permissions.md)
