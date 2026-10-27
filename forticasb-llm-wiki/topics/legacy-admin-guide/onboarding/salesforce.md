---
title: Salesforce onboarding
summary: Edition and permission prerequisites plus OAuth add/update procedure for connecting Salesforce to legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Salesforce onboarding

Note: screenshots in the guide were not extracted.

## Overview
API-based: FortiCASB pulls data from Salesforce via RESTful API; the portal accesses collected data with OAuth2.0 authentication, monitors user activities and provides DLP Data Analysis for files stored on Salesforce. [src: forticasb-admin-guide-24-4-b, p.223]

## Prerequisites
- Supported editions: Enterprise, Unlimited, Developer, Starter. Other editions are not supported.
- The user account added in FortiCASB must have these permissions: View All Data; View All Users; API Enabled.
- Existing or new account; a new account needs at least 24 hours before granting access to FortiCASB.
- "Manage Users" permission is additionally required for: user login tracking, user IP address tracking, geographical location tracking, user password change tracking. Without it FortiCASB cannot obtain user login IPs, so user activity does not appear on the Activity map.

[src: forticasb-admin-guide-24-4-b, p.223-224]

## Add Salesforce account (FortiCASB side)
1. Log in to FortiCASB.
2. Overview > Dashboard, click Add New, select Salesforce, click Add Selected Cloud App.
3. Click Grant Access @Salesforce (redirects to Salesforce).
4. Log in to authenticate; enter the custom Salesforce domain if you have one. Salesforce prompts to allow or deny.
5. Click Allow. You are redirected to the FortiCASB dashboard.

Check install result and SaaS platform monitoring status in the Salesforce dashboard. For common issues see the guide's Troubleshooting section (p.537). No Salesforce-side connected app or OAuth client setup is documented (not found in sources). [src: forticasb-admin-guide-24-4-b, p.224-227]

## Update Salesforce account
1. Log in to FortiCASB; Overview > Dashboard.
2. Open the Salesforce account menu, select Update Cloud Account.
3. Click Grant Access @Salesforce.
4. Log in (custom domain if applicable).
5. Click Allow; you return to the FortiCASB dashboard.

Check the installation checklist and platform monitoring status in the Salesforce Dashboard. [src: forticasb-admin-guide-24-4-b, p.227-228]

## Related
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
- [../user-management-and-permissions.md](../user-management-and-permissions.md)
