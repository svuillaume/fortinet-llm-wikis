---
title: Onboarding Box
summary: Edition and permission prerequisites plus OAuth add/update steps for Box in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Box

FortiCASB pulls data from Box via RESTful API (portal access "with OAuth2.0 authentication"), monitors Box user activities and provides DLP Data Analysis for files stored on Box. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.85]

## Prerequisites
- Organization must use one of: **Business Edition**, **Enterprise Edition**, **Developer Edition** (API enabled by default).
- The user account installed in FortiCASB must have these permissions:
  - Read and write all files and folders stored in Box
  - Manage users
  - Manage groups
  - Manage enterprise properties
- Existing or new account; a new account needs at least 24 hours to take effect before granting access to FortiCASB.
- These features additionally require **Admin User** permission: user login tracking, user IP address tracking, geographical location tracking, user password change tracking, change admin role tracking.

Gotcha: without Admin User permission FortiCASB cannot obtain user login IPs, so user activity will not appear on the Activity map.

[src: forticasb-admin-guide-24-4-b, p.85]

## Add Box account
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > select **Box** > **Add Selected Cloud App**.
3. Click **Grant Access @Box**.
4. You are sent to the Box website; log in. Box prompts to allow or deny.
5. Click **Allow** to grant FortiCASB permission to monitor Box.
6. You are redirected to the FortiCASB dashboard; check the installation checklist and monitoring status in the Box dashboard.

Common install issues: guide refers to Troubleshooting (p.537, outside this page's source range). [src: forticasb-admin-guide-24-4-b, p.87-89]

## Update Box account
1. Log into FortiCASB; go to **Overview > Dashboard**.
2. Open the Box account menu, select **Update Cloud Account**.
3. Click **Grant Access @Box** to re-authenticate.
4. Log in on the Box website; click **Allow**.
5. Redirected to the FortiCASB dashboard; check installation checklist and SaaS platform monitoring status in the Box dashboard.

[src: forticasb-admin-guide-24-4-b, p.89-91]

## Related
- [Onboarding index](index.md)
- [Dropbox Business](dropbox-business.md)
- [User management and permissions](../user-management-and-permissions.md)
