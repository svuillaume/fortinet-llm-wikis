---
title: Data Retention Policy
summary: How long FortiCASB retains each data type while a license is active and after it expires.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Data retention policy

All data types are encrypted and stored in AWS RDS and Elasticsearch (primary storage), with backup snapshots of the RDS and Elasticsearch databases as secondary storage. The source table is flattened in text extraction; the mapping below follows its column order (active license, then license expired).

| Data type | Active license | After license expired |
|---|---|---|
| Company and business unit cloud account data | Not removed | Not removed |
| Audit logs, admin logs, user activities | Not removed | Removed after 90 days |
| Cloud account activities and alerts | Removed after 1 year | Removed after 90 days |
| Cloud account users metadata | Not removed | Removed after 90 days |
| Cloud file data, documents, e-mail attachments, etc. | Not removed | Removed after 90 days |
| Cloud accounts OAuth data | Not removed | Removed after 90 days |
| C-Level, compliance reports, etc. | Not removed | Removed after 90 days |

Note: the "1 year" and "not removed" placement for the activities/alerts row is inferred from the flattened table layout; verify against the PDF page if exactness matters. Snapshot retention duration is not found in sources.

[src: forticasb-admin-guide-24-4-b, p.564-565]

## Related
- [Appendix index](index.md)
- [Licensing](../licensing.md)
