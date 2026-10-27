---
title: Settings, roles and integrations
summary: Users and Roles (4 built-in roles, custom roles), Ticketing & Collaboration, SSO providers, API keys, Shared Accounts and General settings.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Settings, roles and integrations

## Role-based access
- **Users tab**: create users (name, email, role), assign one or more roles, edit/delete.
- **Roles tab**: four built-in roles that cannot be modified:
  1. **Owner**: complete control including critical actions such as revoking access, managing roles and file operations.
  2. **Admin**: full access to assets and settings but cannot perform critical actions such as revoking access or modifying roles.
  3. **User**: view all assets read-only; no actions or settings changes.
  4. **Operator**: restricted to operational tasks with limited permissions.
- An Owner can create roles by cloning (three-dot menu > *Clone role*) and editing permissions, or via **+** (top right) with a role name and selected permissions. The full per-role permission list is shown in the Roles tab (the guide shows only a subset as an image).

## Ticketing & Collaboration
Integrations with ServiceNow, Jira and Slack (Teams and email are used for assignments/notifications). Message templates for assign/notify/justification actions are managed here ([Third-party apps](third-party-apps.md)).

## SSO
Supported SSO providers for logging in to the platform: Okta, OneLogin, AD FS, Azure Entra ID, Google Workspace, JumpCloud.

## API Integrations
Generate, view, edit and delete API keys; link to API documentation. Endpoint reference: not found in sources.

## Shared Accounts
Central management of service-account credentials. When configuring a connector choose an application-specific account or a shared account from a dropdown. Saving credentials as a shared account during setup adds it to the list; changes (such as password updates) apply to all connectors using it; deleting a connector does not delete the shared account unless all connectors are deleted.

## General tab
New Identity criteria; New Shadow SaaS App criteria; 3rd Party Application Status (New Application age, Inactive Application threshold); *Enable automatic password reset* (auto-resets passwords at set intervals to prevent expiration and connection loss); Session Timeout; status options for 3rd party apps, applications and identities; notification exclusions (user groups excluded from certain notifications). Automated status-change rules are also configured here.

## Differences in the predecessor guide
The Suridata guide additionally has a **Domains** tab (list of internal domains so the system distinguishes internal from external file sharing) and a shorter General tab (3rd-party status, session timeout, status options). The Feb 2026 FortiCASB-SSPM guide text does not include a Domains tab.

`[src: forticasb-sspm-user-guide-2026-02, Settings]`, `[src: suridata-user-guide, Settings]`

## Related
- [Dashboard and App Store](dashboard-and-app-store.md)
- [Workflows](workflows.md)
- [Legacy user management](../legacy-admin-guide/user-management-and-permissions.md)
