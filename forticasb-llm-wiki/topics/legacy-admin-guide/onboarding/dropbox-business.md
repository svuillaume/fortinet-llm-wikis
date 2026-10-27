---
title: Onboarding Dropbox Business
summary: Plan and Team Admin prerequisites plus OAuth add/update steps for Dropbox Business in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Dropbox Business

FortiCASB pulls data from Dropbox Business via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and provides DLP Data Analysis. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.113]

## Prerequisites
- Dropbox Business plan: **Essentials**, **Business**, or **Business Plus**.
- The account added to FortiCASB must have the **Team Admin** permission.
- Existing or new account.

[src: forticasb-admin-guide-24-4-b, p.114]

## Add Dropbox Business
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > **Dropbox** > **Add Selected Cloud App**.
3. Click **Grant Access @Dropbox** (redirects to Dropbox).
4. Log in; Dropbox prompts allow or deny.
5. Click **Allow**.
6. Redirected to the FortiCASB dashboard; check installation result and SaaS platform monitoring status in the Dropbox dashboard.

Troubleshooting is referenced at guide p.537 (outside this range). [src: forticasb-admin-guide-24-4-b, p.115-116]

## Update Dropbox Business
1. Log into FortiCASB; **Overview > Dashboard**.
2. Open the Dropbox account menu, select **Update Cloud Account**.
3. Click **Grant Access @Dropbox**.
4. Log in to authenticate; **Allow**.
5. Redirected to the dashboard; check account checklist and platform monitoring status in the Dropbox dashboard.

[src: forticasb-admin-guide-24-4-b, p.117-118]

## Related
- [Onboarding index](index.md)
- [Box](box.md)
- [User management and permissions](../user-management-and-permissions.md)
