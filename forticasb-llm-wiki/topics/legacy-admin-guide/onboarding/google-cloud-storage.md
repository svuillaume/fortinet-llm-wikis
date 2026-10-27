---
title: Onboarding Google Cloud Storage
summary: Service account, domain-wide delegation, org-level roles, API enablement, audit logs, and FortiCASB add/update steps for Google Cloud Storage in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Google Cloud Storage

FortiCASB pulls data from Google Cloud Storage via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and conducts DLP Data Analysis for files in Cloud Storage. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.134]

## Prerequisites
- A Google Workspace account, a Service Account, and the JSON private key associated with the service account.
- The service account must have **Google Workspace Domain-wide Delegation** enabled and **Project Owner / Organization Administrator** roles for monitoring.
- The Google Workspace account used to connect must have the **Super Admin** role. A new account needs at least 24 hours before granting access to FortiCASB.

Step order: Configure Google Workspace Account; Configure OAuth Consent Screen; Create Service Account; Grant Service Account API Access; Grant Service Account Owner and Organization Administrator Role; Enable required APIs; Enable activity and alert monitoring; Add Google Cloud Storage Account. [src: forticasb-admin-guide-24-4-b, p.134]

## 1. Configure Google Workspace account (verify Super Admin)
1. Log into Google Admin.
2. Navigation menu > **Directory > Users**.
3. Click the user account.
4. Scroll to **Admin roles and privileges** and expand.
5. In **Roles**, confirm **Super Admin** is assigned; if not, assign it with the toggle.

[src: forticasb-admin-guide-24-4-b, p.135]

## 2. Configure OAuth consent screen
Needed so Domain-Wide Delegation can be enabled when the service account is created. Skip if already configured for the project.
1. Go to Google Cloud Platform and log in with the Workspace account.
2. Project drop-down > **Select a project** (existing project to monitor) or **New Project**.
3. Search for and open **OAuth Consent Screen**.
4. Choose user type **Internal**, click **CREATE**.
5. Step 1 (OAuth Consent Screen): (a) name the app and choose the managing user; (b) leave **App domain** blank (internal use); (c) **+ADD DOMAIN** and enter the domain of the GCP account (e.g. `forticasb.com`); (d) enter **Developer contact information** e-mail; (e) **SAVE AND CONTINUE**.
6. Step 2 (Scopes): (a) **ADD OR REMOVE SCOPES**; (b) select all scopes of the app and click update; (c) review, **SAVE AND CONTINUE**; (d) confirm Summary, **BACK TO DASHBOARD**.

[src: forticasb-admin-guide-24-4-b, p.136-141]

## 3. Create service account
Existing or new; it must be created in the project that has the OAuth Consent Screen.
1. In GCP portal with the project selected: Navigation Menu > **IAM & Admin > Service accounts**.
2. **+Create service account**, enter a **Service account name**, **CREATE AND CONTINUE**; skip optional steps; **Done**.
3. Click the service account to open Details; record the **Service Account ID (Email)**.
4. Expand **Advanced settings**; record the **Client ID** (used in step 4).
5. **KEYS** tab > **ADD KEY** > **Create new Key** > key format **JSON** > **CREATE**; the JSON private key downloads automatically.

Keep the Service Account ID and JSON key for FortiCASB. [src: forticasb-admin-guide-24-4-b, p.142-144]

## 4. Grant service account API access (Domain-wide Delegation)
A Google Workspace Super Admin performs this one-time configuration.
1. Log into Google Admin with the same Google account.
2. **Security > Access and data control > API Controls**; scroll down; **Manage Domain wide Delegation**.
3. **Add new**.
4. **Client ID**: enter the Client ID saved earlier (a string of numbers).
5. **OAuth scopes**: enter

```
https://www.googleapis.com/auth/admin.directory.user,https://www.googleapis.com/auth/admin.reports.audit.readonly
```

[src: forticasb-admin-guide-24-4-b, p.145-146]

## 5. Grant organization-level roles to the service account
FortiCASB requires one of the following role sets at organization level (monitoring across all projects under the organization):
1. Organization Administrator and Owner roles; or
2. Basic > Viewer, Tag Viewer, and Log View Accessor.

Steps:
1. In GCP portal select the organization the project is under.
2. Navigation Menu > **IAM & admin > IAM**.
3. **+Grant Access**.
4. **Add Principals > New principals**: enter the service account ID.
5. **Assign roles**, choose one option:
   - Option 1: **Select a role** > **Project > Owner** (or Viewer); **+ ADD ANOTHER ROLE** > **Resource Manager > Organization Administrator**.
   - Option 2: **Select a role** > **Resource Manager > Tag Viewer**; **+ ADD ANOTHER ROLE** > **Basic > Viewer**; **+ ADD ANOTHER ROLE** > **Logging > Log View Accessor**.
6. **SAVE**.

[src: forticasb-admin-guide-24-4-b, p.147-149]

## 6. Enable required APIs (on all monitored projects)
Required APIs: Cloud Resource Manager API; App Engine Admin API; Cloud Key Management Service (KMS) API; Compute Engine API; Cloud SQL; Google Cloud Storage JSON API; Cloud Storage; Cloud SQL Admin API; Stackdriver API; Admin SDK; Identity and Access Management (IAM) API.

Check: select the project; Navigation Menu > **APIs & Services > Enable APIs & services**; confirm each is listed. To enable missing ones: select the project > **APIs & Services** > **Activate Cloud Console** (upper right) > paste:

```
gcloud services enable \
  cloudresourcemanager.googleapis.com \
  appengine.googleapis.com \
  cloudkms.googleapis.com \
  compute.googleapis.com \
  sql-component.googleapis.com \
  storage-api.googleapis.com \
  storage.googleapis.com \
  sqladmin.googleapis.com \
  stackdriver.googleapis.com \
  admin.googleapis.com \
  iam.googleapis.com
```

Repeat for other projects in the same organization. [src: forticasb-admin-guide-24-4-b, p.149-151]

## 7. Enable activity and alert monitoring (audit logs)
1. In GCP console select the project where the service account was created, then the project to be monitored.
2. Navigation Menu > **IAM & Admin > Audit Logs**.
3. Search for "Google Cloud Storage" in the resource list.
4. Enable all log types: **Admin Read**, **Data Read**, **Data Write**.
5. **SAVE**.

[src: forticasb-admin-guide-24-4-b, p.151-152]

## 8. Add the account in FortiCASB
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > **Google Cloud Storage** > **Add Selected Cloud App**.
3. Review the key configurations list; **Next**.
4. **User Email**: the Google Workspace account used to create the service account.
5. **Service Account ID**: must end in `.gserviceaccount.com`.
6. **Upload Service Account Private Key**: **Choose File**, upload the JSON key.
7. Click **Add Google Cloud Storage Account**.

[src: forticasb-admin-guide-24-4-b, p.152-155]

## Update Google Cloud Storage account
Complete configuration steps 1-7 using the same Google Workspace account. Then:
1. Log into FortiCASB; **Overview > Dashboard**.
2. Google Cloud Storage menu > **Update Cloud Account**.
3. Review key configurations list; **Next**.
4. Enter **User Email**, **Service Account ID** (`.gserviceaccount.com`), and upload the JSON key via **Choose File**.
5. Click **Update Google Cloud Storage Account**. Allow 15 minutes and check account status.

[src: forticasb-admin-guide-24-4-b, p.155-157; p.134]

## Gotchas
- OAuth consent screen user type is Internal.
- Organization-level roles are required to monitor all projects; APIs must be enabled per project.
- Key format here is JSON; Google Workspace onboarding uses a P12 key instead (see [Google Workspace](google-workspace.md)).

## Related
- [Onboarding index](index.md)
- [Google Workspace](google-workspace.md)
- [Polling intervals](../polling-intervals.md)
