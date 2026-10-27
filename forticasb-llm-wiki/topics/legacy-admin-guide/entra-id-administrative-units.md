---
title: Microsoft Entra ID Administrative Units Integration
summary: Adding Entra ID administrative units to FortiCASB, assigning them to business units, applying them to cloud accounts and syncing members.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Microsoft Entra ID Administrative Units Integration

Entra ID (formerly Azure AD) Administrative Units (AU) group users of interest under one management scope. Instead of monitoring all cloud account users, define the users or groups to monitor. Access via **Company** (top right of the Main page). AUs support both Users and Groups (e.g. group "finance_department" within AU "david_AU"). New in 24.4.b: group-level integration ([Release notes](release-notes.md)).

If the Azure account on FortiCASB was onboarded prior to 2024 and this is the first use of AU Management, first update the Azure Storage account (guide p.83; not in this page set). [src: forticasb-admin-guide-24-4-b, p.33]

## Benefits of AU groups
1. Data Security Policy accepts an AU Group as a Match Criteria; only users in the group are scanned (guide p.364).
2. Compliance, Alert, and Activity Reports support AU Group selection; only group users are considered (guide p.296).

[src: forticasb-admin-guide-24-4-b, p.34]

## Workflow
1. Create the AU and add users/groups in Microsoft Entra ID (Microsoft docs: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-manage).
2. Add the AU to FortiCASB.
3. Add the AU to a Business Unit.
4. Apply the AU to a cloud account.

[src: forticasb-admin-guide-24-4-b, p.34]

## Supported cloud accounts
Salesforce, Office365, Box, Dropbox, Google, Jira, Webex, GitHub, Zoom, ServiceNow, Egnyte, Confluence, SAP IAS. [src: forticasb-admin-guide-24-4-b, p.35]

## Add an AU to FortiCASB
Adding an AU adds all its users and groups simultaneously. It must be added to FortiCASB before it can be added to a business unit.
1. Log in, click **Company**.
2. Scroll to **Microsoft Entra ID AU (Administrative Unit) Management**, click **+ Add New**.
3. Click **Login @Microsoft Entra ID** and sign in with the Azure admin account.
4. After redirect, select the AU(s).
5. Click **Add Selected AUs**.
6. Click **Done** and wait a few minutes for users to sync.

[src: forticasb-admin-guide-24-4-b, p.35-37]

## Add an AU to a Business Unit
1. Obtain the BU ID: switch to the target business unit and note the Business Unit ID on the Dashboard.
2. In Company Management > Entra ID AU Management, select an AU, click **Add To BU**, choose the BU ID in the **Select BU** drop-down, click **Save Changes**.
3. Verify: on the Dashboard click **Switch Business Unit**, click **Go to this BU** for the target, then click **See Added AU** in the Dashboard; the AU should be listed.

[src: forticasb-admin-guide-24-4-b, p.37-40]

## Apply AUs to a cloud account
Prerequisite: AU added to the business unit; verify with **See Added AU**.

**Method 1: Add Cloud Account**
1. Dashboard > **Switch Business Unit**; in Company go to the BU with the AU.
2. Verify via **See Added AU**.
3. In Business Unit Overview click **Add New cloud account**.
4. Select the supported application (e.g. Salesforce), click **Add Selected Cloud App**.
5. Check **Only monitor users that are found in Microsoft Entra ID AU**.
6. Complete the remaining Add Cloud Account steps.

**Method 2: Update Cloud Account**
1-3. As above.
4. In Business Unit Overview select the cloud application, click the setting button, choose **Update Cloud Account**.
5. Check **Only monitor users that are found in Microsoft Entra ID AU**.
6. Complete the Update Cloud Account steps.

[src: forticasb-admin-guide-24-4-b, p.40-43]

## Synchronize AU members
After AU users/groups change in Entra ID, sync manually:
- **Per AU**: Company > Entra ID AU Management, select AUs and click **Sync Members in Selected**.
- **All AUs in a business unit**: Overview > Dashboard > **See Added AU** > **Sync Users In All AU**.

[src: forticasb-admin-guide-24-4-b, p.43-44]

## Related
- [Business units](business-units.md)
- [Company and first-time setup](company-and-first-time-setup.md)
- [Release notes](release-notes.md)
