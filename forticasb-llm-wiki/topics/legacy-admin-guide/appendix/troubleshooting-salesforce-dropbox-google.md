---
title: Troubleshooting - Salesforce, Dropbox Business, Google Workspace, API Throttling
summary: Symptom, cause and fix tables for onboarding and connection errors on Salesforce, Dropbox Business and Google Workspace, plus the cross-app API throttling message.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Troubleshooting: Salesforce, Dropbox Business, Google Workspace, all apps

## Salesforce: OAuth request error "Saas application API gateway not accessible"

| Symptom | Cause | Fix |
|---|---|---|
| Error shown on the Salesforce panel: "Saas application API gateway not accessible" | Integrated user's profile lacks required permissions | Setup > Manage Users > Users, open the integrated user's profile, enable "API Enabled", "View All Data", "View All Users" |
| Same error with all three permissions enabled | Organization reached Salesforce's daily API request limit | Setup > Company Profile > Company Information, check "API Requests, Last 24 Hours"; if at the maximum, wait for the next 24-hour period and retry |

Salesforce enforces API limits per organization, not per user. If several applications share the org's API requests, consolidate usage between them.

[src: forticasb-admin-guide-24-4-b, p.540-541]

See [Salesforce onboarding](../onboarding/salesforce.md).

## Dropbox Business: OAuth request error

| Symptom | Cause | Fix |
|---|---|---|
| OAuth request error when connecting | Account used to log in to Dropbox Business lacks the required role | Use an account with "Team Admin" permissions |

[src: forticasb-admin-guide-24-4-b, p.555]

See [Dropbox Business onboarding](../onboarding/dropbox-business.md).

## Google Workspace: cannot connect

| Symptom | Cause | Fix |
|---|---|---|
| FortiCASB will not connect to Google Workspace | Google account is not a Super Administrator | Verify at https://admin.google.com/ by logging in; ask a Super Administrator to grant the role, or link using the Super Administrator's account |
| Connection fails despite Super Administrator | Workspace edition: only accounts with a business or enterprise license can use FortiCASB; basic license cannot | Use a Workspace account with a business or enterprise license |

If the administrator is unknown, contact IT, the help desk, or the account's issuer. The guide shows a screenshot of the Super Administrator interface (not reproduced).

[src: forticasb-admin-guide-24-4-b, p.556]

See [Google Workspace onboarding](../onboarding/google-workspace.md).

## API throttling limitation message (all apps)

| Symptom | Cause | Fix |
|---|---|---|
| Dashboard shows an API throttling message | Many files uploaded to a cloud app at once; the file count exceeds the API requests FortiCASB Data Scan can handle at a given time | Wait until FortiCASB adjusts its API call frequency or all calls complete; if it persists, ask the cloud application vendor to raise API request quotas |

[src: forticasb-admin-guide-24-4-b, p.556-557]

See also [polling intervals](../polling-intervals.md).

## Related
- [Troubleshooting index](index.md)
- [Office 365 troubleshooting](troubleshooting-office-365.md)
- [Onboarding index](../onboarding/index.md)
