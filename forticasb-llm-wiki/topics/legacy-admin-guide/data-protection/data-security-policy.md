---
title: Data Security Policy
summary: Purpose, supported file types, predefined default policy, customized policies and best practice for FortiCASB Data Security Policy.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Data Security Policy

## Introduction
A Data Security Policy defines which DLP data patterns monitor which type of files under which SaaS applications, which activities trigger an alert, and what mitigation action is taken. In 2024 an enhancement using a Large Language Model framework was added to trigger DLP alerts more accurately, reducing false positives and false negatives and improving classification of text that can match multiple data types. Policies are created in Data Protection > Policies > Data Policies.
[src: forticasb-admin-guide-24-4-b, p.362]

## Supported file types
Mime image files are scanned by OCR for the configured data patterns.

| Category | Types |
|---|---|
| Uncompressed | Microsoft Word (.doc, .docx); PowerPoint (.ppt, .pptx); Excel (.xls, .xlsx); Text (.txt, .rtf, js); PDF (.pdf); Mime image (.jpg, .jpeg, .png, .tif, .tiff) |
| Compressed | .zip, .tar, .7z, .gz, .exe |

Compressed files are extracted and scanned without limitation on the level of compression (a file zipped multiple times is still scanned). Maximum file size for scans: 20 MB (see [predefined-data-patterns.md](predefined-data-patterns.md) and [files-analytics-and-filters.md](files-analytics-and-filters.md)).
[src: forticasb-admin-guide-24-4-b, p.362-363]

## Predefined policy
**Default FortiCASB Scan-All Data Protection Policy** monitors all files under all onboarded SaaS accounts for all types of file activities using the 34 FortiCASB basic predefined data patterns. To use all 147 predefined patterns and customized patterns, create a customized policy. The guide refers to a "Basic Predefined Data Patterns" list; it is not found as a separate list in the sources (see the oddity note in [predefined-data-patterns.md](predefined-data-patterns.md)).
[src: forticasb-admin-guide-24-4-b, p.363]

## Customized policy
Create via **+Add New**. Important: when a customized policy is enabled, disable the Default FortiCASB Scan-All Data Protection Policy to avoid two conflicting policies.
[src: forticasb-admin-guide-24-4-b, p.364]

## Best practice
1. Create a customized policy for the specific files being monitored, to avoid scanning files not intended to be monitored.
2. Choose only the DLP patterns that need protection, to avoid unnecessary scans.
3. Always turn on Email Notification and Notify File Owners.
4. Use Send Alert to FortiAnalyzer if FortiCASB is part of the security fabric.
[src: forticasb-admin-guide-24-4-b, p.364]

## Related
- [policy-match-criteria.md](policy-match-criteria.md)
- [policy-actions.md](policy-actions.md)
- [policy-example.md](policy-example.md)
- [index.md](index.md)
