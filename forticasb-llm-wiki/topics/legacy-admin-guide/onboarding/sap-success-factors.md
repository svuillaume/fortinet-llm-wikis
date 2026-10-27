---
title: SAP SuccessFactors onboarding
summary: Registering an OAuth2 client application with an X.509 certificate, granting Manage Integration Tools permissions, and adding or updating SAP SuccessFactors in legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# SAP SuccessFactors onboarding

Note: screenshots were not extracted; the Location and Environment option list is shown only as a screenshot and is not available (not found in sources).

## Overview
API-based via RESTful API; authentication through OAuth2.0, with FortiCASB using an access token for API queries. FortiCASB monitors user activities and provides DLP Data Analysis for files shared on the platform. Add flow: Step 1 register OAuth client application, Step 2 set permission scope, Step 3 add the account in FortiCASB. [src: forticasb-admin-guide-24-4-b, p.238-239]

## Step 1. Register OAuth client application (SuccessFactors)
1. Log in to SAP SuccessFactors, go to Admin Center. In the Tools box search for and open Manage OAuth2 Client Applications.
2. Click Register Client Application.
3. Enter an application name (example: FortiCASB Integration) and an Application URL (example: https://www.forticasb.com/).
4. At the bottom click Generate X.509 Certificate. On the "Self Assign a new X.509 Certificate" page enter a Common Name and click Generate.
5. You return to the previous page with certificate values filled. Click Download to save the certificate pem file (used later as the private key), then click Register.
6. Open the OAuth2 application just created; the API Key is generated automatically. Record the API Key and the Company ID.

[src: forticasb-admin-guide-24-4-b, p.239-241]

## Step 2. Set permission scope
1. Admin Center > User Role Search.
2. Look up the User ID to be added in FortiCASB and note the Roles under that user.
3. Admin Center > Manage Permission Role.
4. Look up one of the user's roles (example: System Admin) and open it.
5. In Permission Role Detail click Permission.
6. Scroll down, select Manage Integration Tools, click Select All to add all integration permissions, click Done.

[src: forticasb-admin-guide-24-4-b, p.241-243]

## Step 3. Add account in FortiCASB
1. Log in to FortiCASB.
2. Overview > Dashboard > Add New > SAP SuccessFactors > Add Selected Cloud App.
3. Review the configuration list, confirm complete, click Next Step.
4. Enter SAP Success Factors Company ID, the API Key saved earlier, and the SAP Success Factors User ID.
5. Open the Location and Environment drop-down and select one (options not extracted).
6. Upload the X.509 certificate pem file saved earlier and click Add SAP Success Factors Account.
7. Wait 15 minutes for the account to be fully added.

[src: forticasb-admin-guide-24-4-b, p.243-246]

## Update account
Repeat Step 1 (register a new OAuth client application and certificate) and Step 2 (permission scope) exactly as above, then:
1. Log in to FortiCASB; Overview > Dashboard.
2. Open the SAP Success Factors account menu, select Update Cloud Account.
3. Review the configuration list, click Next Step.
4. Enter Company ID, API Key, and User ID.
5. Select Location and Environment.
6. Upload the X.509 certificate pem file and click Update SAP Success Factors Account.
7. Wait 15 minutes.

[src: forticasb-admin-guide-24-4-b, p.246-253]

## Gotchas
- The downloaded pem file is required again at FortiCASB add/update; keep it.
- The permission role grant applies to a role of the user whose User ID is entered in FortiCASB.

## Related
- [sap-ias.md](sap-ias.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
