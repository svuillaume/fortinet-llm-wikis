# FortiCASB LLM Wiki - index

Compiled 2026-10-26 from the FortiCASB 24.4.b Admin Guide, the FortiCASB-SSPM User Guide and related FortiCASB / FortiCASB-SSPM documents found under the home folder. Start with [Product names and the rebrand](topics/product/naming-and-rebrand.md): "FortiCASB" can mean the Legacy platform (Admin Guide) or the renamed SSPM platform.

Conventions: every claim ends with `[src: <source stub>]`; stubs are in `sources/`. `needs-review` marks pages where sources disagree. See [log.md](log.md).

## Product, naming, licensing and concepts

- [CASB, SSPM, SSDR, SASE and CNAPP: how the categories relate](topics/product/casb-sspm-concepts.md) - Definitions and scope boundaries used in the FortiCASB enablement material, including the SSPM vs CASB vs CSPM comparison.
- [Connector types, integration methods and permission scopes](topics/product/connector-types-and-permissions.md) - Three connector categories (network/EDR/proxy, core SaaS, IdP), their integration methods, outcomes and read/write permission types.
- [FortiSASE entitlements and order examples](topics/product/fortisase-entitlements.md) - How FortiCASB entitlement works with FortiSASE Standard, Advanced and Comprehensive, which capabilities stay in FortiOS/FortiSASE, and the three worked order examples.
- [Inline vs API CASB (FortiGuard CASB dual-mode)](topics/product/inline-vs-api-casb.md) - How inline CASB (FortiGate/FortiSASE) and API CASB (FortiCASB) divide the work, the four API CASB use-case groups, Shadow IT reporting and on-demand reports.
- [FortiCASB Legacy vs FortiCASB-SSPM, and Basic vs SSPM editions](topics/product/legacy-vs-sspm-comparison.md) - Side-by-side of the Legacy 24.4.b platform and the SSPM platform as documented, plus the Basic/SSPM edition capability table.
- [Licensing, SKUs and pricing for FortiCASB / FortiCASB-SSPM](topics/product/licensing-and-skus.md) - SKU families, user bands and list prices from three document generations, with the conflicts between them recorded. *(needs-review)*
- [FortiCASB Legacy lifecycle and migration](topics/product/lifecycle-and-migration.md) - End-of-order notice for legacy SaaS-only SKUs, the Sept 2026 statement that no dates should be communicated yet, and the migration stance. *(needs-review)*
- [Product names and the FortiCASB rebrand](topics/product/naming-and-rebrand.md) - Which product each FortiCASB-related name refers to (Legacy 24.4.b, FortiCASB-SSPM, FortiCASB Basic, FortiCASB new, FortiGuard CASB, Suridata) and how they map.
- [FortiCASB (SSPM platform) overview and use cases](topics/product/overview-and-use-cases.md) - What the FortiCASB-SSPM / FortiCASB platform does, its six use-case areas, data-collection architecture and capability pillars.
- [FortiCASB-SSPM roadmap items and FAQ answers from enablement decks](topics/product/roadmap-and-faq.md) - Roadmap snapshots from the Nov 2025 and early-2026 decks (ETA only), the POC flow, and FAQ answers on licensing basis, deployment, frameworks, GenAI and workflows. *(needs-review)*
- [SaaS OAuth token abuse: Salesloft/Drift to Salesforce attack path](topics/product/saas-oauth-attack-path-example.md) - The attack path used in the enablement decks to illustrate third-party OAuth risk, and the controls FortiCASB-SSPM maps to it.

## FortiCASB-SSPM User Guide (Feb 2026)

- [FortiCASB-SSPM User Guide (Feb 2026) - section index](topics/sspm-user-guide/index.md) - Entry point to the wiki pages compiled from the FortiCASB-SSPM User Guide and its Suridata predecessor.
- [Activities](topics/sspm-user-guide/activities.md) - The Activities page as a near-real-time audit trail across apps, its embedded pre-filtered tabs, and saving filters as risks.
- [Applications page and connected applications](topics/sspm-user-guide/applications.md) - Managed vs unmanaged applications, priority calculation, connection states, status values, and the Overview, Risks, Users and Activities tabs of a connected application.
- [Dashboard, App Store and SaaS Graph](topics/sspm-user-guide/dashboard-and-app-store.md) - Dashboard metrics, App Store connector flow and connection types, External Link delegation, and SaaS Graph behavior in FortiCASB-SSPM.
- [Data protection: PII discovery, file access security and advanced Search](topics/sspm-user-guide/data-protection-and-search.md) - How the platform scans file-based SaaS apps, the Search query builder, saving queries as risks with workflow actions, and four worked Advanced Search recipes.
- [Identities](topics/sspm-user-guide/identities.md) - Identity profiles aggregated from apps, EDR and IdPs; list columns, priority factors, six finding types and the Overview, Risks and 3rd Party Apps tabs.
- [Risks page](topics/sspm-user-guide/risks.md) - Risk lifecycle (active, remediated, accepted), actions (resolve, assign, ticket, history, report, trigger scan) and Jira/ServiceNow ticket synchronization.
- [Settings, roles and integrations](topics/sspm-user-guide/settings-and-rbac.md) - Users and Roles (4 built-in roles, custom roles), Ticketing & Collaboration, SSO providers, API keys, Shared Accounts and General settings.
- [Shadow SaaS applications](topics/sspm-user-guide/shadow-saas.md) - How unmanaged SaaS apps are detected, what the Overview and Users tabs show, business-justification requests and the SentinelOne-only block action.
- [Third-party apps and tokens: inventory, filters, collaboration, revoke access, saved risks](topics/sspm-user-guide/third-party-apps.md) - Inventory criteria, filters, templates for collaboration, status automation, revoke-access procedure and prerequisites, and the Save as Risk method.
- [Workflows (triggers, conditions, actions)](topics/sspm-user-guide/workflows.md) - No-code workflow model, supported triggers/conditions/actions, canvas steps, AND/OR logic, clone behavior and execution log.

## Competitive and market analysis

- [Competitive section index](topics/competitive/index.md) - Entry point for the FortiCASB / FortiCASB-SSPM competitive research pages, with source inventory, evidence flags and the register of cross-document disagreements. *(needs-review)*
- [Capability matrix](topics/competitive/capability-matrix.md) - The capability comparisons and numeric scores that are present in the text extracts of the competitive research, with an explicit note that the 0-5 heatmap grids are missing. *(needs-review)*
- [Fortinet fit and documented gaps](topics/competitive/fortinet-fit-and-gaps.md) - Documented strengths, weaknesses, integration status and UNVERIFIED items for FortiCASB-SSPM according to the competitive research, with the points on which the research documents disagree. *(needs-review)*
- [CASB and SSPM market landscape](topics/competitive/market-landscape.md) - Category definitions, vendor groupings, analyst placement and market-size data for the CASB, SSPM and SSE/SASE market as of August to October 2026. *(needs-review)*
- [Competitive newsletter digest 2026](topics/competitive/newsletter-digest-2026.md) - Dated chronological digest of CASB, SSPM and SSE market events reported in the August to October 2026 competitive research, with evidence flags and publication timeline. *(needs-review)*
- [Pricing benchmarks](topics/competitive/pricing-benchmarks.md) - Price points and licensing structures per vendor from the August to October 2026 competitive research, each with source, date and evidence flag, plus the conflicts between documents. *(needs-review)*
- [Competitor vendor profiles](topics/competitive/vendor-profiles.md) - Per-vendor profiles of CASB and SSPM competitors (architecture, SSPM origin, analyst standing, recent events) with evidence flags and the facts on which the sources disagree. *(needs-review)*
- [FortiCASB-SSPM vs Microsoft Defender for Cloud Apps](topics/competitive/vs-microsoft-defender-for-cloud-apps.md) - Feature-by-feature, licensing and gap comparison of FortiCASB-SSPM and Microsoft Defender for Cloud Apps in Microsoft 365 E5, with the differences between the three October 2026 versions of the comparison. *(needs-review)*

## FortiCASB Legacy Admin Guide 24.4.b - core

- [FortiCASB Legacy Admin Guide 24.4.b - section index](topics/legacy-admin-guide/index.md) - Entry point and chapter map for the pages compiled from the FortiCASB 24.4.b Admin Guide (574 pages, Dec 30 2024).
- [Business Units](topics/legacy-admin-guide/business-units.md) - Adding, configuring, assigning users to and switching between FortiCASB business units, including creating FortiCloud business users.
- [Company Management and First Time Setup](topics/legacy-admin-guide/company-and-first-time-setup.md) - Company management functions, account permission levels and the first-time setup procedure for FortiCASB.
- [Microsoft Entra ID Administrative Units Integration](topics/legacy-admin-guide/entra-id-administrative-units.md) - Adding Entra ID administrative units to FortiCASB, assigning them to business units, applying them to cloud accounts and syncing members.
- [Introduction and Cloud Security Features](topics/legacy-admin-guide/introduction-and-features.md) - Overview of the legacy FortiCASB platform (Admin Guide 24.4.b) and its visibility, data security, threat protection and compliance features.
- [FortiCASB Licensing](topics/legacy-admin-guide/licensing.md) - License types, SKUs, FortiClient ZTNA entitlement and scan-capacity rules for legacy FortiCASB.
- [NAT IP Address and API Credentials](topics/legacy-admin-guide/nat-ip-and-api-credentials.md) - FortiCASB NAT IP addresses per region and how to generate a REST API credential.
- [Cloud Application Polling Intervals](topics/legacy-admin-guide/polling-intervals.md) - API polling intervals per cloud application and the list of webhook-integrated applications.
- [Change Log and What's New (24.4.b)](topics/legacy-admin-guide/release-notes.md) - Document change log history and the FortiCASB 24.4.b release highlights.
- [Native Apps Support and Scan Scope](topics/legacy-admin-guide/supported-apps-and-scan-scope.md) - Which cloud application native apps are monitored and what data is in scope for scanning.
- [User Management and Permission Chart](topics/legacy-admin-guide/user-management-and-permissions.md) - User types, permission chart, and Local IAM and OU IAM user creation and login for FortiCASB.

## Legacy: cloud application onboarding

- [Cloud application onboarding index](topics/legacy-admin-guide/onboarding/index.md) - Index of per-application onboarding pages for legacy FortiCASB 24.4.b with auth method and key prerequisites.
- [Onboarding AWS S3](topics/legacy-admin-guide/onboarding/aws-s3.md) - Prerequisites, IAM policy/role, CloudTrail setup, and FortiCASB add/update steps for monitoring AWS S3 in legacy FortiCASB 24.4.b.
- [Onboarding Azure Storage](topics/legacy-admin-guide/onboarding/azure-storage.md) - Azure subscription, Reader and Storage Blob Data Reader roles, blob logging, and FortiCASB add/update steps for Azure Storage in legacy FortiCASB 24.4.b.
- [Onboarding Box](topics/legacy-admin-guide/onboarding/box.md) - Edition and permission prerequisites plus OAuth add/update steps for Box in legacy FortiCASB 24.4.b.
- [Onboarding Citrix ShareFile](topics/legacy-admin-guide/onboarding/citrix-sharefile.md) - ShareFile user-access setup, subdomain entry, and OAuth add/update steps for Citrix ShareFile in legacy FortiCASB 24.4.b.
- [Onboarding Confluence](topics/legacy-admin-guide/onboarding/confluence.md) - Atlassian OAuth 2.0 app, scopes, webhook install and creation, and FortiCASB add/update steps for Confluence Cloud in legacy FortiCASB 24.4.b.
- [Onboarding Dropbox Business](topics/legacy-admin-guide/onboarding/dropbox-business.md) - Plan and Team Admin prerequisites plus OAuth add/update steps for Dropbox Business in legacy FortiCASB 24.4.b.
- [Onboarding Egnyte](topics/legacy-admin-guide/onboarding/egnyte.md) - Administrator prerequisite and OAuth add/update steps for Egnyte in legacy FortiCASB 24.4.b.
- [Onboarding Facebook Workplace](topics/legacy-admin-guide/onboarding/facebook-workplace.md) - Custom integration (App ID, App Secret, access token) setup and FortiCASB add/update steps for Facebook Workplace in legacy FortiCASB 24.4.b.
- [Onboarding GitHub](topics/legacy-admin-guide/onboarding/github.md) - Organization plan and Owner prerequisites plus OAuth add/update steps for GitHub in legacy FortiCASB 24.4.b.
- [Onboarding Google Cloud Storage](topics/legacy-admin-guide/onboarding/google-cloud-storage.md) - Service account, domain-wide delegation, org-level roles, API enablement, audit logs, and FortiCASB add/update steps for Google Cloud Storage in legacy FortiCASB 24.4.b.
- [Onboarding Google Workspace](topics/legacy-admin-guide/onboarding/google-workspace.md) - OAuth consent screen, P12 service account, Drive API and domain-wide delegation, audit logs, and FortiCASB add/update steps for Google Workspace in legacy FortiCASB 24.4.b.
- [Onboarding Jira](topics/legacy-admin-guide/onboarding/jira.md) - Browse Projects permission, Atlassian OAuth 2.0 (3LO) app, system webhook, and FortiCASB add/update steps for Jira Cloud in legacy FortiCASB 24.4.b.
- [Office 365 onboarding (after 24.2.a)](topics/legacy-admin-guide/onboarding/office-365-after-24-2-a.md) - Service-account onboarding for Office 365 using a Microsoft Entra ID app registration (client ID, tenant ID, client secret) with Graph and Office 365 Management API application permissions.
- [Office 365 onboarding (before 24.2.a)](topics/legacy-admin-guide/onboarding/office-365-before-24-2-a.md) - Legacy user-account (OAuth consent) onboarding flow for Office 365 in FortiCASB, with audit log, SharePoint site admin, license prerequisites and the delegated permission list.
- [Salesforce onboarding](topics/legacy-admin-guide/onboarding/salesforce.md) - Edition and permission prerequisites plus OAuth add/update procedure for connecting Salesforce to legacy FortiCASB.
- [SAP IAS onboarding](topics/legacy-admin-guide/onboarding/sap-ias.md) - Creating an SAP IAS System administrator with client secrets and audit-log credentials, then adding or updating the account in legacy FortiCASB.
- [SAP SuccessFactors onboarding](topics/legacy-admin-guide/onboarding/sap-success-factors.md) - Registering an OAuth2 client application with an X.509 certificate, granting Manage Integration Tools permissions, and adding or updating SAP SuccessFactors in legacy FortiCASB.
- [ServiceNow onboarding](topics/legacy-admin-guide/onboarding/servicenow.md) - Creating a ServiceNow developer instance and OAuth API endpoint (application registry) and adding or updating the account in legacy FortiCASB.
- [Webex Teams onboarding](topics/legacy-admin-guide/onboarding/webex-teams.md) - Full Administrator requirement in Cisco Webex Control Hub and the OAuth grant flow for adding or updating Webex Teams in legacy FortiCASB.
- [Zendesk onboarding](topics/legacy-admin-guide/onboarding/zendesk.md) - Creating a Zendesk OAuth client with FortiCASB regional redirect URLs and adding or updating the account in legacy FortiCASB.
- [Zoom onboarding](topics/legacy-admin-guide/onboarding/zoom.md) - Zoom role settings, account-level OAuth app with event subscription and scopes, and the FortiCASB add/update steps for legacy FortiCASB.

## Legacy: alerts, reports, Shadow IT, app events, Fabric

- [Overview Features Index](topics/legacy-admin-guide/overview-features/index.md) - Index of legacy FortiCASB 24.4.b Overview feature pages (alerts, reports, audit logs, Shadow IT, app events, Fabric integration).
- [Box Events](topics/legacy-admin-guide/overview-features/app-events-box.md) - Event list for Box Events supported by legacy FortiCASB.
- [Confluence Events](topics/legacy-admin-guide/overview-features/app-events-confluence.md) - Event list for Confluence Events supported by legacy FortiCASB.
- [Dropbox Business Events](topics/legacy-admin-guide/overview-features/app-events-dropbox-business.md) - Event list for Dropbox Business Events supported by legacy FortiCASB.
- [Egnyte Events](topics/legacy-admin-guide/overview-features/app-events-egnyte.md) - Event list for Egnyte Events supported by legacy FortiCASB.
- [GitHub Events](topics/legacy-admin-guide/overview-features/app-events-github.md) - Event list for GitHub Events supported by legacy FortiCASB.
- [Google Workspace Events](topics/legacy-admin-guide/overview-features/app-events-google-workspace.md) - Event list for Google Workspace Events supported by legacy FortiCASB.
- [Jira Events](topics/legacy-admin-guide/overview-features/app-events-jira.md) - Event list for Jira Events supported by legacy FortiCASB.
- [Office 365 Events](topics/legacy-admin-guide/overview-features/app-events-office-365.md) - Event list for Office 365 Events supported by legacy FortiCASB.
- [App Events Overview](topics/legacy-admin-guide/overview-features/app-events-overview.md) - Which cloud apps have event lists in legacy FortiCASB and how events are used in Activity pages, policies, filters and the Audit log.
- [Salesforce Events](topics/legacy-admin-guide/overview-features/app-events-salesforce.md) - Event list for Salesforce Events supported by legacy FortiCASB.
- [SAP IAS Events](topics/legacy-admin-guide/overview-features/app-events-sap-ias.md) - Event list for SAP IAS Events supported by legacy FortiCASB.
- [ServiceNow Events](topics/legacy-admin-guide/overview-features/app-events-servicenow.md) - Event list for ServiceNow Events supported by legacy FortiCASB.
- [Webex Teams Events](topics/legacy-admin-guide/overview-features/app-events-webex-teams.md) - Event list for Webex Teams Events supported by legacy FortiCASB.
- [Zoom Events](topics/legacy-admin-guide/overview-features/app-events-zoom.md) - Event list for Zoom Events supported by legacy FortiCASB.
- [Audit Logs and Data Analysis Logs](topics/legacy-admin-guide/overview-features/audit-logs.md) - Overview > Audit log records administrative and user activity in FortiCASB; Data Analysis Logs show file download/scan/delete activity.
- [Fabric Integration with FortiAnalyzer](topics/legacy-admin-guide/overview-features/fabric-integration-fortianalyzer.md) - Add, authorize, update and remove FortiAnalyzer in FortiCASB, Syslog variables, and port requirements.
- [Global Alerts](topics/legacy-admin-guide/overview-features/global-alerts.md) - Overview > Alert combines Data Analysis, Threat Protection and Compliance alerts from all onboarded cloud apps in one view, with filters.
- [Reports](topics/legacy-admin-guide/overview-features/reports.md) - How to generate C-Level, Compliance, Alert, Activity and Shadow IT reports under Overview > Report.
- [Shadow IT Discovery](topics/legacy-admin-guide/overview-features/shadow-it-discovery.md) - Configuring FortiGate, FortiAnalyzer and FortiCASB for Shadow IT discovery, access control and the dashboard.

## Legacy: data protection

- [Data Protection Overview](topics/legacy-admin-guide/data-protection/index.md) - Index of the legacy FortiCASB 24.4.b Data Protection pages: discovery, files, data security policy, and data patterns.
- [Customized Data Patterns](topics/legacy-admin-guide/data-protection/customized-data-patterns.md) - Creating customized DLP data patterns in legacy FortiCASB using regex (PCRE) or Exact Data Match CSV datasets.
- [Data Security Policy](topics/legacy-admin-guide/data-protection/data-security-policy.md) - Purpose, supported file types, predefined default policy, customized policies and best practice for FortiCASB Data Security Policy.
- [Discovery Analytics](topics/legacy-admin-guide/data-protection/discovery-analytics.md) - Data Protection > Discovery analytics: all files overview, sensitive files exposure and external collaboration.
- [Files Analytics and Filters](topics/legacy-admin-guide/data-protection/files-analytics-and-filters.md) - Data Protection > Files page: bubble charts, filters, Data Analysis scan status and scan limitations.
- [Label and Metered API Prerequisites](topics/legacy-admin-guide/data-protection/label-and-metered-api-prerequisites.md) - How to enable the Google Drive Labels API and the Microsoft Graph metered API for FortiCASB label features.
- [Policy Actions](topics/legacy-admin-guide/data-protection/policy-actions.md) - Actions a FortiCASB Data Security Policy can take: quarantine, change access permission, write label, email and FortiAnalyzer alerts.
- [Policy Example: AV and Malware Monitor](topics/legacy-admin-guide/data-protection/policy-example.md) - Worked example creating a data security policy that quarantines malware and notifies users, file owners and FortiAnalyzer.
- [Policy Match Criteria](topics/legacy-admin-guide/data-protection/policy-match-criteria.md) - The eight match criteria of a customized FortiCASB Data Security Policy, including label triggers.
- [Predefined Data Patterns](topics/legacy-admin-guide/data-protection/predefined-data-patterns.md) - Predefined DLP data patterns in legacy FortiCASB: personal identity, financial, and malware/ransomware categories.

## Legacy: cloud application features

- [Cloud Application Features Index](topics/legacy-admin-guide/cloud-app-features/index.md) - Index of legacy FortiCASB 24.4.b pages on per-application dashboard, files, users, policies, alerts, activity and Yammer.
- [Activity](topics/legacy-admin-guide/cloud-app-features/activity.md) - Activity page: map, filters, alert correlation, Microsoft app integration and Google third-party app verification status.
- [Alerts](topics/legacy-admin-guide/cloud-app-features/alerts.md) - How FortiCASB alerts are produced by Data Analysis, Threat Protection and Compliance policies and where to view them.
- [Compliance Policies](topics/legacy-admin-guide/cloud-app-features/compliance-policies.md) - Compliance standards covered by FortiCASB policies, regex configuration, and configuration of the SOX-COBIT and PCI-DSS policies documented in the guide.
- [Customized Policies](topics/legacy-admin-guide/cloud-app-features/customized-policies.md) - How to create customized Threat Protection policies (content and activity monitoring) with a worked SSN download example.
- [Dashboard and Account Status](topics/legacy-admin-guide/cloud-app-features/dashboard-and-account-status.md) - Cloud application dashboard contents, account status and onboarding checklist, and how to delete a cloud account in legacy FortiCASB 24.4.b.
- [Files](topics/legacy-admin-guide/cloud-app-features/files.md) - Files page in each cloud application: bubble chart, filters, Highlight filter, data scan statuses, normalized share types and Microsoft/Google integrations.
- [Normalized Share Types](topics/legacy-admin-guide/cloud-app-features/normalized-share-types.md) - Mapping of per-application share permissions to the five FortiCASB normalized share types, plus the Appendix B summary taxonomy.
- [Policies Overview](topics/legacy-admin-guide/cloud-app-features/policies-overview.md) - Policy types per cloud application, how to enable a policy, and the general configuration parameters shared by policies.
- [Threat Protection Policies](topics/legacy-admin-guide/cloud-app-features/threat-protection-policies.md) - Per-policy description, parameters and configuration steps for each FortiCASB threat protection policy.
- [Users and Administrative Privileges](topics/legacy-admin-guide/cloud-app-features/users-and-admin-privileges.md) - Users page, user property types, and which roles FortiCASB treats as privileged per cloud application.
- [Yammer Integration](topics/legacy-admin-guide/cloud-app-features/yammer-integration.md) - Prerequisites and steps to enforce Office 365 identity in Yammer and verify Yammer licenses so FortiCASB can monitor Yammer files.

## Legacy: REST API

- [REST API Index](topics/legacy-admin-guide/api/index.md) - Index of the FortiCASB REST API reference pages with the endpoints each covers.
- [Alert Endpoints](topics/legacy-admin-guide/api/alert-endpoints.md) - Request and response reference for the Post Alert List endpoint (/api/v1/alert/list).
- [Business Unit and Country Endpoints](topics/legacy-admin-guide/api/business-unit-and-country-endpoints.md) - Reference for Get Business Unit Info (/api/v1/businessUnit/info) and Get Country List (/api/v1/country/list).
- [Dashboard Endpoints](topics/legacy-admin-guide/api/dashboard-endpoints.md) - Reference for the dashboard REST endpoints - risk trend, statistics, summary and usage trend.
- [Document Profile Endpoints](topics/legacy-admin-guide/api/data-protection-and-document-endpoints.md) - Reference for Post Document Profile Summary and Post Document Profile List, which return data protection file profile information.
- [Event and Filter Endpoints](topics/legacy-admin-guide/api/event-and-filter-endpoints.md) - Reference for Get Event (/api/v1/event) and Get Filter List (/api/v1/filter/list).
- [API Overview and Authentication](topics/legacy-admin-guide/api/overview-and-authentication.md) - FortiCASB REST API conventions, the three token acquisition methods, request headers, throttling, and the token and resource-map endpoints.
- [Policy Endpoints](topics/legacy-admin-guide/api/policy-endpoints.md) - Reference for the data security, threat protection and compliance policy list endpoints.
- [Report Endpoints](topics/legacy-admin-guide/api/report-endpoints.md) - Reference for the C-Level, Compliance, Shadow IT and Alert report summary endpoints.
- [Service, Status, Severity and User Endpoints](topics/legacy-admin-guide/api/service-status-and-user-endpoints.md) - Reference for Get Service History, Get Application Status, Get Severity, Get Status and Get User List.

## Legacy: troubleshooting and appendices

- [Appendix and Troubleshooting Index](topics/legacy-admin-guide/appendix/index.md) - Entry point for the legacy FortiCASB 24.4.b troubleshooting, appendix, data retention and legal pages.
- [Appendix A - Amazon Policy Usage](topics/legacy-admin-guide/appendix/aws-s3-policy-usage.md) - AWS IAM permissions granted to FortiCASB per service and the FortiCASB feature each one supports.
- [Data Retention Policy](topics/legacy-admin-guide/appendix/data-retention.md) - How long FortiCASB retains each data type while a license is active and after it expires.
- [Troubleshooting - Licensing and Getting Started](topics/legacy-admin-guide/appendix/troubleshooting-getting-started.md) - Symptom, cause and fix steps when a new or renewed FortiCASB license does not appear.
- [Troubleshooting - Office 365](topics/legacy-admin-guide/appendix/troubleshooting-office-365.md) - Symptom, cause and fix guidance for Office 365 site collection admin, users, groups, sync and Insufficient Permissions (OneDrive and SharePoint) errors.
- [Troubleshooting - Salesforce, Dropbox Business, Google Workspace, API Throttling](topics/legacy-admin-guide/appendix/troubleshooting-salesforce-dropbox-google.md) - Symptom, cause and fix tables for onboarding and connection errors on Salesforce, Dropbox Business and Google Workspace, plus the cross-app API throttling message.

## Sources

- [Skipped and out-of-scope files](sources/_skipped.md) - skipped
- [CASB-SSPM Competitive Intelligence Newsletter 2026-08-17](sources/casb-sspm-ci-newsletter-2026-08-17.md) - ingested
- [CASB-SSPM newsletter 2026-08-24](sources/casb-sspm-newsletter-2026-08-24.md) - ingested
- [CASB-SSPM Newsletter Sep2026 (shorter variant)](sources/casb-sspm-newsletter-sep2026.md) - ingested
- [CASB-SSPM Newsletter September 2026](sources/casb-sspm-newsletter-september-2026.md) - ingested
- [FortiCASB-SSPM competitive analysis (HTML report, Aug 2026)](sources/competitive-analysis-forticasb-sspm-2026-08.md) - ingested
- [CNAPP and SSPM TechExpo slide deck](sources/deck-cnapp-and-sspm-techexpo.md) - ingested
- [FortiCNAPP and FortiCASB-SSPM](sources/deck-forticnapp-and-forticasb-sspm.md) - ingested
- [FortiCASB Unofficial Sales Deck (jhurley, Sept 2026)](sources/deck-forticasb-sales-unofficial-2026-09.md) - ingested
- [Intro to FortiCASB-SSPM - Nov 25 (Lee Kappon, Director Product Management)](sources/deck-intro-to-forticasb-sspm-nov25.md) - ingested
- [Intro to FortiCASB-SSPM (early variant)](sources/deck-intro-to-forticasb-sspm.md) - ingested
- [SaaS Security - SSPM (Final Version), Q1 2026](sources/deck-saas-security-sspm-final.md) - ingested
- [TDM Presentation - FortiGuard CASB (inline and API)](sources/deck-tdm-presentation-casb.md) - ingested
- [TechTalk: FortiCASB-SSPM v1.1](sources/deck-techtalk-forticasb-sspm-v1-1.md) - ingested
- [Expert Talks: FortiCASB-SSPM (Haviv Ohayon, Director Product Management)](sources/expert-talks-forticasb-sspm-suridata.md) - ingested
- [FortiCASB 24.4.b Admin Guide](sources/forticasb-admin-guide-24-4-b.md) - ingested
- [FortiCASB Product, Licensing and Platform Update v1.5 (Sept 2026, internal working guidance)](sources/forticasb-commercial-platform-update-v1-5.md) - ingested
- [FortiCASB Data Sheet v0.10 (draft with review comments)](sources/forticasb-data-sheet-v0-10.md) - ingested
- [Product Life Cycle Announcement - FortiCASB SaaS-only licences](sources/forticasb-legacy-lifecycle-notice.md) - ingested
- [FortiCASB-SSPM User Guide (Feb 10, 2026)](sources/forticasb-sspm-user-guide-2026-02.md) - ingested
- [FortiCASB-SSPM vs Market 2026](sources/forticasb-sspm-vs-market-2026.md) - ingested
- [SSPM_CASB_True_Players.xlsx (CASB + SSPM shortlist, Aug 2026)](sources/sspm-casb-true-players-2026-08.md) - ingested
- [User Guide to Suridata's SaaS Security Platform](sources/suridata-user-guide.md) - ingested
- [FortiCASB-SSPM vs Microsoft Defender for Cloud Apps 2026](sources/vs-defender-for-cloud-apps-2026-10.md) - ingested
- [FortiCASB-SSPM vs Defender for Cloud Apps SSPM (variant 1)](sources/vs-defender-for-cloud-apps-v1.md) - ingested
- [FortiCASB-SSPM vs Defender for Cloud Apps SSPM (variant 2)](sources/vs-defender-for-cloud-apps-v2.md) - ingested
