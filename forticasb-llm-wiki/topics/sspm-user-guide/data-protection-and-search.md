---
title: Data protection: PII discovery, file access security and advanced Search
summary: How the platform scans file-based SaaS apps, the Search query builder, saving queries as risks with workflow actions, and four worked Advanced Search recipes.
sources: [forticasb-sspm-user-guide-2026-02, suridata-user-guide]
updated: 2026-10-26
status: current
---

# Data protection: PII, file access security and Search

## Problem classes named in the guide
Publicly accessible files; overly broad access permissions; exposure of sensitive data to unauthorized internal users. Applies to file-based SaaS such as OneDrive, SharePoint and Google Drive.

## Capabilities
- **PII discovery and classification** across connected file-based SaaS using pattern matching, keyword analysis and other techniques (names, addresses, social security numbers, credit card numbers).
- **File access security**: continuous scanning of files, metadata and user activity (sharing, downloads); detects deviations from established volumes of downloading and sharing; remediation includes revoking sharing permissions.

## Search page
Lists all scanned files from connected file apps. An **advanced query builder** combines file metadata fields with access-control fields using operators such as ranges and dates.
- **Save as a Risk**: Name, Risk Score (1-100), Description.
- Optional **workflow** on results: *Quarantine, Revoke permissions, Delete, Notify by email* each time a newly scanned file meets the criteria; frequency configurable.
- Saved risk appears on the Risks page with all risk actions (assign, ticket).

## Advanced Search recipes
1. **Files containing PII**: field `PII` > pick a type (example *Password*) > operator `Count` > set min/max (example at least 5 passwords). Opening a file lists PII types and counts (example file with 8 passwords).
2. **Duplicate an existing data risk with a changed value**: Risks page > open the risk's asset count > file search page > *Advanced Search* (top right) > edit the condition (for example change the user email) > *Save as a Risk* with new name/score > Save. Works for system risks and user-created data risks.
3. **Files under a parent folder and subfolders**: field `Path`, operator `Starts With`, value the folder URL (example `https://example-my.sharepoint.com/folder_path1/subfolder1/`).
4. **Condition that must occur at least X times** (for example shared externally at least once): operator `Range` on the counted value (example access-control field *Shared external with*), minimum 1.

`[src: forticasb-sspm-user-guide-2026-02, Data Protection]`

## Legacy comparison
The Legacy platform implements data protection through Data Security Policies, predefined patterns and exact data match: see [Legacy data protection](../legacy-admin-guide/data-protection/index.md).

## Related
- [Risks](risks.md)
- [Workflows](workflows.md)
- [Legacy vs SSPM comparison](../product/legacy-vs-sspm-comparison.md)
