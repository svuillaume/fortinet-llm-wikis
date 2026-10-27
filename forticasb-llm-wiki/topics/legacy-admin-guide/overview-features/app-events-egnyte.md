---
title: Egnyte Events
summary: Event list for Egnyte Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Egnyte Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. 

| Event Type | Event | Description |
|---|---|---|
| File | Upload File | Upload a new file |
| File | Delete File | Delete an existing file |
| File | Move File | Move a file to different path |
| File | Copy File | Copy file to different path |
| File | Add Version | Modification in the existing file, create a new version of the file |
| File | Delete Version | Delete version of the file by user |
| File | Delete Version (VPC) | Delete version (Version Policy Control) of the file by Egnyte System |
| File | Restore File | Restore the file from trash |
| File | Rename File | Change the name of the existing file |
| File | Upload File Via Link | Create shared link for sharing to upload file |
| Folder | Add Folder | Upload a new folder |
| Folder | Delete Folder | Delete an existing folder |
| Folder | Move Folder | Move folder to different path |
| Folder | Copy Folder | Copy folder to different path |
| Folder | Restore Folder | Restore folder from the trash |
| Folder | Rename Folder | Change name of the folder |
| Folder | Change share permission | Any change in user permissions on sharing the folder |
| Feed | Create comment | Any note/comment posted by user regarding the file |

[src: forticasb-admin-guide-24-4-b, p.329-330]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
