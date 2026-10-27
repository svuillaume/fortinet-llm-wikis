---
title: Yammer Integration
summary: Prerequisites and steps to enforce Office 365 identity in Yammer and verify Yammer licenses so FortiCASB can monitor Yammer files.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Yammer Integration

The integration lets FortiCASB monitor and inspect files posted on Yammer by users in the organization. Organization users who are also Yammer users show as "Yammer Licensed". Under **Office 365 > Users**, Yammer users have the Yammer icon under Property. Files uploaded by licensed users appear in **Office 365 > Documents**, distinguished by an icon in the File Name column; clicking a name shows creator, created date, last modified date, file path, etc. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.463]

## Prerequisites

Enforcing Office 365 identity in Yammer may lock out Yammer users who lack an Office 365 account. Before the change, notify users and:

- Ensure all Yammer users have an Azure AD account. Compare Yammer users with Office 365 users; in Yammer use **Settings > Edit Network Settings > Export Users**.
- Help users without an Azure AD account get one before enforcing.

You must be an Office 365 global administrator synchronized to Yammer as a verified administrator. Verify in Yammer under **Settings > Edit Network Settings > Admins** that your Yammer admin is synchronized to the Office 365 global administrator account. [src: forticasb-admin-guide-24-4-b, p.464]

## Enforce Office 365 identity in Yammer

1. Log into Yammer with the Yammer admin account.
2. New Yammer: **Settings > Edit Network Admin Settings** (upper right). Old Yammer: **Settings > Network Admin** (upper left).
3. Click **Security Settings** under Content and Security.
4. Scroll to **Office 365 Identity Enforcement** and check **Enforce Office 365 identity**.
5. A confirmation asks for the enforcement level.
6. Select **Committed Enforcement** and press OK. This cannot be undone: users can no longer log in with Yammer-only accounts; only users with Azure AD accounts can log in.
7. Click **Save**.
8. After at least 15 minutes, return to Security Settings and check status under **Office 365 Connected Yammer Groups**; it should be enabled.

[src: forticasb-admin-guide-24-4-b, p.465-466]

## Yammer license verification

Requires Office 365 global administrator.

1. Log into https://www.office.com/ as global administrator.
2. Click **Admin** to open the Microsoft 365 admin center.
3. Expand **Users** and select **Active Users**.
4. Click a licensed user to open the profile.
5. Select the **Licenses and Apps** tab and expand **Apps**.
6. Scroll down; **Yammer Enterprise** must be checked for the user to integrate with FortiCASB.
7. Repeat steps 4-6 for all Yammer users.

[src: forticasb-admin-guide-24-4-b, p.467-469]

## Yammer file path

After enforcement, files uploaded to Yammer are relocated to `Shared Document/Apps/Yammer/` in the user's SharePoint. FortiCASB retrieves file metadata through this path, so it must not be changed. This is the Yammer file path shown in FortiCASB. [src: forticasb-admin-guide-24-4-b, p.469-470]

## Related

- [Activity](activity.md)
- [Files](files.md)
- [Users and administrative privileges](users-and-admin-privileges.md)
- [Onboarding](../onboarding/index.md)
