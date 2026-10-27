---
title: Files Analytics and Filters
summary: Data Protection > Files page: bubble charts, filters, Data Analysis scan status and scan limitations.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Data Protection Files Analytics

## Introduction
Files (Data Protection > Files) is the consolidated SaaS data-storage analytics view for all onboarded cloud applications. When a cloud account is first added, its files are pulled into the Files page; status is then updated automatically when users access files through the cloud application account. A Files view is also available within each cloud application except SAP IAS and Zoom.
[src: forticasb-admin-guide-24-4-b, p.356]

## Bubble charts
The bubble chart categorizes files by File Type, Data Analysis, Share Type and SaaS App (SaaS App bubble chart exists only on the consolidated Files page).
- **File Type**: all file types regardless of readability within the account storage/bucket. Click a bubble to show that type.
- **Data Analysis**: files containing DLP data; each bubble is one Data Analysis policy. Click to show files for that policy.
- **Share Type**: normalized share type grouping users by access permission (Appendix B, guide p.563). Click to show files shared by that type.
- **SaaS App**: filters files by cloud platform.
[src: forticasb-admin-guide-24-4-b, p.356-357]

## Filters
There are 11 filters for sorting files across cloud applications (the guide lists them in a screenshot, not extracted; the 11 names are not found in text sources). Two are detailed: Highlight and Data Analysis Scan.

### Procedure: malware detected in last 90 days
1. Click **+Add Filter**.
2. Select **Created > Last 90 days**.
3. Click **+Add Filter** again.
4. Select **Data Analysis > AV Scan**.
5. Click the Search sign.
6. All malware from the last 90 days is displayed.
7. Click any file to view basic details, activity, users exposed and data pattern violation.
[src: forticasb-admin-guide-24-4-b, p.357-359]

### Highlight filter
Filters by file type: Sensitive, External, Malware.

| Highlight | Description |
|---|---|
| Sensitive | Files with sensitive information matched by DLP policies, e.g. Social Security Number, Visa credit card number |
| External | Files shared with external users/groups |
| Malware | Infectious files matched by malware policies through AV scan |
[src: forticasb-admin-guide-24-4-b, p.359-360]

### Data Analysis Scan filter
Data Analysis Scan (also DLP Scan) identifies PII such as driver license, credit card and Social Security numbers resting in cloud accounts. Stated purposes: (1) possible network intrusion access on sensitive data; (2) unauthorized internal storage of personal or sensitive data; (3) detect potential malware and viruses through Fortinet AV scan. The scan is triggered when user activity is detected on a file; if the file is PII, it is noted in file details.
[src: forticasb-admin-guide-24-4-b, p.360]

## Data Analysis Scan Status
| Status | Description |
|---|---|
| Scanned | Scan completed; result available |
| Scan N/A | Scan not conducted due to the limitations below |
| Waiting | No user activity yet; file awaits scan |

### Scan limitations (Scan N/A)
1. File size exceeds 20 MB.
2. File extension is not a supported type (see [data-security-policy.md](data-security-policy.md)).
3. All Data Analysis policies are disabled (guide references Policy Configuration, p.427).
[src: forticasb-admin-guide-24-4-b, p.361]

## Related
- [discovery-analytics.md](discovery-analytics.md)
- [data-security-policy.md](data-security-policy.md)
- [index.md](index.md)
