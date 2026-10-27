---
title: Shadow SaaS applications
summary: How unmanaged SaaS apps are detected, what the Overview and Users tabs show, business-justification requests and the SentinelOne-only block action.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Shadow SaaS applications

Shadow SaaS (unmanaged) applications are applications that IT or security teams do not know about or do not manage. The platform can use network and endpoint protection solutions (EDRs, firewalls, VPNs and others) to identify the applications users are using. `[src: forticasb-sspm-user-guide-2026-02, Shadow SaaS Applications]`

## Overview tab
- **Priority**: five factors (application type, vendor compliance level, number of users, frequency of interactions, nature of interactions).
- **Source**: how the application was identified.
- **Activity**: user actions over a period; each interaction is one HTTP/S request by a specific user.
- **Block Application**: for an application unapproved by policy, generates and applies the necessary policy **in the EDR system. Currently available only for SentinelOne customers.**

## Users tab
- **Users Trends Over Time**: active user engagement.
- **Users table**: users active in the shadow application **within the past 180 days**: full name and endpoint device names; "Number of Interactions" for the selected period.

## Request Business Justification
Targeted Slack or Teams messages to employees using shadow SaaS applications, asking about their familiarity and, if known, the business justification.
- Trigger from the Application list: select one or more apps and click the *Request Business justification* icon (top right of the table); sent to all users identified as using those apps.
- Trigger per user: Users tab of an application, select users and use the icon, or the three-dot menu on a user.
- Responses are compiled in a table.

## Data sources by connector
Shadow SaaS data comes from the FortiAnalyzer / EDR / Proxy connector category (HTTP/S telemetry and devices, read-only admin). See [Connector types](../product/connector-types-and-permissions.md).

## Related
- [Applications](applications.md)
- [Third-party apps](third-party-apps.md)
- [Settings: General tab thresholds](settings-and-rbac.md)
