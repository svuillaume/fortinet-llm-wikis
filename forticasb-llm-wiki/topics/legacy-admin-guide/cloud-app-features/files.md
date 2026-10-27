---
title: Files
summary: Files page in each cloud application: bubble chart, filters, Highlight filter, data scan statuses, normalized share types and Microsoft/Google integrations.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Files

Screenshots were not extracted from the source guide. The list of the 11 file filters is shown only as an image in the guide and is not found in the extracted text.

## Introduction

Files is a SaaS data storage security analytics view located in each cloud application except SAP IAS and Zoom. When a cloud account is first added, files already in the account are pulled into the Files page. FortiCASB then updates file status automatically when users access files through the cloud application account.

The files bubble chart categorizes files by:

- **File Type**: all file types regardless of readability within the cloud account storage/bucket. Click a bubble to show files of that type.
- **Data Analysis**: scans and captures files containing DLP data; each bubble represents a Data Analysis policy. Click a bubble to show only files for that policy.
- **Share Type**: normalized share type grouping users by access permission (see below). Click a share type to see files shared by those users.
- Click an app bubble to filter files by app.

[src: forticasb-admin-guide-24-4-b, p.404]

## Filters

There are 11 filters for sorting files across all cloud applications (names not found in extracted text). Highlight and Data Analysis Scan filters are described below.

Example: find malware detected in the last 90 days across all cloud applications.

1. Click **+Add Filter**.
2. Select **Created > Last 90 days**.
3. Click **+Add Filter** again.
4. Select **Data Analysis > AV Scan**.
5. Click the Search sign.
6. All malware from the last 90 days is displayed.
7. Click any item to view basic details, activity, users exposed, and data pattern violation.

[src: forticasb-admin-guide-24-4-b, p.404-406]

## Highlight filter

The Highlight filter filters files by type: Sensitive, External, and Malware.

| Type | Description |
|---|---|
| Sensitive | Files with sensitive information matched by DLP policies, such as Social Security Number, Visa credit card number. |
| External | Files shared with external users/groups. |
| Malware | Infectious files matched by malware policies through AV scan. |

[src: forticasb-admin-guide-24-4-b, p.407-408]

## Data Scan Status

Data Scan Status shows the status of the DLP scan, which identifies PII such as driver license, credit card and social security numbers resting in the cloud account. It helps administrators act on: possible network intrusion access to sensitive data; unauthorized internal storage of personal or sensitive data; potential malware and viruses detected through Fortinet AV scan.

The DLP scan is triggered when user activity is detected on a file resting in the cloud account. If the file is identified as PII, it is noted in the file details. Data Scan Status is under Files in any supported cloud application; hovering over the tooltip shows a description of the status.

There are 17 statuses (not all are supported by every cloud application):

Initiating, In Scan Queue, In Progress, Completed, Cannot Be Scanned, Scan Failure, API Threshold Error, Data Protection Exceeded, Empty File, File Not Found, File Transfer Error, Insufficient Permissions, Internal Error, No Scan Policy, Unknown Error, Unsupported File Size, Unsupported File Type.

Per-status descriptions are not found in extracted text. [src: forticasb-admin-guide-24-4-b, p.408-410]

## Normalized share types

Share permissions from all supported cloud applications are normalized into 5 share types: Private Access, Public Editable, Group Editable, Group Readable, Public Readable. The full mapping is in [normalized-share-types.md](normalized-share-types.md). [src: forticasb-admin-guide-24-4-b, p.410]

## Microsoft Online Apps integration (Office 365 only)

The integration monitors Microsoft Yammer, OneDrive, SharePoint and Teams. In the Files page, shared files from these apps are shown with corresponding logos (logos listed for Yammer, One Drive, Sharepoint, Teams and Azure Active Directory). A file can appear under more than one app, for example both Teams and OneDrive. [src: forticasb-admin-guide-24-4-b, p.417-418]

## Google Drive label integration (Google Workspace only)

Google Drive Labels attach metadata to files in Google Drive. FortiCASB includes labels in Google Workspace file profiles. There are two types:

- **Badged label** (Basic Detail - Badged Label): critical organization metadata, the most visible label next to the file name in Google Docs, Sheets, etc. Only one badged label per organization.
- **Standard label** (Basic Detail - Standard Label): tag-like metadata with fields and values. Maximum 150 standard labels per organization.

Reference cited in the guide: Google's "Get Started as a Drive labels admin". [src: forticasb-admin-guide-24-4-b, p.418-419]

## Related

- [Normalized share types](normalized-share-types.md)
- [Activity](activity.md)
- [Users and administrative privileges](users-and-admin-privileges.md)
- [Data protection](../data-protection/index.md)
- [Cloud application features index](index.md)
