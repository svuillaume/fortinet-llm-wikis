---
title: Office 365 Events
summary: Event list for Office 365 Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Office 365 Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. No description column. Type labels for the last rows (Modify Other License through Edit Company Info) were not visible; they follow the Share group in the page order.

| Event Type | Event |
|---|---|
| Login | Login Success; Login Failed |
| User | Create User; Delete User; Modify User; Restore User; Change Password; Modify Role |
| Group | Add Group; Delete Group; Add Group Member; Update Group; Add Group Owner; Delete Group Owner; Set Group Managed By; Create Group Settings; Update Group Settings; Delete Group Settings; Set Group License |
| File | Upload File; Delete File; Download File; Modify File; Access File; Move File; Copy File; Rename File; Edit File |
| Share | Share File; Create Anonymous Link; Delete Anonymous Link; Create Company Link; Delete Company Link; Company Link Used |
| (type not shown, after Share) | Modify Other License; Delete Folder; Create Sharing Invitation; Edit Company Info |

[src: forticasb-admin-guide-24-4-b, p.335-337]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
