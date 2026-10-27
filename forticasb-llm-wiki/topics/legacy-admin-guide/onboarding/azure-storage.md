---
title: Onboarding Azure Storage
summary: Azure subscription, Reader and Storage Blob Data Reader roles, blob logging, and FortiCASB add/update steps for Azure Storage in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Azure Storage

FortiCASB pulls data from Azure Storage via RESTful API (portal access "with OAuth2.0 authentication" per guide), monitors user activities and provides DLP Data Analysis for files on Azure Storage. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.73]

## Prerequisites
- Existing or new Azure AD account. A new account needs at least 24 hours to take effect before granting access to FortiCASB.
- The user account used on FortiCASB must have **Global Administrator** role, or **Cloud Application Administrator + Global Reader** roles.
- Set up the Azure AD Privileged Identity Management application (guide links Microsoft's pim-configure doc).
- All Azure AD license types supported, but FortiCASB integrates only features available to the license (example: free Azure AD has no sign-in activity report, so no sign-in activities).
- Minimum subscription: "Pay-As-You-Go".

Order: Setup Azure Subscription; Add Reader role; (optional) Reader roles for multiple subscriptions; Collect Subscription and Tenant IDs; Setup Blob Storage; Enable Blob Log Monitoring; Setup Storage Blob Data Reader; Add Azure Storage Account. [src: forticasb-admin-guide-24-4-b, p.73-74]

## 1. Set up Azure subscription
1. Log into the Azure Portal. 2. Search **Subscriptions**. 3. Click **+Add**. 4. Select the subscription and complete billing. Minimum "Pay-As-You-Go". [src: forticasb-admin-guide-24-4-b, p.74]

## 2. Add Reader role to the subscription
Gives FortiCASB read access to resources under the subscription.
1. **Subscriptions**; click the subscription to be added.
2. **Access control (IAM)**.
3. **+Add** > **Add role assignment**.
4. **Select a role**: **Reader**.
5. Leave **Assign access to** as User, group, or service principal.
6. In **Select**, choose the member (user account) - must hold Global Administrator, or Cloud Application Administrator + Global Reader.
7. **Save**.

[src: forticasb-admin-guide-24-4-b, p.75-76]

## 3. Reader roles on multiple subscriptions (optional)
To add multiple subscriptions with one user account. If the user already has Global Administrator, do only steps 6-9.
1. Log in to Azure portal as the master account user.
2. Search **users**.
3. Click the user to be used when adding subscriptions to FortiCASB.
4. Profile navigation > **Assigned roles**.
5. **+Add assignments**: add **Global reader** and **Global Administrator** (Global Administrator is removed later).
6. Log out; log in as the user who received the roles.
7. Search **Azure Active Directory**.
8. **Properties**.
9. Under **Access management for Azure resources** click **Yes**, then **Save** (lets the user manage access to all subscriptions under the account).
10. Log out; log back in as the master account.
11. Repeat steps 2-4 and remove the Global administrator role.

Result: all subscriptions under the user have Reader role and can be added at once. [src: forticasb-admin-guide-24-4-b, p.76-77]

## 4. Collect Subscription ID and Tenant ID
- Subscription ID: portal > **Subscriptions**, record the ID.
- Tenant ID: **Azure Active Directory** > **MANAGE > Properties** > Directory properties > Tenant ID.

[src: forticasb-admin-guide-24-4-b, p.78-79]

## 5. Set up Blob Storage
A storage account with blob log monitoring enabled is required before adding to FortiCASB.
1. Portal > **storage accounts**.
2. **+Create**.
3. Basics > Project details: select the subscription linked to your subscription ID.
4. **Resource group**: choose or create.
5. Instance details > **Storage account name**: enter a name.
6. **Review + create**; after validation click **Create**.

[src: forticasb-admin-guide-24-4-b, p.79-80]

## 6. Enable Blob log monitoring
1. Select the storage account.
2. In the middle pane scroll to **Monitoring (classic)** > **Diagnostic settings (classic)**.
3. Turn **On** diagnostic logs. In the **Blob properties** tab, under **Logging**, select **Read/Write/Delete**.
4. **Save**.

[src: forticasb-admin-guide-24-4-b, p.80-81]

## 7. Set up Storage Blob Data Reader
Required for FortiCASB DLP Data Analysis and virus scan to read data in the storage blob account and for integrating Azure cloud traffic.
1. Portal > **Subscriptions**; select your subscription.
2. **Access Control (IAM)** > **+Add** > Add role assignment.
3. **Role**: **Storage Blob Data Reader**.
4. **Assign access to**: leave User, group, or service principal.
5. **Select**: the Azure AD user's name or e-mail.
6. **Save**.

[src: forticasb-admin-guide-24-4-b, p.81-82]

## 8. Add the account in FortiCASB
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > **Azure Storage** > **Add Selected Cloud App**.
3. Review the key configurations list; **Next**.
4. Enter **Subscription ID**.
5. Click **Add Azure Storage Account**.

[src: forticasb-admin-guide-24-4-b, p.82-83]

## Update Azure Storage account
Complete the same Azure-side configuration (steps 1-7 above), then:
1. **Overview > Dashboard**.
2. Open the Azure Storage account menu > **Update Cloud Account**.
3. Review key configurations list; **Next**.
4. Enter **Subscription ID**.
5. Click **Update Azure Storage Account**.

[src: forticasb-admin-guide-24-4-b, p.83-84]

## Gotchas
- Free Azure AD licenses lack sign-in activity reports.
- Where the Tenant ID is entered in FortiCASB: not found in sources (only Subscription ID is entered in the add/update form).
- Guide uses "Azure Active Directory" naming (pre-Entra).

## Related
- [Onboarding index](index.md)
- [AWS S3](aws-s3.md)
- [Polling intervals](../polling-intervals.md)
- [User management and permissions](../user-management-and-permissions.md)
