---
title: User Management and Permission Chart
summary: User types, permission chart, and Local IAM and OU IAM user creation and login for FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# User Management and Permission Chart

Two classes of users:
- **FortiCloud Full Access Users and IAM Admin Users**: full permission in Company and Business Unit management.
- **FortiCloud Limited Access Users and IAM Read/Write Users**: limited permissions.

[src: forticasb-admin-guide-24-4-b, p.48]

## Permission chart
The source table is garbled in extraction; reconstructed below (column order as printed).

| User type | Permission type | Need to assign BU first | Manage Company page | Add BU in Company page | Modify Business Units | Add Applications in Business Unit page |
|---|---|---|---|---|---|---|
| IAM user | Admin | No (has access to all BU) | Yes | Yes | Yes | Yes |
| IAM user | Read/Write | Yes | No | No | No | Yes |
| Sub Account User | Limited | Yes | No | No | No | Yes |
| Sub Account User | Full | No (has access to all BU) | Yes | Yes | Yes | Yes |

[src: forticasb-admin-guide-24-4-b, p.48]

## Local IAM user
Created and delegated by the FortiCloud master administrative user; access is limited to the assigned permission profile.

### Create
1. Log into FortiCloud Organization as the master user.
2. **Services** > **IAM**.
3. From the master user drop-down (upper right), note the **Account ID** (used for IAM login).
4. **Users** > **Add New** > **IAM**.
5. Enter IAM user information, **Next**.
6. Basic Info > Select a Type: **Local**.
7. Permission Scope: keep **My Assets**.
8. Select a Permission Profile; access comes through this profile.
9. Permission Details shows the entitled access type.
10. **Next**.
11. On Confirmation, review and **Confirm**.
12. Enter the verification code from the verification email.

### First login
1. FortiCASB login page, **IAM LOGIN** tab.
2. Enter master Account ID, IAM username, password; **Log In**.
3. Enter the emailed security code; **Go**.
4. User lands on the dashboard per the permission profile.

[src: forticasb-admin-guide-24-4-b, p.48-52]

## OU IAM user
An IAM user with Organization scope and a permission profile defined by the master user. Unlike a Local IAM user, it can access other FortiCASB profiles in the same organization scope, switching via the upper-right account button. [src: forticasb-admin-guide-24-4-b, p.52]

### Organization unit configuration
1. Create a FortiCloud Root or Sub Organization Unit (OU) with a master user that has a FortiCASB license.
2. (Optional) Create/use a registered FortiCloud user with a FortiCASB license.
3. (Optional) Add that user to the OU: send an invitation token from the organization; the user joins the organization.

(Links to FortiCloud docs: Creating an organization, Creating a FortiCloud account, Registering assets, Invitations, Joining an organization; URLs not in text.) [src: forticasb-admin-guide-24-4-b, p.53]

### Create OU IAM user
1-5. As for Local IAM user (Services > IAM, note Account ID, Users > Add New > IAM, enter info, Next).
6. Basic Info > Select a Type: **Organization**.
7. Permission Scope: choose an organization unit or account.
8. Select a Permission Profile. Choose one with **Admin** Access Type for FortiCASB; only OU IAM users with Admin access can switch to other organization profiles.
9. **Next**.
10. Review and **Confirm**.
11. Enter the verification code from email.

[src: forticasb-admin-guide-24-4-b, p.54-55]

### First login
1. FortiCASB login page, **IAM LOGIN** tab.
2. Enter the organization Account ID, IAM username, password; **Log In**.
3. Enter the emailed security code; **Go**.
4. On the 'Welcome Back' page select an OU or Sub OU account.
5. The user reaches that FortiCASB profile's default dashboard.

[src: forticasb-admin-guide-24-4-b, p.56-57]

## Related
- [Business units](business-units.md)
- [Company and first-time setup](company-and-first-time-setup.md)
