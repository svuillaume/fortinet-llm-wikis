---
title: Shadow IT Discovery
summary: Configuring FortiGate, FortiAnalyzer and FortiCASB for Shadow IT discovery, access control and the dashboard.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Shadow IT Discovery (Legacy FortiCASB 24.4.b)

Screenshots were not extracted from the source.

## Capabilities
By integrating with FortiGate and FortiAnalyzer, FortiCASB gives an overview of sanctioned and unsanctioned cloud applications.
- **Unsanctioned Application Discovery**: uses FortiGate/FortiAnalyzer logs plus FortiCASB's own discovery process.
- **Cloud Risk Score**: per application; factors include (not limited to) user numbers, company size, multi-factor authentication support, service hosting location; scores in multiple criteria are aggregated into one final score.
- **Access Control**: block or monitor applications using FortiCASB and FortiGate.
- **Data Correlation**: FortiGate/FortiAnalyzer data plus FortiCASB data to identify riskier activities.

Requirement: a FortiGate or FortiAnalyzer policy.

[src: forticasb-admin-guide-24-4-b, p.308]

## Scenarios (order of configuration)
- **Scenario 1 - logs from FortiGate**: (1) FortiGate Configuration (all 3 parts); (2) Log Configuration Using FortiGate GUI/CLI; (3) FortiCASB Configuration.
- **Scenario 2 - logs from FortiAnalyzer**: (1) FortiGate Configuration (all 3 parts); (2) FortiAnalyzer Configurations; (3) FortiCASB Configuration.

[src: forticasb-admin-guide-24-4-b, p.308]

## FortiGate configuration
### Part 1 - SSL/SSH Inspection profile
1. FortiGate: **Security Profiles > SSL/SSH Inspection**.
2. Create a new profile named `deep-test`.
3. In **Protocol Port Mapping**, enable **Inspect all ports**.
4. Under **SSH Inspection Options**, enable **SSH deep scan**, click **Specify**, enter ssh port `22`.
5. Under **Common Options**, select **Allow** for Invalid SSL certificates.
6. In **Common Options**, enable **Log SSL anomalies**.

### Part 2 - Application Control
1. **Security Profiles > Application Control**.
2. Select default or create a new profile.
3. Open the **All Categories** drop-down and select **Monitor**.
4. Under **Options**, enable **Allow and Log DNS Traffic** and **Replacement Messages for HTTP-based Applications**.

### Part 3 - Firewall policy
1. **Policy & Objects > Firewall Policy**.
2. Create a new policy named `Shadow-IT`.
3. Security Profiles:
   a. For access control, enable the Web Filter created with the URL filter set (if a web filter profile is set up).
   b. Enable **Application Control** so FortiCASB can track how many cloud applications are visited.
   c. To correlate log data with FortiCASB data, keep Application Control enabled and select `deep-test` in the **SSL/SSH Inspection** drop-down.
4. In **Logging Options**, enable **Log Allowed Traffic** and select **Security Events** or **All Sessions**.

[src: forticasb-admin-guide-24-4-b, p.309-312]

## Log configuration using FortiGate GUI
1. FortiGate: **Log & Report > Log Settings**.
2. Enable **Send Logs to FortiAnalyzer/FortiManager**.
3. In **Server**, enter the FortiCASB receiver IP address (found by pressing **Device** on the FortiCASB Shadow IT dashboard). One of:

| Region | Receiver IPs |
|---|---|
| Global and US | 52.89.162.108 or 52.24.189.163 |
| EU | 54.155.112.218 or 34.240.128.139 |

4. Click **Test Connectivity**.

Choose only one method (CLI or GUI) to configure the FortiCASB connection; if done in the GUI, do not repeat via CLI.

[src: forticasb-admin-guide-24-4-b, p.312-313]

## Log configuration using FortiGate CLI
Obtain the Application Control ID first: FortiGate > **Security Events > Application Control > Other**.

```
config log fortianalyzer setting
set status enable
set server <FortiCASB server IP>
set enc-algorithm high-medium
set upload-option realtime
set reliable enable
end
```
Optional - forward only application-ctrl logs:
```
config log fortianalyzer filter
config free-style
edit 1
set filter-type include
set filter "logid <Application Control ID>"
end
```
Test:
```
execute log fortianalyzer test-connectivity
```
Success returns `Registration: registered` and `Connection: allow`; otherwise an error code is returned. (The guide prefixes commands with `#`.)

[src: forticasb-admin-guide-24-4-b, p.313-314]

## FortiAnalyzer configuration (Scenario 2)
### Part 1 - Port configuration
Provide a public IPv4 address for FortiAnalyzer reachable from the external network on TCP 80 (HTTP) and TCP 443 (HTTPS).
1. FortiAnalyzer: **System Settings > Network**, select the interface.
2. Click **Edit**.
3. Enable HTTPS or HTTP in **Administrative Access** (connectivity is tested later in FortiCASB Configuration).

### Part 2 - System configuration
1. Complete FortiGate Configuration parts 1-3.
2. FortiAnalyzer **System Settings > Administrators**, select the user that will connect to FortiCASB, **Edit**.
3. **Admin Profile**: `Standard_User` or `Super_User`.
4. **JSON API Access**: `Read-Write`.
5. Add RPC-permit read/write via CLI:
```
config system admin user
edit "user"        # the FortiAnalyzer user used to connect to FortiCASB
set rpc-permit read-write
```
(Guide shows no `next`/`end` lines.)

### Part 3 - Configure FortiAnalyzer on FortiGate
1. FortiGate CLI:
```
config log fortianalyzer2 setting
set status enable
set server <FortiAnalyzer server IP>
set enc-algorithm high-medium
set upload-option realtime
set reliable enable
end
```
2. FortiAnalyzer **Device & Groups**: find the unauthorized FortiGate and authorize it.
3. On FortiGate: `execute log fortianalyzer test-connectivity 2`
4. Success returns `Registration: registered` / `Connection: allow`. The guide's sample output also lists FortiAnalyzer Host Name, Adom Name, FortiGate Device ID, Adom disk space, Analytics/Archive usage and data policy days, Log/IPS Packet Log/Content Archive/Quarantine as `Tx & Rx`, and certificate validity with FortiAnalyzer serial.

[src: forticasb-admin-guide-24-4-b, p.315-317]

## FortiCASB configuration
1. Go to **Overview > Shadow IT > Dashboard**. Click **Connect** (top right), then **Add Device**.
2. In **Device Setting**, **Device Type**: FortiGate or FortiAnalyzer.
3. **Device ID**: the serial number of the FortiAnalyzer or FortiGate (on FortiAnalyzer, shown in the System Settings dashboard).
4. **OS Version**: if FortiGate/FortiAnalyzer is 6.0 or above, select "6.0 and higher".
5. **Protocol**: HTTP or HTTPS, matching what is enabled in FortiAnalyzer; the port updates automatically.
6. Click **Test** to test the connection.
7. FortiGate: click **Save**. FortiAnalyzer: fill remaining fields, click **Next**, select the FortiGate device(s) authorized in FortiAnalyzer, click **Save**; a summary page is shown. Ensure the FAZ appears under the **Parent Device** column.

[src: forticasb-admin-guide-24-4-b, p.318-321]

## Access control (using Shadow IT discovery)
After analyzing an application in FortiCASB, use FortiGate Web Filter to block or monitor it.
1. Use FortiCASB to get the host name of the traffic to control.
2. FortiGate: **Security Profile > Web Filter**.
3. Under **Static URL Filter**, choose the URL filter.
4. Click **Create New** to add a URL filter.
5. Choose a **Type**.
6. Choose an **Action**.
7. Set **Status** to Open (as written in the guide; likely "Enable").
8. Click **OK**.

[src: forticasb-admin-guide-24-4-b, p.321-322]

## Shadow IT dashboard
- **Usage of unsanctioned cloud applications**: unsanctioned apps are ranked by risk score, number of users and use volume; FortiCASB shows the most at-risk applications, clients and sessions, with pie charts of statistics and percentages of risky applications, clients and sessions.
- **File insight**: total sanctioned cloud applications used, total users, and total files stored in each cloud application.
- **Top Unsanctioned Apps**: Top High Risk, Client and Session Apps show all applications monitored by FortiCASB; filter with the time range box at top right; click an app for details.

[src: forticasb-admin-guide-24-4-b, p.322-324]

## Related
- [Reports](reports.md) (Shadow IT report)
- [Fabric integration with FortiAnalyzer](fabric-integration-fortianalyzer.md)
- [Overview Features index](index.md)
