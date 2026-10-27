---
title: Customized Policies
summary: How to create customized Threat Protection policies (content and activity monitoring) with a worked SSN download example.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Customized Policies

FortiCASB supports personalized policies. To add one: select a cloud application, go to **Threat Protection > Customized**, scroll to the bottom and click **+ Add New**. Customized policies cover two aspects:

- **Content monitoring**: looks for sensitive data in the cloud accounts.
- **Activity monitoring**: monitors user activities for suspicious activity.

Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.452]

## Example: monitor file download links with Social Security number

Generates an alert when any Salesforce text file sharing link containing a social security number is downloaded.

1. Enter a **Policy Name** and **Description**, for example "Text Files Monitors SSN".
2. Click the **Activity** drop-down and select **Download File**.
3. Turn on **Email Notification** to notify FortiCASB users and file owners.
4. In **Notify FortiCASB Users**, enter the FortiCASB user to receive the alert.
5. In **Notify File Owners**, edit the alert content with the file name, activity name, and exposure name parameters.
6. Turn on **Content Matching** to reveal Data Patterns selection.
7. In **Path**, enter `.*.(txt|pdf|doc|docx|xls|xlsx)$` to monitor downloads of all text files.
8. In the **Data Patterns** drop-down, select **DLP SSN**.
9. In the **Share Level** drop-down, select **Anyone View Link**.
10. Click **Add Customized Policy**.

[src: forticasb-admin-guide-24-4-b, p.453-456]

## Related

- [Policies overview](policies-overview.md)
- [Threat protection policies](threat-protection-policies.md)
- [Alerts](alerts.md)
