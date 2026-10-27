---
title: Discovery Analytics
summary: Data Protection > Discovery analytics: all files overview, sensitive files exposure and external collaboration.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Data Protection Discovery Analytics

## Introduction
Discovery is at Data Protection > Discovery. It analyzes and categorizes all files from onboarded supported SaaS applications, emphasizing files and users with access that pose the most security vulnerability.

FortiCASB classifies data in cloud accounts as:
- **Data at Rest**: data uploaded before the cloud account was added to FortiCASB.
- **Traffic Data**: data uploaded after the cloud account was added and security monitoring started.

Files are scanned individually when there is an access attempt. After the scan, depending on the enabled Data Analysis policies, files are classified as sensitive or non-sensitive.

Discovery supports only: Salesforce, Office 365, Box, Dropbox, Google Workspace, Egnyte, Github, and Webex.
[src: forticasb-admin-guide-24-4-b, p.353]

## All Files Overview
| Item | Description |
|---|---|
| Malware | Malicious software or files. Click to review and remove malware from cloud accounts. |
| Sensitive Files | Files with DLP data containing personal information identified by Data Analysis policies. Click to list them. |
| Shared Files | Files shared by creators with other users, groups or collaborators. |
| High Risk File Owner | Users considered high risk because they share sensitive files with other users. |
| Exposure Summary | Categorizes users with access to files as Viewer, Editor, Commenter, Others (normalized share types of all platforms). Click a type to show only files shared by that type of user. |
| Top 10 File-Sharing Users | Top 10 file-sharing users across all onboarded cloud applications. |
| Top 10 Users/Groups with Access to Shared Files | Top 10 users granted the most file access. |

Normalized share types are detailed in Appendix B (guide p.563); not covered here.
[src: forticasb-admin-guide-24-4-b, p.354-355]

## Sensitive Files Exposure Overview
Graphical distribution of the number of sensitive files shared per cloud application. Hovering over a color shows the count for that application.
[src: forticasb-admin-guide-24-4-b, p.355]

## External Collaboration
- **External Collaboration Summary**: total number of sensitive and non-sensitive files shared to external users/groups and external domains. Supported only for Office 365, Dropbox, Google Workspace and Box.
- **Top 10 External Domains Shared To**: top 10 external domains with which cloud application files are shared.
- **Top 10 External Users/Group Shared To**: top 10 external users/groups with access to files.
[src: forticasb-admin-guide-24-4-b, p.355-356]

## Related
- [files-analytics-and-filters.md](files-analytics-and-filters.md)
- [data-security-policy.md](data-security-policy.md)
- [index.md](index.md)
