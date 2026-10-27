---
title: Webex Teams onboarding
summary: Full Administrator requirement in Cisco Webex Control Hub and the OAuth grant flow for adding or updating Webex Teams in legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Webex Teams onboarding

Note: screenshots in the guide were not extracted.

## Overview
API-based via RESTful API with OAuth2.0. FortiCASB protects files shared in Webex Teams space chats (virus protection, compliance-violation monitoring) and monitors events for suspicious user activity or unauthorized events. [src: forticasb-admin-guide-24-4-b, p.263]

### Monitored activity types
The guide presents a table with columns Admin, Regular, Event (Without IP), Event (With IP); the column assignment was lost in text extraction. Activities listed: File Activities (Upload File, Delete File); Create User; Delete User; Create Memberships; Delete Memberships; Update Memberships; Participant Join Meeting; Participant Left Meeting. [src: forticasb-admin-guide-24-4-b, p.264]

## Prerequisites
The Webex account must be under a Basic, Business, or Enterprise subscription plan. [src: forticasb-admin-guide-24-4-b, p.264]

## Configure the Webex admin account
1. Log in to Cisco Webex Admin with the Webex admin account.
2. Click the user profile icon drop-down and click Cisco Webex Control Hub.
3. In Control Hub navigation click Management > Users.
4. Click the user to be added to FortiCASB. Under Roles and Security > Administrator Roles, ensure the user is a Full Administrator (ask another admin to assign it if needed).

[src: forticasb-admin-guide-24-4-b, p.264-265]

## Add Webex Teams account (FortiCASB)
1. Log in to FortiCASB.
2. Overview > Dashboard > Add New > Webex Teams > Add Selected Cloud App.
3. Review the key configurations list and click Grant Access@Webex (redirects to Webex OAuth verification). Note: log out of Webex first if another account is logged in on another page.
4. Enter Webex credentials and press Submit; return to FortiCASB.

May take 15 minutes; check status in Overview > Dashboard. [src: forticasb-admin-guide-24-4-b, p.266-267]

## Update Webex Teams account
Redo the admin configuration with the same account, then:
1. Log in to FortiCASB; Overview > Dashboard.
2. Open the Webex Teams menu, select Update Cloud Account.
3. Review the key configurations list, click Grant Access@Webex (same log-out note applies).
4. Enter Webex credentials, press Submit.

May take 15 minutes. [src: forticasb-admin-guide-24-4-b, p.267-268]

## Related
- [zoom.md](zoom.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
