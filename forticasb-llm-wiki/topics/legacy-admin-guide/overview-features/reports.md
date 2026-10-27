---
title: Reports
summary: How to generate C-Level, Compliance, Alert, Activity and Shadow IT reports under Overview > Report.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Reports (Legacy FortiCASB 24.4.b)

FortiCASB generates C-Level, Compliance and Shadow IT reports; Alert and Activity reports are daily/monthly exports activated by Compliance policies. Screenshots were not extracted.

| Report | Description |
|---|---|
| C-Level | Quarterly, monthly or annual reports |
| Compliance | Overview of compliance with policies such as HIPAA, SOX/COBIT, PCI |
| Shadow IT | Highlights unsanctioned application usage |
| Alert | Daily security alerts (CSV), consolidated monthly (ZIP) |
| Activity | Daily cloud account activities (CSV), consolidated monthly (ZIP) |

[src: forticasb-admin-guide-24-4-b, p.296-297]

## Generate C-Level report
1. Go to **Overview > Report > C-Level**.
2. Click **Generate**.
3. Choose a **Type** (Yearly, Quarterly, or Monthly Report), select the **Year**, then click **Generate C-Level Report**.
4. When generated, download it using the icon in the **Action** column.

[src: forticasb-admin-guide-24-4-b, p.297]

## Compliance reports
Compliance reports are generated automatically monthly, quarterly and yearly; a custom time frame can also be generated. HIPAA, GDPR, SOX-COBIT and PCI-DSS reports are generated in zip format; ISO 27001 and NIST800 reports are PDF. Download with the action icon.

Prerequisite: enable and configure the Compliance Policies required by your organization (Policy Configuration is documented in the Compliance policy section of the guide, p.427; not in this page range).

### Customized compliance report
1. Go to **Overview > Report > Compliance** and click **Generate**.
2. Select a **Report Type**, then select a **Cloud Application** (Office 365, Google Workspace, etc.).
3. Select a **Time Frame** within 90 days from today.
4. In **Select Group**, select one or more Microsoft Entra ID groups to target. If none is selected, all users are targeted.
5. Click **Generate Now**.
6. The file title contains user name, cloud application, report type and date range, e.g. an Office 365 PCI report for 3/1/2020-3/14/2020: `'User Name' Office 365 PCI Compliance Report Mar 14 00:00:00 - Mar 14 23:59:59 UTC.zip` (example as given in the guide).

[src: forticasb-admin-guide-24-4-b, p.297-299]

## Alert report
Tracks all daily security alerts with a downloadable daily report; at month end, daily reports are consolidated into one monthly report.

### Activate
Enable any ONE of these Compliance policies (only one needed):
- NIST800/53 - Track all security alerts (tab **NIST800-53 rev4**)
- NIST800/171 - Track all security alerts (tab **NIST SP800-171**)
- ISO27001 - Track all security alerts (tab **ISO 27001**)

Steps (same for each):
1. Click the target cloud account (Salesforce, Office 365, etc.) in the navigation menu.
2. Go to **Policy > Compliance** and click the relevant tab above.
3. Locate the policy named as above.
4. Enable it by clicking **On**.

### Export
Daily report is a CSV; month-end daily reports are packaged into a ZIP.
1. Go to **Overview > Report > Alert**.
2. In the **Current Month** tab, select a cloud application from the **Cloud App** drop-down.
3. Optionally select a Microsoft Entra ID group in the drop-down on the right; if selected, only that group's users are targeted, otherwise all users.
   - Option 1: select a daily report and click the download button.
   - Option 2: click **Package Up-To-Date for Download** to combine all current-month daily reports into one .zip.
4. Click the **History** tab for monthly reports: select the year and **Cloud App**; all monthly security alert reports for that year are available for export.

[src: forticasb-admin-guide-24-4-b, p.299-302]

## Activity report
Tracks all daily cloud account activities; monthly consolidation as above.

### Activate
Enable Compliance policy **NIST800/53 - Display content of audit record**:
1. Click the target cloud account.
2. **Policy > Compliance**, tab **NIST800-53 rev4**.
3. Locate **NIST800/53 - Display content of audit record**.
4. Click **On**.

### Export
1. **Overview > Report > Activity**.
2. In **Current Month**, select the cloud account from the drop-down.
3. Optionally select a Microsoft Entra ID group (same behavior as Alert report).
   - Option 1: download a single daily report.
   - Option 2: **Package Up-To-Date for Download** (single .zip).
4. **History** tab: select year and cloud application to export monthly activity reports.

[src: forticasb-admin-guide-24-4-b, p.303-304]

## Shadow IT report
Go to **Overview > Report > Shadow IT**; reports are generated automatically. Click **Settings** to configure notification, report format and generation frequency.

Customized date range:
1. On the Shadow IT page click **Generate**.
2. Click **Date Range** and select a time frame.
3. Click **Generate Shadow IT Report**.
4. Download from the **Action** column when ready.

[src: forticasb-admin-guide-24-4-b, p.305-306]

## Related
- [Global Alerts](global-alerts.md)
- [Shadow IT Discovery](shadow-it-discovery.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
