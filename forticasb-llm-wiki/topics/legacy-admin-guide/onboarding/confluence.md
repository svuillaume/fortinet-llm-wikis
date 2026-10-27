---
title: Onboarding Confluence
summary: Atlassian OAuth 2.0 app, scopes, webhook install and creation, and FortiCASB add/update steps for Confluence Cloud in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Confluence

FortiCASB pulls data from Confluence via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and provides DLP Data Analysis. Before adding, the Confluence account is configured to grant FortiCASB read access; the account added in FortiCASB must be the same account that was configured. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.97]

## Prerequisites
- Confluence plan must be **Standard, Premium or Enterprise**. Free plan NOT supported.
- The account must be the **Organization and Site Admin** of the Confluence site used in FortiCASB.

Sequence (guide order): install Webhook on Confluence; Confluence account configuration; add Confluence account. [src: forticasb-admin-guide-24-4-b, p.97]

## 1. Confluence account configuration (Atlassian Developer Console)
1. Log in to the Atlassian Developer Console as the Organization and Site Admin.
2. **Create App** drop-down > **OAuth 2.0 integration**.
3. Enter an **App name**, agree to Atlassian's developer terms, click **Create**.
4. Left menu: **Permission**.
5. In API name find **Confluence API**, click **Add**; when it becomes **Configure**, click it.
6. **Classic scopes** tab > **Edit Scopes**. Select and **Save**:
   - Read Confluence space summary
   - Read Confluence content properties
   - Read Confluence detailed content
   - Read Confluence content summary
   - Read content permissions in Confluence
   - Read user
   - Read user groups
   - Download content attachments
7. **Granular scopes** tab > **Edit Scopes**. Select and **Save**:
   - View audit records
   - View and download content attachments
   - View user details
8. **Permissions** again; find **User Identity API**, click **Add**, then **Configure**.
9. **Edit Scopes**, select and **Save**:
   - View active user profile
   - View user profiles
10. Left menu **Authorization**; Authorization type **OAuth 2.0 (3LO)** > **Add**.
11. In **Callback URL** enter the callback URL provided by FortiCASB; **Save Changes**. (The guide does not show the URL value; it is provided in FortiCASB.)
12. Left menu **Settings**; under **Authentication details** note the **Client ID** and **Secret** for FortiCASB.

[src: forticasb-admin-guide-24-4-b, p.98-101]

## 2. Install Webhook on Confluence
Webhooks are automated messages from Confluence to FortiCASB, faster than API calls, sent when targeted events fire. Required before adding Confluence.
1. Log into the Confluence site as the Organization and Site Admin.
2. Main menu: **Find new apps**.
3. Select **Webhook Manager for Confluence Cloud** and install it.

[src: forticasb-admin-guide-24-4-b, p.101-103]

## 3. Add Confluence account in FortiCASB
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > **Confluence** > **Add Selected Cloud App**.
3. Fill in **Confluence Site Domain name** (the site domain prefix: for `https://mydomain.atlassian.net/` it is `mydomain`), **Client ID** and **Client Secret**.
4. Click **Next Step**.
5. On "Add Confluence Account page 2", click the **Confluence** link (redirects to Atlassian).
6. On the Atlassian page, apps menu button > **Confluence**.
7. Confluence **Apps** drop-down > **Manage apps**.
8. Left menu: scroll to **Webhooks**.
9. **Add Webhook**.
10. Enter a name and enable the Webhook status.
11. **Event types** drop-down: select event types to monitor. Supported events are listed in the guide's "Confluence Events" section (p.326, outside this page's range).
12. Paste the **Webhook URL** from the FortiCASB Add Confluence page into the URL field.
13. Click **Grant Access @Confluence**.
14. On the Confluence OAuth validation site, open the **Authorize for** drop-down and select the Confluence site domain.
15. Click **Accept**; you are redirected to FortiCASB.

May take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.103-108]

## Update Confluence account
Complete the Confluence account configuration (section 1) first. Then:
1. Log into FortiCASB; **Overview > Dashboard**.
2. Open the Confluence account menu, select **Update Cloud Account**.
3. Fill in **Confluence Site Domain name**, **Client ID**, **Client Secret**; **Next Step**.
4. On "Update Confluence Account page 2" click the **Confluence** link.
5. Atlassian page: apps menu > **Confluence**; **Apps** > **Manage apps**; **Webhooks**.
6. **Add Webhook**; enter a name; enable status; select **Event types**.
7. Paste the **Webhook URL** from the FortiCASB Update Confluence page.
8. Click **Grant Access @Confluence**.
9. On the OAuth validation site: **Authorize for** > select site domain; click **Accept**; redirected to FortiCASB.

May take 15 minutes; check status in **Overview > Dashboard**. Note: the update procedure lists no webhook re-install step (Webhook Manager install is not repeated), only a new webhook creation.

[src: forticasb-admin-guide-24-4-b, p.108-113]

## Gotchas
- The same account must be used for Developer Console configuration and FortiCASB.
- Client ID/Secret are taken from the Developer Console Settings page.
- The webhook URL is unique to the FortiCASB add/update page; copy it from there.

## Related
- [Onboarding index](index.md)
- [Jira](jira.md) (also an Atlassian OAuth 2.0 app)
- [Polling intervals](../polling-intervals.md)
