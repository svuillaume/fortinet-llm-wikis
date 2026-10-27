---
title: ServiceNow onboarding
summary: Creating a ServiceNow developer instance and OAuth API endpoint (application registry) and adding or updating the account in legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# ServiceNow onboarding

Note: screenshots in the guide were not extracted.

## Overview and prerequisites
API-based via RESTful API with OAuth2.0; FortiCASB monitors user activities and provides DLP Data Analysis for files stored on ServiceNow tickets. An OAuth API Endpoint must be created in ServiceNow (via an application registry on a ServiceNow instance) before adding the account. Only ServiceNow Istanbul or higher is supported. Sequence: create developer instance, create OAuth API endpoint, add account. [src: forticasb-admin-guide-24-4-b, p.253]

## Create ServiceNow developer instance
Skip if you have an existing developer instance.
1. Log in to the ServiceNow Developer Home page.
2. Click Request Instance (right corner).
3. Choose an instance type and click Request.
4. Wait a few minutes for creation.
5. Record the instance URL and credentials provided.

[src: forticasb-admin-guide-24-4-b, p.254-255]

## Create ServiceNow OAuth API endpoint
1. Go to the instance, e.g. `https://<Instance ID>.service-now.com/`.
2. Log in with the instance credentials.
3. Click All in the navigation menu, scroll or search for System OAuth, click Application Registry.
4. Click New (upper right).
5. Select Create an OAuth API endpoint for external clients.
6. Enter a unique Name and a Client Secret for the OAuth client application.
7. In Redirect URL enter the Redirect URL shown in step 4 of the FortiCASB Add ServiceNow Account page.
8. Record the Client ID and Client Secret.
9. Leave Refresh Token Lifespan and Access Token Lifespan at default.
10. Click Submit and return to the FortiCASB Add ServiceNow Account page.

[src: forticasb-admin-guide-24-4-b, p.255-258]

## Add ServiceNow account (FortiCASB)
1. Log in to FortiCASB.
2. Overview > Dashboard > Add New > ServiceNow > Add Selected Cloud App.
3. Review the key configurations list and click Next.
4. Enter Client ID and Client Secret recorded earlier, and your ServiceNow url (the Redirect URL for ServiceNow step 7 is displayed on this page).
5. Click Add ServiceNow Account. It may take 15 minutes; check status in Overview > Dashboard.

[src: forticasb-admin-guide-24-4-b, p.259-261]

## Update ServiceNow account
Complete the same ServiceNow configuration (developer instance, OAuth endpoint) with the same account first, then:
1. Log in to FortiCASB; Overview > Dashboard.
2. Open the ServiceNow menu, select Update Cloud Account.
3. Review the key configurations list, click Next.
4. Enter Client ID, Client Secret and ServiceNow url.
5. Click Update ServiceNow Account. It may take 15 minutes; check status in Overview > Dashboard.

[src: forticasb-admin-guide-24-4-b, p.261-263]

## Gotchas
- The guide's "Client Secret" is entered by the admin in ServiceNow in step 6; record it as FortiCASB asks for it.
- The Redirect URL comes from FortiCASB, so start the FortiCASB add wizard first.

## Related
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
- [zendesk.md](zendesk.md)
