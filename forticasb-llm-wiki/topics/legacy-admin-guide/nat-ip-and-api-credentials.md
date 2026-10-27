---
title: NAT IP Address and API Credentials
summary: FortiCASB NAT IP addresses per region and how to generate a REST API credential.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# NAT IP Address and API Credentials

## FortiCASB NAT IP address
The public IP address FortiCASB uses to connect to your SaaS or added cloud accounts. Add it to the cloud account's security allow list to avoid alerts when FortiCASB makes API calls.

| Region | FortiCASB site | NAT IP address |
|---|---|---|
| Global (US) | https://www.forticasb.com | 52.41.24.220 |
| European Union (EU) | https://eu.forticasb.com | 34.247.192.72 |

(The table text wraps in the source; EU IP read as 34.247.192.72 and the Global URL as www.forticasb.com.) [src: forticasb-admin-guide-24-4-b, p.45]

## Generate API credential
FortiCASB REST API resources are free and available for development. An OAuth 2.0 bearer token in the Authorization header is required; one way to get it is the Get Credentials Token API, which needs a credential generated as follows.
1. Log into FortiCASB.
2. Click **Switch Company** (top right).
3. In Company, click **Manage Company**.
4. Open the **API Setting** tab.
5. Click **Generate New**.
6. Enter a name and click **Generate Credential**.
7. Copy the credential.

The credential is shown only once; store it securely. It can be reused until revoked in FortiCASB. [src: forticasb-admin-guide-24-4-b, p.45-47]

## Related
- [Polling intervals](polling-intervals.md)
- [Company and first-time setup](company-and-first-time-setup.md)
