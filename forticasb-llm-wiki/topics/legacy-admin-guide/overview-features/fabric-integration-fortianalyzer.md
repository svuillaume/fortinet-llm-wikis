---
title: Fabric Integration with FortiAnalyzer
summary: Add, authorize, update and remove FortiAnalyzer in FortiCASB, Syslog variables, and port requirements.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Fabric Integration with FortiAnalyzer (Legacy FortiCASB 24.4.b)

Screenshots were not extracted.

## Overview
FortiCASB security alerts and logs can be shared with FortiAnalyzer as part of the Fortinet Security Fabric, so other Fabric products such as FortiGate and FortiClient can access FortiCASB SaaS security alerts. FortiAnalyzer is added in FortiCASB, then FortiCASB is authorized on FortiAnalyzer. [src: forticasb-admin-guide-24-4-b, p.342-343]

## Viewing alerts on FortiAnalyzer
FortiCASB is recognized as a Syslog device. Data Analysis alerts sent to FortiAnalyzer appear as Syslog messages in **Log View > Syslog**.

| Variable | Description |
|---|---|
| type | Type of alert sent from FortiCASB: Data Analysis |
| subtype (optional) | Data Analysis policy's Data Pattern Category: Personal Identity Information, Financial Information, or Malware |
| devid | FortiCASB product serial number the alert originated from |
| sessionid | Alert ID of the FortiCASB security alert sent |
| eventtype | Static; always "FORTICASB-FINDING" |
| tz | Time zone of the alert |
| docsource | Cloud application where the alert triggered, e.g. Salesforce, Office 365, Box, Dropbox, Google Workspace |

[src: forticasb-admin-guide-24-4-b, p.343-344]

## Requirements
1. FortiAnalyzer 5.4 or later.
2. FortiCASB license (serial number starts with FCASBR or FCASBP) and SKU in the format FC2-10-FCASB-145-02-XX.

## Port requirements
1. A ping request is sent from FortiCASB to FortiAnalyzer TCP port 514 when FortiAnalyzer is first added (connection test).
2. FortiAnalyzer UDP port 514 receives Syslog messages from FortiCASB.

Open UDP 514 and TCP 514 to the FortiCASB IPs:
| Region | FortiCASB IP |
|---|---|
| Global (US) | 52.41.24.220 |
| European Union | 34.247.192.72 |

[src: forticasb-admin-guide-24-4-b, p.344-345]

## Add FortiAnalyzer on FortiCASB
Collect first: FortiAnalyzer IP address and serial number.
1. Go to **Overview > Fabric Integration**.
2. Click **+Add New**.
3. **Device IP Address**: the FortiAnalyzer IP (e.g. 254.254.254.254). **Device Serial Number**: in FortiAnalyzer, **System Settings > System Information**.
4. Click **Add New FortiAnalyzer**. FortiCASB sends a test log and awaits authorization.

[src: forticasb-admin-guide-24-4-b, p.345-346]

## Authorize FortiCASB on FortiAnalyzer
Wait 5-10 minutes for the FortiCASB device to appear in FortiAnalyzer's unauthorized devices.
1. Log into FortiAnalyzer.
2. Go to **Device Manager**.
3. In **Device & Groups**, select **Unauthorized Devices**.
4. Check the FortiCASB device whose Connecting IP is the FortiCASB IP.
5. Click **Authorize**, then **OK**.
6. Optional: select the device, **Edit**, rename to "FortiCASB" or another name.
7. FortiCASB should now appear under **All Logging Devices**.

[src: forticasb-admin-guide-24-4-b, p.347-349]

## Remove FortiAnalyzer
Remove it on both sides to fully remove the integration.
1. FortiCASB: **Overview > Fabric Integration**.
2. On the device, click **Action** > **Delete Device**.
3. Click **Delete Device** again to confirm.
4. FortiAnalyzer: **Device Manager > All Logging Devices**.
5. Locate the device with the FortiCASB IP and delete it.

About 5 minutes after completion, FortiCASB stops sending alerts to FortiAnalyzer Syslogs.

[src: forticasb-admin-guide-24-4-b, p.349-350]

## Update FortiAnalyzer
Only allows renaming the device in FortiCASB; no action is required on FortiAnalyzer.
1. **Overview > Fabric Integration**.
2. **Action** > **Update Device**.
3. Rename the **Device Name**.
4. Click **Update FortiAnalyzer**.

[src: forticasb-admin-guide-24-4-b, p.351]

## Related
- [Shadow IT Discovery](shadow-it-discovery.md) (separate FortiAnalyzer log-source use)
- [Global Alerts](global-alerts.md)
- [Overview Features index](index.md)
