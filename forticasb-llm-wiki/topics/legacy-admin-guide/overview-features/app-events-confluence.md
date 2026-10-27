---
title: Confluence Events
summary: Event list for Confluence Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Confluence Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. Most events are captured via Webhook Event.

| Type | Event | Description |
|---|---|---|
| User | User created | New user created in the account. |
| User | User removed | A user is deleted from the account. |
| User | User deactivated | A user is deactivated from the account. |
| User | User followed | A user is reactivated on the account. (name as printed) |
| Group | Group created | Creates a new user group. |
| Group | Group removed | Delete user group. |
| Attachments | Attachment viewed | File view activity via Webhook Event. |
| Attachments | Attachment created | Create File/Upload File activity via Webhook Event. |
| Attachments | Attachment Updated | File update activity via Webhook Event. |
| Attachments | Attachment trashed | Trash/Delete File activity via Webhook Event. |
| Attachments | Attachment restore | File restore activity via Webhook Event. |
| Attachments | Attachment removed | File removed activity via Webhook Event. |
| Label | Label created/added | Label create activity via Webhook Event. |
| Label | Label removed/deleted | Label removed activity via Webhook Event. |
| Space | Space created | Space create activity via Webhook Event. |
| Space | Space updated | Space update activity via Webhook Event. |
| Space | Space logo updated | Space logo activity via Webhook Event. |
| Space | Space removed | Delete space activity via Webhook Event |
| Page | Page viewed | Page view activity via Webhook Event. |
| Page | Page created | Page create activity via Webhook Event. |
| Page | Page updated | Page update activity via Webhook Event. |
| Page | Page moved | Page move activity via Webhook Event. |
| Page | Page removed | Page removed activity via Webhook Event. |
| Page | Page archived | Page archived activity via Webhook Event. |
| Page | Page restored | Page restored activity via Webhook Event. |
| Page | Page trashed | Page deleted activity via Webhook Event. |
| Comment | Comment created | Create comment under this page. |
| Comment | Comment updated | Edit comment under this page. |
| Comment | Comment removed | Delete comment under this page. |

[src: forticasb-admin-guide-24-4-b, p.326-327]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
