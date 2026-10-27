---
title: Onboarding Google Workspace
summary: OAuth consent screen, P12 service account, Drive API and domain-wide delegation, audit logs, and FortiCASB add/update steps for Google Workspace in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Google Workspace

FortiCASB authenticates to Google Workspace using OAuth2.0 credentials and the Google Workspace API to monitor user activities and scan data stored in Google Drive. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.157]

## Prerequisites
- Edition: **Business** or **Enterprise** (API enabled by default). Accounts with a basic license cannot use FortiCASB.
- The user account installed in FortiCASB must be a **Super Administrator**. The guide points to "Google Workspace connection errors" (p.556, outside this range) for checking this.
- Existing or new account; wait at least 24 hours for a new account.

Setup order: Configure OAuth Consent Screen; Create Google Service Account; Enable Google Drive API and Authorize Client ID; Enable activity and alert monitoring; Add Google Workspace Account. [src: forticasb-admin-guide-24-4-b, p.157-158]

## 1. Configure OAuth consent screen
Purpose: enable Domain-Wide Delegation when the service account is created, so the Google Drive API OAuth scope can be authorized for the service account. Skip if already configured for the project.
1. Go to Google Cloud Platform Console, log in with the Workspace account.
2. Project drop-down > **Select a project** or **New Project**.
3. Navigation menu > **APIs & Services > OAuth consent screen**.
4. Choose user type **Internal**, click **CREATE**.
5. On the OAuth Consent Screen page: (a) name the app and choose the managing user; (b) leave **App domain** blank; (c) **+ADD DOMAIN** with the Workspace domain (guide example: `security_admin@microsoft.com` gives `microsoft.com`); (d) enter **Developer contact information** e-mail; (e) **SAVE AND CONTINUE**.
6. On Scopes selection, **SAVE AND CONTINUE** (no scopes added here, unlike the Google Cloud Storage page).
7. Confirm Summary; **BACK TO DASHBOARD**.

[src: forticasb-admin-guide-24-4-b, p.158-161]

## 2. Create Google service account
Required to add the account. Must be created in the project that has the OAuth Consent Screen. Without a service account FortiCASB can still be used, but file-related features such as Discovery will not work.
1. GCP Console, project selected: Navigation Menu > **IAM & Admin > Service accounts**.
2. **+Create service account**, enter **Service account name**, **CREATE AND CONTINUE**; skip optional steps; **Done**.
3. Open the service account Details; record the **Service Account ID (Email)**.
4. Expand **Advanced settings**; record the **Client ID**.
5. **KEYS** tab > **ADD KEY** > **+Create new Key** > key format **P12** > **CREATE**; the P12 private key downloads automatically.

Keep the Service Account ID and P12 private key for FortiCASB. [src: forticasb-admin-guide-24-4-b, p.163-165]

## 3. Enable Google Drive API and authorize Client ID
1. In GCP Console select the project where the service account was created.
2. **APIs & Services > Enabled APIs & services**.
3. **+ENABLE APIS AND SERVICES**.
4. Search for **Google Drive API** and enable it.
5. Go to Google Workspace Admin Console, log in with the same account.
6. **Security > Access and data control > API controls**.
7. **MANAGE DOMAIN WIDE DELEGATION**.
8. **Add new**; enter the Client ID from the service account.
9. In **OAuth scope** enter `https://www.googleapis.com/auth/drive` and click **AUTHORIZE**.

[src: forticasb-admin-guide-24-4-b, p.166-168]

## 4. Enable activity and alert monitoring
1. In GCP Console select the same project as the service account.
2. Navigation Menu > **IAM & Admin > Audit Logs**.
3. Search for "Google Cloud Storage" in the resource list (as written in the guide).
4. Enable all log types: **Admin Read**, **Data Read**, **Data Write**.
5. **SAVE**.

[src: forticasb-admin-guide-24-4-b, p.169]

## 5. Add the account in FortiCASB
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > **Google Workspace** > **Add Selected Cloud App**.
3. Review the key configurations summary; **Next**.
4. Enter the **Service Account ID (Email)** (ends in `.gserviceaccount.com`; shown in Service account details) and upload the **Private Key (P12 File)**.
5. Click **Add Google Workspace Account**; you are sent to Google for authentication. Use the same Workspace account; if you have a custom Google domain, enter it.
6. Log in; Google prompts Allow or Deny.
7. Click **Allow**. You are redirected to the FortiCASB dashboard; check installation checklist and platform monitoring status in the Google Workspace dashboard.

[src: forticasb-admin-guide-24-4-b, p.170-173]

## Update Google Workspace account
Complete steps 1-4 with the same Workspace account first. Then:
1. Log into FortiCASB; **Overview > Dashboard**.
2. Google Workspace menu > **Update Cloud Account**.
3. Review key configurations summary; **Next**.
4. Enter **Service Account ID (Email)** and upload the **Private Key (P12 File)**.
5. Click **Update Google Workspace Account**; authenticate with the same Workspace account (custom domain if applicable).
6. Log in; **Allow**.
7. Redirected to the dashboard; check installation checklist and platform monitoring status.

[src: forticasb-admin-guide-24-4-b, p.174-177]

## Gotchas
- P12 key (not JSON) is used for Workspace; the Cloud Storage onboarding uses JSON.
- Delegated scope here is only `https://www.googleapis.com/auth/drive`; Cloud Storage onboarding delegates `admin.directory.user` and `admin.reports.audit.readonly`.
- The audit-log step refers to the "Google Cloud Storage" resource even in this Workspace procedure.

## Related
- [Onboarding index](index.md)
- [Google Cloud Storage](google-cloud-storage.md)
- [Company and first-time setup](../company-and-first-time-setup.md)
