---
title: Google Workspace Events
summary: Event list for Google Workspace Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Google Workspace Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. No description column. The type label for the user events (Create User onward) was not visible in the extracted text; they are grouped as User by inference.

| Event Type | Event |
|---|---|
| Login | Login Success; Login Failure; Login Challenge; Logout |
| File | Create File; Upload File; Edit File; View File; Rename File; Move File; Delete File; Download File; Preview File; Trash File; Untrash File |
| User (inferred) | Create User; Suspend User; Unsuspend User; Modify User; Change Password; Create Data Transfer Request; Delete User; Assign Role; Unassign Role |

[src: forticasb-admin-guide-24-4-b, p.330-331]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
