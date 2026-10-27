---
title: Business Units
summary: Adding, configuring, assigning users to and switching between FortiCASB business units, including creating FortiCloud business users.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Business Units

## Add a business unit
1. Log into FortiCASB with your primary FortiCloud account.
2. Click **Company** (top right).
3. Click **+Add Business Unit** under Company management.
4. Enter the Business Unit ID and a name, then click **Add BU**.

Repeat for more business units. [src: forticasb-admin-guide-24-4-b, p.26-27]

## Create a business user (FortiCloud)
Business users must be created on FortiCloud, and only the FortiCloud primary account user can create them. They then appear in User Management in FortiCASB.
1. Log into FortiCloud (https://support.fortinet.com), or from FortiCASB use the account drop-down and select **My Account**.
2. Click **Mange User** (as printed) on the left; a user list is shown.
3. Click the add user button on the right.
4. Fill in User Name, E-mail, and Telephone.
5. Select **Full Access** (full permissions incl. create/access/assign companies and business units) or **Limited Access** (basic access), then Save.
6. For Limited Access, click **Add More Products** to select a license.
7. Click **Save**.

Then assign users to business units. [src: forticasb-admin-guide-24-4-b, p.27-29]

## Business Unit Settings
Accessible via Business Unit Setting in the upper right of the Overview/Dashboard page, or in the Company page under each Business Unit.
- **Business Unit ID**: identifies the business unit.
- **Business Unit Name**: should be unique.
- **Time Zone**: sets cloud account activity time stamps; also used in alert notification emails for all activities.
- **Report Settings**: Cover and Header Image for C-Level, Compliance, Alert, Activity, and Shadow IT reports generated through the business unit.

[src: forticasb-admin-guide-24-4-b, p.30-31]

## Assign users to a business unit
Newly created FortiCloud users appear in User Management; log out and back in if they are not visible.
1. Log in with the primary FortiCloud account.
2. On the Dashboard, click **Company** (top right).
3. Scroll to **User Management**; check the business unit box to grant access, uncheck to remove.
4. Click **Save**.

[src: forticasb-admin-guide-24-4-b, p.32]

## Switch between business units
Only business users created by the FortiCloud primary account can access FortiCASB.
1. At the sign-in page, sign in with your business user account.
2. Select a FortiCASB user account (if applicable).
3. Select your business unit; the dashboard opens.
4. To switch, click **Company** (top right).
5. Find the business unit and click **Go to this BU**.

If the account has not been assigned to a business unit an error appears; ask the primary FortiCloud administrator to add you. [src: forticasb-admin-guide-24-4-b, p.32-33]

## Related
- [Company and first-time setup](company-and-first-time-setup.md)
- [User management and permissions](user-management-and-permissions.md)
- [Entra ID administrative units](entra-id-administrative-units.md)
