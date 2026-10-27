---
title: Third-party apps and tokens: inventory, filters, collaboration, revoke access, saved risks
summary: Inventory criteria, filters, templates for collaboration, status automation, revoke-access procedure and prerequisites, and the Save as Risk method.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Third-party apps and tokens

Third-party apps are any apps connected to core applications, including tokens and 3rd-party integrations. Two views: main menu **3rd Party Apps** (all core applications) and the **3rd Party Apps** tab inside one core application. `[src: forticasb-sspm-user-guide-2026-02, 3rd Party Apps]`

## Inventory and priority
Apps are ordered by priority using: permissions (descriptions and priority by access controls), vendor risk, access to sensitive data, marketplace verification, and user activity (inactivity threshold from Settings, default **180 days**).

Tokens (API keys) generated in core applications are included. In some Microsoft cases tokens appear inside the third-party app with secrets and certificates. For each token: roles, type (for example OAuth 2), creation, expiration, last-active date.

### Statistics shown
Status graph (approved, pending, rejected, N/A), priority graph (critical, high, medium, low), sensitive applications count, inactive applications count (over 180 days or the configured threshold).

## Filters
Priority, Application, Vendor, Name, GenAI, Type (apps or tokens), Last Active, Active, Status, Last Status Updated, Users, User Count, Permissions, Permission Scopes, Assignee, Verified, Sensitive, Comments, Justification (Total Responses; Know/Don't Know This App), Token Expiration Date, Token Expiration Status (active, expired, never expire). Not all filters are visible by default; use *More Filters*. Any filter combination can be saved with **Save as Risk**.

## Collaboration
- **Templates** (Settings > Ticketing & Collaboration) for: notify authorizing users, request and remind business justification, assign a risk, assign a 3rd party. Multiple templates per action. **Naming convention**: a template whose name contains an application name is auto-selected for that app (example: "Google Workspace- team assignments").
- **Assign users** via Slack, Teams or email.
- **Request business justification** via Slack/Teams for employees using specific third-party apps; responses compiled in a table.
- **Notify authorizing users** automatically via Slack or email about risks of apps they authorized.
- **3rd Party Apps Users tab** lists users who authorized access, their justification status and interaction counts; reachable through the eye icon on the 3rd Party Apps tab.
- **Automate status changes** (Settings > General): for example "Approved for 30 days" changes to "In Review" after the period; individually or in bulk.
- **Vendor reputation**: vendor category, headquarters, data center, population, domains, supported compliance standards.
- **Summarize data**: comments, Action History (with notes per change), export to CSV.

## Revoke access
- Supported core applications: **Microsoft, Google, Okta, Salesforce, Atlassian** (more planned).
- **Prerequisite**: write permission granted when the application was connected (read-only connections cannot revoke). Revocation can have broader business impact and is **irreversible**; limit the permission through role definitions.
- Procedure: open 3rd Party Apps (page or tab of a core app) > select the core app > select app/token (three-dot menu, or checkboxes for bulk) > **Revoke Access** > review the confirmation modal (lists affected users) > **Confirm**.
- Effect: removed from the application immediately; may take up to **24 hours** to reflect in the platform (daily scan); an audit log entry is created.

## Adding third-party risks (Save as Risk)
Apply filters > **Save as Risk** > enter Risk name and Risk score (1-100, higher = more risk to the business); optionally description, Domain, Frameworks > Save. Matching apps are stored as the risk's **assets** and shown on the Risks page; new apps matching the criteria are added automatically.

Common saved filters: critical apps, sensitive apps, GenAI apps, permission scopes (such as Write), token expiration, assigned apps, non-verified apps, status changes (such as Rejected).

`[src: forticasb-sspm-user-guide-2026-02, 3rd Party Apps - Workflows and Best Practices]`

## Related
- [Risks](risks.md)
- [Workflows](workflows.md)
- [Settings and RBAC](settings-and-rbac.md)
- [OAuth attack-path example](../product/saas-oauth-attack-path-example.md)
