---
title: SAP IAS onboarding
summary: Creating an SAP IAS System administrator with client secrets and audit-log credentials, then adding or updating the account in legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# SAP IAS onboarding

Note: screenshots in the guide were not extracted.

## Overview
API-based: FortiCASB pulls data from SAP IAS via RESTful API with OAuth2.0 and monitors user activities such as logins, user assignments, updates and similar. [src: forticasb-admin-guide-24-4-b, p.228]

## Prerequisites
- The SAP IAS application must be hosted in the SAP infrastructure.
- A System Administrator must be created under the SAP IAS account to give FortiCASB access.

[src: forticasb-admin-guide-24-4-b, p.229]

## Add SAP IAS account
### SAP IAS side
1. Log in to the SAP IAS Administration Console; record the Tenant ID and the IAS Region.
2. Top menu: Users & Authorization > Administrators. Click Add in the top Administrators section and select Systems.
3. In Add Administrator > System Details: set a System Display name, turn all Configure Authorizations to ON, click Save.
4. In Configure System Authentication click Secrets.
5. Click +Add.
6. In the Add Secret pop-up enter a description, select an expiration duration, click Save.
7. A Client ID and Secret are generated; record them (they cannot be viewed again). These are the System Client ID and System Client Secret.
8. Top navigation: Monitoring & Reporting > Audit and Change Logs.
9. Click +Generate to generate client credentials for audit logs.
10. A new audit log Client ID and Secret are generated; record them (not viewable again). These are the Audit Logs Client ID and Audit Logs Client Secret.

### FortiCASB side
11. Return to the FortiCASB Add SAP IAS Account page.
12. Click Next Step.
13. Enter System Client ID, System Client Secret, Audit Logs Client ID, Audit Logs Client Secret, and select the Region recorded earlier.
14. Click Add SAP IAS Account.

Check the installation checklist and platform monitoring status in the SAP IAS Dashboard. The guide does not say where the FortiCASB Add Cloud App entry is reached; presumably Overview > Dashboard > Add New (not stated on these pages). Tenant ID is recorded but no FortiCASB field for it is named (not found in sources). [src: forticasb-admin-guide-24-4-b, p.229-233]

## Update SAP IAS account
The procedure repeats the SAP-side steps 1-10 above (a new System administrator, secret, and audit log credentials), then on the FortiCASB Update SAP IAS Account page: click Next Step; enter System Client ID, System Client Secret, Audit Logs Client ID, Audit Logs Client Secret and select the Region. [src: forticasb-admin-guide-24-4-b, p.234-238]
14. Click Update SAP IAS Account to finish. Check the installation checklist and platform monitoring status in the SAP IAS Dashboard.

Gotchas: secrets are shown only once; secret expiration duration is chosen at creation, so rotate by running the update procedure.

## Related
- [sap-success-factors.md](sap-success-factors.md)
- [index.md](index.md)
- [../polling-intervals.md](../polling-intervals.md)
