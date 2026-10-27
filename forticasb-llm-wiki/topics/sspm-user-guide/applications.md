---
title: Applications page and connected applications
summary: Managed vs unmanaged applications, priority calculation, connection states, status values, and the Overview, Risks, Users and Activities tabs of a connected application.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Applications page and connected applications

## Application categories
- **Managed applications**: integrated with the platform; detailed security insight.
- **Unmanaged applications**: detected through EDR sources and other data channels; shown in the Inventory page. See [Shadow SaaS](shadow-saas.md).

## Priority ranking
- **Unmanaged apps**: priority from five factors: application type, vendor compliance level, number of users, frequency of interactions, nature of interactions.
- **Managed apps**: weighted average of risk levels inside the application; critical risks weigh more than lower levels.

## Filters
- **Connection Status**: connected; failed (typically check credentials and permissions); connecting; paused (after connecting an app stays paused until the user starts the instance; can also be paused manually). The guide shows the states as icons; icon names are not in the text.
- **Status** (user-settable): Managed (set automatically when an app connects), Unmanaged, Approved, Rejected, Pending.
- Export of the application list and security data; per-application status update.
- **Assign users** via Slack, Teams or email for application ownership.

`[src: forticasb-sspm-user-guide-2026-02, Applications]`

## Connected application tabs

### Overview
Connection status (green active, red issue), priority (low to critical, derived from business impact, likelihood of exploitation, vendor best practices, standards alignment), operational status, number of users and 3rd-party apps, **Risks Over Time** graph.

### Risks
Export; assign risk via Slack/Email/Teams; create ticket via Jira or ServiceNow; view risk history; filter by priority, risk type, frameworks, ticket status, assignee type.

### Users
Columns: Role, Name, Email, Groups, Last Active, Authorized 3rd Party Apps. Actions: export, filter, **set a user as Application Owner** (primary contact for application decisions).

### Activities
Chronological log of user and file actions. Fields: Activity Type (for example Downloaded, Shared, Created link for), User Email, Time, City/Region/Country (from IP), IP Address, VPN/Proxy flag. Filters on all fields combined with AND/OR; export current view to CSV. Listed uses: security monitoring (mass downloads, unauthorized sharing), behavior analysis, compliance audit evidence, incident response.

`[src: forticasb-sspm-user-guide-2026-02, Connected Applications]`

## Related
- [Shadow SaaS](shadow-saas.md)
- [Third-party apps](third-party-apps.md)
- [Risks](risks.md)
- [Activities](activities.md)
