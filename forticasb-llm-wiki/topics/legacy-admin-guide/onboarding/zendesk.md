---
title: Zendesk onboarding
summary: Creating a Zendesk OAuth client with FortiCASB regional redirect URLs and adding or updating the account in legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Zendesk onboarding

Note: screenshots in the guide were not extracted.

## Overview and prerequisites
API-based via RESTful API with OAuth2.0; FortiCASB monitors user activities and the ticketing system and provides DLP Data Analysis for files on tickets.
1. The Zendesk account must be under an Enterprise plan.
2. The account added to FortiCASB must have the Admin Role in Support.
3. A Zendesk OAuth Client must be created to authorize FortiCASB REST API access.

[src: forticasb-admin-guide-24-4-b, p.269]

## Step 1: Create Zendesk OAuth client
1. Log in to Zendesk with your sub-domain, then with the admin account.
2. Left navigation: Admin, scroll to Channels, click API.
3. On the Zendesk API page select the OAuth Clients tab, click Add OAuth client.
4. Enter a Client Name, Short Description, and Unique Identifier (auto-populated). Record the unique identifier.
5. In Redirect URLs use the FortiCASB URL for your region:

| Region | Redirect URL |
|---|---|
| Global | https://www.forticasb.com/api/v1/oauth/redirect/Zendesk |
| European Union | https://eu.forticasb.com/api/v1/oauth/redirect/Zendesk |

6. Click Save, then in the Secret field click Generate. Copy the secret token; it appears only once.

[src: forticasb-admin-guide-24-4-b, p.270-271]

## Step 2: Add Zendesk account (FortiCASB)
1. Log in to FortiCASB.
2. Overview > Dashboard > Add New > Zendesk > Add Selected Cloud App.
3. Fill in Zendesk Sub-Domain, Unique Identifier, and the Secret Token; click Add Zendesk Account.
4. Authorize FortiCASB in Zendesk: click Allow.
5. Wait 15 minutes.

[src: forticasb-admin-guide-24-4-b, p.271-273]

## Update Zendesk account
Repeat Step 1 (create a new OAuth client, same values as above), then:
1. Log in to FortiCASB; Overview > Dashboard.
2. Open the Zendesk account menu, select Update Cloud Account.
3. Fill in Zendesk Sub-Domain, Unique Identifier, Secret Token; click Update Zendesk Account.
4. Click Allow on the Zendesk authorization prompt.
5. Wait 15 minutes.

[src: forticasb-admin-guide-24-4-b, p.274-276]

## Gotchas
- Secret token is displayed once only.
- Pick the redirect URL matching the FortiCASB region (Global vs EU).

## Related
- [servicenow.md](servicenow.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
