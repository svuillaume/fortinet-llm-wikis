---
title: Policy Example: AV and Malware Monitor
summary: Worked example creating a data security policy that quarantines malware and notifies users, file owners and FortiAnalyzer.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Create Data Security Policy Example

Goal: monitor for malicious files containing malware or virus; send alerts to the FortiCASB user, file owner and FortiAnalyzer. Screenshots were not extracted.

1. Go to Data Protection > Policies > Scan Policies.
2. Click **+Add New**.
3. In Data Security Policy Name, enter "AV and Malware Monitor".
4. Click the **Enabled** toggle.
5. In Match Criteria, open the **Files Added Within** drop-down and select "Time Frame: All Time". (The criterion is named "Files Created After" elsewhere in the guide.)
6. In File Types, click **Select All**.
7. In Access Permissions, click **Select All**.
8. In File Activity Triggers, click **Select All**.
9. In SaaS Applications, click **Select All**.
10. In DLP Pattern, enable only the Malware type patterns and disable the rest.
11. In Action, turn on **Quarantine Files**.
12. In Send Email Notification, turn on **FortiCASB Users** and enter a user to be notified.
13. Turn on **Notify File Owners** and edit the notification contents.
14. Turn on **Send Alerts to FortiAnalyzer**.
15. Click **Add New Data Security Policy**.
[src: forticasb-admin-guide-24-4-b, p.385-387]

## Related
- [policy-actions.md](policy-actions.md)
- [policy-match-criteria.md](policy-match-criteria.md)
- [predefined-data-patterns.md](predefined-data-patterns.md)
