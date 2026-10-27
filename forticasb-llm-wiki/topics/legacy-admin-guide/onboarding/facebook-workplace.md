---
title: Onboarding Facebook Workplace
summary: Custom integration (App ID, App Secret, access token) setup and FortiCASB add/update steps for Facebook Workplace in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Facebook Workplace

FortiCASB pulls data from Facebook Workplace via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and conducts DLP Data Analysis for files shared on Workplace. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.122]

## Prerequisites
- Workplace plan must be **Advanced** or **Enterprise**; free plan NOT supported.
- The Workplace account added to FortiCASB must be the **System Administrator** user.

[src: forticasb-admin-guide-24-4-b, p.122]

## Configure Workplace and add the account
1. Log into Workplace with the System Administrator account.
2. Left navigation: **Admin Panel** > **Integrations**.
3. Click **Create Custom Integration**, fill in **Name** and **Description**, click **Create**.
4. Under **Integration Details** note the **App ID** and **App Secret**; click **Create Access Token** and copy the token.
5. In FortiCASB: **Overview > Dashboard** > **Add New** > **Workplace** > **Add Selected Cloud App**.
6. Click **Next** on the Add Workplace Account page.
7. Enter **App ID**, **App Secret**, **Access Token**; click **Add Workplace Account**.

May take 15 minutes; check status in **Overview > Dashboard**. No custom-integration permission set is listed in the guide (not found in sources).

[src: forticasb-admin-guide-24-4-b, p.123-125]

## Update Workplace account
1. Repeat Workplace-side steps 1-4 above (create a custom integration, note App ID/App Secret, create a new access token).
2. In FortiCASB go to **Overview > Dashboard**.
3. Open the Workplace account menu, select **Update Cloud Account**.
4. Click **Next** on the Update Workplace Account page.
5. Enter **App ID**, **App Secret**, **Access Token**, and click the button labeled **Add Workplace Account** (the guide uses this label in the update procedure).

May take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.126-127]

## Related
- [Onboarding index](index.md)
- [GitHub](github.md)
- [Company and first-time setup](../company-and-first-time-setup.md)
