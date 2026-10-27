---
title: Onboarding Jira
summary: Browse Projects permission, Atlassian OAuth 2.0 (3LO) app, system webhook, and FortiCASB add/update steps for Jira Cloud in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Jira

FortiCASB pulls data from Jira via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and provides DLP Data Analysis for files on Jira tickets. Before adding, the Jira account is configured to grant FortiCASB read access; the account added in FortiCASB must be the same account that is configured. Screenshots were not extracted; the list of issue-related webhook events is shown only in a screenshot and is therefore not found in the extracted text. [src: forticasb-admin-guide-24-4-b, p.177]

## Prerequisites
- All Jira Cloud plans supported, including Free.
- The account user must be a **Site Admin** of the Jira service site.
- Step order: Jira Account Configuration, then Add Jira Account (the Browse Project permission section precedes configuration in the guide).

[src: forticasb-admin-guide-24-4-b, p.177]

## 1. Grant Browse Projects permission
The account used to add Jira must have **Browse Projects** permission on each Jira project to be monitored. The project must be a **Company-managed software** type to edit the access permission.
1. Go to the Jira project site; choose the project to monitor.
2. Open the project menu and select **Project settings**.
3. **Permissions**.
4. **Actions** drop-down > **Edit permissions**.
5. In the **Browse Projects** column, click **Update**.
6. Check **Single User**, type and select the account user used to add Jira to FortiCASB.
7. Click **Update**.

[src: forticasb-admin-guide-24-4-b, p.178-179]

## 2. Jira account configuration (Atlassian Developer Console)
1. Log in to the Atlassian Developer Console as Site Admin.
2. **Create App** drop-down > **OAuth 2.0 (3LO) integration**.
3. Enter an **App name**, agree to Atlassian's developer terms, click **Create**.
4. Left menu **Permissions**; API name > **Jira API** > **Add**; when it turns to **Configure**, click it.
5. **Classic scopes** tab, section **Jira Platform REST API**: **Edit Scopes**.
6. Check all scopes in "Edit Jira Platform REST API" and **Save**.
7. **Permissions** again; **User Identity API** > **Add** > **Configure**.
8. **Edit Scopes**, add the **View User Profile** scope, **Save**.
9. Left menu **Authorization**; Authorization type **OAuth 2.0 (3LO)** > **Add**.
10. **Callback URL**: enter the callback URL from the FortiCASB Add Jira Account page; **Save Changes**.
11. Left menu **Settings**; under **Authentication details** note **Client ID** and **Secret**.

[src: forticasb-admin-guide-24-4-b, p.180-182]

## 3. Add Jira account in FortiCASB
1. Log into FortiCASB.
2. **Overview > Dashboard** > **+Add New** > **Jira** > **Add Selected Cloud App**.
3. Fill in **Jira Site Domain name** (site domain prefix: for `https://mydomain.atlassian.net/` it is `mydomain`), **Client ID**, **Client Secret**.
4. Click **Next Step**.
5. Click the **Jira** link to open the Jira Domain Projects page.
6. Click **Settings** (upper right) > **System**.
7. Left menu: scroll to the bottom and select **Webhooks**.
8. **+Create Webhook**.
9. Enter a **Name** and set status **Enabled**.
10. Copy the **Webhook URL** from the FortiCASB Add Jira Account page into the **URL** field.
11. Under **Events**, check the issue-related events (list shown only in a screenshot; not extracted).
12. Click **Create**.
13. Back on the FortiCASB Add Jira Account page, click **Grant Access @Jira**.
14. On the Jira OAuth site click **Accept**; you are redirected to FortiCASB.

May take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.183-186]

## Update Jira account
Complete the Jira account configuration (section 2) with the same Jira account first. Then:
1. Log into FortiCASB; **Overview > Dashboard**.
2. Jira account menu > **Update Cloud Account**.
3. Fill in **Jira Site Domain name**, **Client ID**, **Client Secret**; **Next Step**.
4. Click the **Jira** link; **Settings > System**; **Webhooks** (bottom of left menu).
5. **+Create Webhook**; enter a **Name**; status **Enabled**.
6. Paste the **Webhook URL** from the FortiCASB Update Jira Account page into **URL**.
7. Under **Events** check the issue-related events; click **Create**.
8. On the FortiCASB Update Jira Account page click **Grant Access @Jira**.
9. On the Jira OAuth site click **Accept**; redirected to FortiCASB.

May take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.187-190]

## Gotchas
- Browse Projects can only be edited on Company-managed software projects.
- Webhook is created at Settings > System > Webhooks (instance level), unlike Confluence which uses a Webhook Manager marketplace app.
- Update procedure creates another webhook; whether an old webhook should be removed is not found in sources.

## Related
- [Onboarding index](index.md)
- [Confluence](confluence.md)
- [Polling intervals](../polling-intervals.md)
