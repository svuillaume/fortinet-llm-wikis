---
title: Cloud application onboarding index
summary: Index of per-application onboarding pages for legacy FortiCASB 24.4.b with auth method and key prerequisites.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Cloud application onboarding index

This section covers the LEGACY FortiCASB platform (Admin Guide 24.4.b). Administrators and users can onboard cloud applications to a business unit; once added, all users in the business unit can view the application. In FortiCASB the generic path is **Overview > Dashboard > Add New > (app) > Add Selected Cloud App**; updates use the account menu > **Update Cloud Account**. The guide states each connector is API-based (RESTful API) with OAuth2.0; actual credential mechanisms differ per app as shown below. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.58]

| App | Auth method (as configured) | Key prerequisites | Page |
|---|---|---|---|
| AWS S3 | IAM role with FortiCASB-generated External ID; Role ARN entered | AWS Administrator User; regional STS activated; custom IAM policy; CloudTrail multi-region trail (Mgmt + S3 data events) | [aws-s3.md](aws-s3.md) |
| Azure Storage | Subscription ID + Azure role assignments | Global Administrator (or Cloud Application Administrator + Global Reader); Reader and Storage Blob Data Reader roles; storage account with blob logging; Pay-As-You-Go minimum | [azure-storage.md](azure-storage.md) |
| Box | OAuth (Grant Access @Box) | Business/Enterprise/Developer edition; read/write all files, manage users/groups/enterprise properties; Admin User for login IP tracking | [box.md](box.md) |
| Citrix ShareFile | OAuth (Grant Access@ShareFile) | Admin user with User Access "Select All"; ShareFile subdomain | [citrix-sharefile.md](citrix-sharefile.md) |
| Confluence | Atlassian OAuth 2.0 (3LO) app: Client ID/Secret; OAuth grant; webhook | Standard/Premium/Enterprise plan; Organization and Site Admin; Webhook Manager for Confluence Cloud | [confluence.md](confluence.md) |
| Dropbox Business | OAuth (Grant Access @Dropbox) | Essentials/Business/Business Plus; Team Admin | [dropbox-business.md](dropbox-business.md) |
| Egnyte | OAuth (Grant Access@Egnyte) | Administrator role only; Egnyte domain | [egnyte.md](egnyte.md) |
| Facebook Workplace | Custom integration App ID, App Secret, Access Token | Advanced/Enterprise plan; System Administrator | [facebook-workplace.md](facebook-workplace.md) |
| GitHub | OAuth (Grant Access@GitHub) | Free/Team/Enterprise organization (no personal accounts); Organization Owner | [github.md](github.md) |
| Google Cloud Storage | Service account JSON key + domain-wide delegation | Workspace Super Admin; OAuth consent screen (Internal); org-level roles; 11 APIs enabled; audit logs | [google-cloud-storage.md](google-cloud-storage.md) |
| Google Workspace | Service account P12 key + domain-wide delegation, then Google OAuth Allow | Business/Enterprise edition; Super Admin; Drive API; delegated scope `.../auth/drive` | [google-workspace.md](google-workspace.md) |
| Jira | Atlassian OAuth 2.0 (3LO) app: Client ID/Secret; OAuth grant; system webhook | Any Jira Cloud plan; Site Admin; Browse Projects permission (company-managed projects) | [jira.md](jira.md) |
| Office 365 (before 24.2.a) | User-account OAuth consent | Audit log activation; SharePoint site admin; Office 365 licences (see page) | [office-365-before-24-2-a.md](office-365-before-24-2-a.md) |
| Office 365 (after 24.2.a) | Service-account style: Microsoft Entra ID app registration (client ID, tenant ID, client secret) | Microsoft Graph and Office 365 Management API application permissions; audit log activation | [office-365-after-24-2-a.md](office-365-after-24-2-a.md) |
| Salesforce | OAuth | Edition and permission prerequisites (see page) | [salesforce.md](salesforce.md) |
| SAP IAS | System administrator with client secrets and audit-log credentials | SAP IAS administrator; tenant details (see page) | [sap-ias.md](sap-ias.md) |
| SAP SuccessFactors | OAuth2 client application with X.509 certificate | Manage Integration Tools permissions | [sap-success-factors.md](sap-success-factors.md) |
| ServiceNow | OAuth API endpoint (application registry) on a developer instance | ServiceNow developer instance | [servicenow.md](servicenow.md) |
| Webex Teams | OAuth grant | Full Administrator in Cisco Webex Control Hub | [webex-teams.md](webex-teams.md) |
| Zendesk | OAuth client with FortiCASB regional redirect URLs | Zendesk admin (see page) | [zendesk.md](zendesk.md) |
| Zoom | OAuth app (account-level) with event subscription and scopes | Zoom role settings (see page) | [zoom.md](zoom.md) |

Rows for Office 365 through Zoom are summarized from each page's own summary line; read the page for exact roles, scopes and permissions.

Common notes
- New accounts: Box, Azure, Google Workspace and Google Cloud Storage pages state to wait at least 24 hours before granting access to FortiCASB.
- Several apps state the add/update process may take 15 minutes; check **Overview > Dashboard**.
- For apps with OAuth logins (ShareFile, Egnyte), the user added in FortiCASB must be the same user logged into the app.

## Related
- [Polling intervals](../polling-intervals.md)
- [Company and first-time setup](../company-and-first-time-setup.md)
- [User management and permissions](../user-management-and-permissions.md)
- [Naming and rebrand](../../product/naming-and-rebrand.md)
