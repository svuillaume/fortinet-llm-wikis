---
title: Risks page
summary: Risk lifecycle (active, remediated, accepted), actions (resolve, assign, ticket, history, report, trigger scan) and Jira/ServiceNow ticket synchronization.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Risks page

Overview of all identified risks across the SaaS ecosystem. Opens by default on **active** risks; the Status filter can include **remediated** and **accepted**. Remediated means associated assets are resolved (files no longer shared, third-party apps removed). The same risk name can appear twice: one entry with active assets and one with the remediated count.

## Filters
Priority, risk type, frameworks, core application, assignee, whether a Jira/ServiceNow ticket exists, and number of assets.

## Actions (three-dot menu or bulk buttons)
- **Resolve**: details, remediation effect and steps to remediate.
- **Export Risks.**
- **Assign Risk** via platform user/email, Slack or Teams.
- **Create Ticket** via Jira or ServiceNow. The risk shows the ticketing icon with a clickable ticket number; when the ticket is closed in the external tool the risk record updates and the icon color changes (two-way sync).
- **View Risk History.**
- **Create Report**: executive report of sensitive assets across applications for a timeframe and over time, with overall posture scores and industry benchmarks.
- **Trigger Scan**: the platform scans connected applications **daily** by default, so remediation may be recognized the next day; Trigger Scan forces an immediate check.

`[src: forticasb-sspm-user-guide-2026-02, Risks Page]`

## How risks are created by users
- Filtered third-party inventory > *Save as Risk* ([Third-party apps](third-party-apps.md)).
- Saved file queries ([Search](data-protection-and-search.md)).
- Saved activity filters ([Activities](activities.md)).
Each stores matching items as assets and picks up new matches automatically.

## Related
- [Applications](applications.md)
- [Identities](identities.md)
- [Workflows](workflows.md)
