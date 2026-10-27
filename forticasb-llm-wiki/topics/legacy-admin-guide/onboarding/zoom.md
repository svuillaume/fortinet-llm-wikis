---
title: Zoom onboarding
summary: Zoom role settings, account-level OAuth app with event subscription and scopes, and the FortiCASB add/update steps for legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Zoom onboarding

Note: screenshots in the guide were not extracted.

## Overview and prerequisites
API-based via RESTful API with OAuth2.0; FortiCASB monitors Zoom user activities and provides DLP Data Analysis for files shared through Zoom.
- Zoom plan must be Pro, Business, Business Plus, or Enterprise. Free plan is NOT supported.
- The Zoom user added must be the Account Owner or Admin.

[src: forticasb-admin-guide-24-4-b, p.276]

## Part 1: Zoom role settings
1. Log in to Zoom as Account Owner or Admin.
2. Left pane: ADMIN > User Management > Roles.
3. In the Admin Role section click the Admin Role Settings icon.
4. On the Role Settings tab ensure checked: User and Permission Management: Users: View; Role management: View. Team Chat Management: Chat Channels: View; Chat messages: View.

[src: forticasb-admin-guide-24-4-b, p.277-278]

## Part 2: Create OAuth app on Zoom
1. Log in as the same Account Owner or Admin.
2. ADMIN > Advanced > App Marketplace.
3. Top right: Develop drop-down > Build App.
4. Select OAuth app type, click Create.
5. Enter an App name; select Account-level app; uncheck the option to publish the app on Zoom App Marketplace; click Create.
6. In App Credentials record Client ID and Client Secret.
7. Copy the Redirect URL for OAuth from the FortiCASB Add Zoom Account page and paste into Redirect URL for OAuth.
8. Scroll to OAuth allow list, add the same redirect URL to the allow list, click Continue.
9. Basic Information: Short Description, Long Description, Company Name. Developer Contact Information: Name and E-Mail Address. Click Continue. (The app cannot be created without these.)
10. In Add Feature record the Secret Token.
11. Turn on Event Subscription, then: (a) +Add new subscription and enter a Subscription Name; (b) on the FortiCASB Add Zoom Account page paste the recorded Client ID into Client ID and click Generate to produce the Event Notification Endpoint URL; (c) paste that URL into Zoom's Event notification endpoint URL and click Validate.
12. In Add Events click +Add Events and add the event types below, then Done.
13. In Event notification receiver ensure "All users in the account" is selected; click Save.
14. Click Continue to reach the Scopes page.
15. +Add Scopes, add the scopes below, click Continue.
16. On the FortiCASB Add Zoom Account page enter the Zoom Client Secret and the Secret Token, click Grant Access @Zoom.
17. On the Zoom OAuth authorization page click Allow; you return to FortiCASB.
18. Wait 15 minutes and check account status.

[src: forticasb-admin-guide-24-4-b, p.278-285]

### Event types (grouping reconstructed from garbled table)
| Category | Events |
|---|---|
| User | User has been created; disassociated; deleted; activated; deactivated; User has accepted the account invitation; User's profile info has been updated |
| User Activity | User has signed in; User has signed out |
| Chat Channel | Chat Channel Created; Chat Channel Deleted; Member Removed; Member Left |
| Chat Message | Chat Message Sent; Updated; Deleted; Replied |

The guide's extracted table is column-misaligned; verify exact event names in the Zoom UI. [src: forticasb-admin-guide-24-4-b, p.283]

### Scopes
| Scope type | Scope |
|---|---|
| User | View all user information / user:read:admin |
| Team Chat | View all users' team chat channels / chat_channel:read:admin |
| Team Chat | View all users' team chat messages / chat_message:read:admin |
| Role | View all user roles / role:read:admin |

[src: forticasb-admin-guide-24-4-b, p.283]

## Update Zoom account
Redo Part 1 with the same Zoom account, then repeat Part 2 steps 1-17 with the same settings, except that the Redirect URL and Client ID/endpoint generation happen on the FortiCASB Update Zoom Account page (a new OAuth app is created). Open the update page via the Zoom account menu on Overview > Dashboard > Update Cloud Account (menu path assumed from other apps; not stated on these pages). After Grant Access @Zoom and Allow, wait 15 minutes and check status. [src: forticasb-admin-guide-24-4-b, p.286-292]

## Gotchas
- Event subscription URL validation requires the Client ID entered in FortiCASB first.
- Publishing to Zoom App Marketplace must stay unchecked (account-level app).

## Related
- [webex-teams.md](webex-teams.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
