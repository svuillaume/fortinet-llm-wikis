---
title: Cloud Application Polling Intervals
summary: API polling intervals per cloud application and the list of webhook-integrated applications.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Cloud Application Polling Intervals

Polling interval is how often FortiCASB communicates with the onboarded cloud application host to retrieve real-time data and keep monitored data synchronized. Two types:
1. **API Polling**: FortiCASB queries the cloud application at a fixed interval whether or not an event occurs. Shorter interval = closer to real time.
2. **Webhook Polling**: requests are made automatically by the source/cloud application server when an event occurs, so there is no synchronization delay.

[src: forticasb-admin-guide-24-4-b, p.22]

## API polling intervals

| Cloud application | Polling interval (min) |
|---|---|
| AWS S3 | 10 |
| Azure Storage | 20 |
| Box | 10 |
| Dropbox | 2 |
| Egnyte | 10 |
| GCP Storage | 5 |
| Google Workspace | 1 |
| Office 365 | 1 |
| Salesforce | 4 |
| SAP IAS | 10 |
| SAP SuccessFactors | 4 |
| ServiceNow | 2 |
| Zendesk | 10 |

[src: forticasb-admin-guide-24-4-b, p.22-23]

## Webhook-integrated applications
Citrix, Confluence, Facebook Workplace, Github, Jira, Webex, Zoom. [src: forticasb-admin-guide-24-4-b, p.23]

## Oddity
The Google Workspace native apps section states a 15-minute API poll for Google Drive and Marketplace, while the table lists 1 minute for Google Workspace. [src: forticasb-admin-guide-24-4-b, p.22]

## Related
- [Supported apps and scan scope](supported-apps-and-scan-scope.md)
- [NAT IP and API credentials](nat-ip-and-api-credentials.md) (allow-listing the IP that issues API polls)
