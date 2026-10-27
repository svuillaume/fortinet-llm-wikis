---
title: Threat Protection Policies
summary: Per-policy description, parameters and configuration steps for each FortiCASB threat protection policy.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Threat Protection Policies

Policies: Excessive Login Failures, Suspicious Movement, Unapproved Login Location, Restricted User, Suspicious IP, Suspicious Time, Suspicious Location, Sensitive File, Sensitive Event, Large File Upload, Suspicious Label Activity (Google Workspace only). The Password Change and Ransomware Behavior Detection policies appear in the catalog ([policies-overview.md](policies-overview.md)) but have no configuration section in the guide (not found in sources). Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.430]

## Common procedure

Unless noted, every policy below is configured as follows (policy-specific steps follow in each section):

1. Click a Cloud Account drop-down on the FortiCASB dashboard (for example Salesforce, Office365).
2. Click **Policy** and select **Threat Protection**.
3. Locate the policy and click the right arrow `>` to expand it.
4. Click **On** in **Enabled**.
5. Choose the **Severity level** (Critical, Alert, Warning, Information).
6. Fill the policy-specific fields (below).
7. Click **Save Changes**.

When the condition is met, an alert is raised on the Alert page ([alerts.md](alerts.md)).

## Excessive Login Failures

Monitors excessive login attempts of an unidentified user in a time interval. Both the failed-attempt threshold and the interval (minutes) are configurable.

| Field | Meaning |
|---|---|
| Login Attempts | Threshold of failed login attempts before an alert is generated |
| Interval (minute) | Time interval, measured from the first failed login attempt of the same user |

[src: forticasb-admin-guide-24-4-b, p.431-432]

## Suspicious Movement

Monitors changes in user geographical location. If the traveling speed (mph) between the original and new location exceeds the maximum, an alert is generated. The policy also considers the proximity distance of the new location before checking speed. Known users can be excluded via the IP allow list.

| Field | Meaning |
|---|---|
| Velocity Setting (mph) | Maximum speed a user can travel between two locations before being suspicious. Most commonly used: commercial flight speed, 600 mph. |
| Distance Tolerance (mile) | Proximity distance not accounted for. Example: 50 miles means any login within 50 miles of the origin is not suspicious. |
| IP Allow List | IP ranges excluded from monitoring; useful for users who travel periodically. |

[src: forticasb-admin-guide-24-4-b, p.432-434]

## Unapproved Login Location

Monitors logins from a block-listed country.

| Field | Meaning |
|---|---|
| Unapproved Location List | Click to select countries; an alert is generated for any login attempt from them |

[src: forticasb-admin-guide-24-4-b, p.434-435]

## Restricted User

Monitors cloud account activities by targeted users; alerts when they perform certain activities.

| Field | Meaning |
|---|---|
| Event | Choose **Specific events** and select event(s) from the drop-down, or **Select all events** |
| Suspicious User | Choose **Specify users** and use **Select User**, or **Select all users** |

[src: forticasb-admin-guide-24-4-b, p.435-436]

## Suspicious IP

Monitors activities by targeted IP addresses.

| Field | Meaning |
|---|---|
| Suspicious IP | Enter beginning and ending IP of a range and click **+** to add; repeat for more ranges |

[src: forticasb-admin-guide-24-4-b, p.436-437]

## Suspicious Time

Monitors activities outside regular working hours.

| Field | Meaning |
|---|---|
| Event | **Specific events** or **Select all events** |
| Suspicious Time | **Select day in week** drop-down for a day to monitor, then beginning and end time of the day |

An alert fires when the specific activity occurs within the suspicious time frame on the target day. [src: forticasb-admin-guide-24-4-b, p.437-438]

## Suspicious Location

Monitors activities not shown on the location allow list.

| Field | Meaning |
|---|---|
| Location Allow List | **Select Country** drop-down, then **Add**; repeat for more locations |

An alert fires for any activity outside the allow-listed locations. [src: forticasb-admin-guide-24-4-b, p.439]

## Sensitive File

Alerts when targeted cloud account files are accessed; file location is configured by regex.

| Field | Meaning |
|---|---|
| File Path Regex | Valid regex of the target file path |

Examples from the guide:

- `.*` targets all files in the cloud account.
- `^(?:[\w]\:|\\)(\\[a-z_\-\s0-9\.]+)+\.(txt|gif|pdf|doc|docx|xls|xlsx)$` targets paths beginning with `x:\` or `\\` ending in txt, gif, pdf, doc, docx, xls, xlsx. Matches: `\\192.168.0.1\folder\file.pdf`, `c:\my folder\abc abc.docx`.

[src: forticasb-admin-guide-24-4-b, p.440-441]

## Sensitive Event

Monitors specific cloud account activities. Typical use: downloading or uploading multiple files in a given time.

| Field | Meaning |
|---|---|
| Event | **Specific events** or **Select all events** |
| Threshold (Times) | Maximum number of times the event is performed by the same user before an alert |
| Interval (Minutes) | Time window in which the user conducts the targeted activities before an alert |

[src: forticasb-admin-guide-24-4-b, p.441-442]

## Large File Upload

Alerts when an uploaded file exceeds the size threshold.

| Field | Meaning |
|---|---|
| Maximum file size (MB) | Largest file that can be uploaded without triggering an alert |

Step 5 in the extracted text is blank (not found in sources). [src: forticasb-admin-guide-24-4-b, p.442-443]

## Suspicious Label Activity (Google Workspace only)

Alerts when targeted Google Drive label activities exceed a threshold for specific labels. Path: **Google Workspace > Policy > Threat Protection**.

1. Locate Suspicious Label Activity and expand it; click **On** in Enabled.
2. Select the Severity level.
3. In the **Event** drop-down select the triggering event(s):
   - Attach label to file: a new label is attached.
   - Remove label from file: an existing label is removed.
   - Edit label from file: an existing label is modified.
4. In **Specify Label**, choose **Label Type**:
   - Standard Labels: Label Name, Label Field (optional), Label Values (optional).
   - Badged Labels: Label Name and Label Value (optional).
5. Select **Threshold (Number of Activities)** needed to trigger the alert.
6. In **Interval**, select minutes between each activity to trigger an alert.
7. Turn **Email Notification** On and enter the address(es) to receive notification.
8. Click **Save Changes**.

[src: forticasb-admin-guide-24-4-b, p.443-444]

## Related

- [Policies overview](policies-overview.md)
- [Customized policies](customized-policies.md)
- [Alerts](alerts.md)
- [Files (Google Drive labels)](files.md)
