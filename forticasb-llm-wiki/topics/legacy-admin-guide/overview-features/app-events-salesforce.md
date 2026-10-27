---
title: Salesforce Events
summary: Event list for Salesforce Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Salesforce Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. No description column. The type label for the final account/contact rows is inferred as Account.

| Event Type | Event |
|---|---|
| Login | Login Success; Login Failed |
| User | Create User; Modify User; Change Password; Activate User; Deactivate User; Change User Profile; Change User Role; Change User Email; Change User Permission Set |
| Group | Add Group; Add Group Member; Update Group; Change Group Access; Add External Group Member (Customer); Invite People |
| Profile | Create Profile; Modify Profile; Add Permission Set; Modify Permission Set |
| Feed | Post; Modify Post; Comment; Modify Comment |
| File | Upload File; Upload New Version; Download File; Edit File |
| Share | Share File; Share File with People; Share File with Group; Share File via Link; Download File via Link |
| Account (inferred) | Business Modification; Account Owner Change; Contact Modification; Contact Owner Change; Account Create; Contact Create |

[src: forticasb-admin-guide-24-4-b, p.337-339]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
