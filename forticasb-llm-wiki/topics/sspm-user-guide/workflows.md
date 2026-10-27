---
title: Workflows (triggers, conditions, actions)
summary: No-code workflow model, supported triggers/conditions/actions, canvas steps, AND/OR logic, clone behavior and execution log.
sources: [forticasb-sspm-user-guide-2026-02]
updated: 2026-10-26
status: current
---

# Workflows

Automation that runs defined actions when specific conditions are met. The Workflows page lists workflows with name, status, last change date and actions (Edit, Clone, Execution Details, Delete). **Clone** creates `Clone-{workflow name}` in an **inactive** state preserving all parameters. Status toggles Active/Inactive in the table.

## Components
1. **Trigger** (what starts it). Categories: 3rd Party Apps, Applications, Risks, Data Access. Examples in the menu: New 3rd Party App Authorized; New Shadow SaaS App Detected; New Asset / Asset Remediated; Risk Identified / Risk Status Changed.
2. **Conditions** (rules). Depend on the trigger:
   - Risk: priority (Critical/High/Medium/Low), status (New, Resurfaced, Reactivated), frameworks (such as SOC 2, ISO 27001).
   - Application: name, Gen-AI based (Yes/No), vendor.
   - 3rd Party Apps: active status, sensitive data access.
   - **AND**: all conditions must match. **OR**: at least one.
3. **Actions**: Send Notification (Slack, Email); Assign (route to a security team for review). Multiple actions can be chained with AND.

## Building a workflow
1. Workflows page > **Add** (opens the canvas).
2. Choose a trigger.
3. Click **+** below the trigger to add a flow.
4. Add Component menu: Condition or Action (drag into the box).
5. Conditions: small **+** adds an AND condition; the large **+** adds an OR condition; trash icon deletes.
6. Add action(s) with the large **+**; small **+** next to an action adds an AND action.
7. Enter a unique name and toggle **Active**. A workflow cannot be activated with missing required details.

## Execution log
Per workflow: items matched by the trigger, items meeting conditions, actions executed, and context such as CSV files sent in notifications or links to automatically created Jira tickets.

## Documented vs presented capabilities
Enablement decks also describe workflow actions such as ticketing, access revocation, misconfiguration fixes and business-justification steps. The User Guide's documented action list is Send Notification and Assign; other actions: not found in this guide. See [Roadmap and FAQ](../product/roadmap-and-faq.md). File-search results can also trigger Quarantine, Revoke permissions, Delete or Notify: see [Search](data-protection-and-search.md).

`[src: forticasb-sspm-user-guide-2026-02, Workflows]`

## Related
- [Risks](risks.md)
- [Third-party apps](third-party-apps.md)
- [Settings and RBAC](settings-and-rbac.md)
