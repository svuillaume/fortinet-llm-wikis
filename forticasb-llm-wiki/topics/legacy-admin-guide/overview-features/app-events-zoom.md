---
title: Zoom Events
summary: Event list for Zoom Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Zoom Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. FortiCASB only monitors messages in Team Chat Channels, not private messages between Zoom users.

| Event Type | Event | Description |
|---|---|---|
| User | Create User | A user has been created. |
| User | Update User | A user profile has been updated. |
| User | Delete User | A user has been deleted. |
| User | Activate User | A user has been activated on Zoom. |
| User | Deactivate User | A user has been deactivated on Zoom. |
| User | Disassociate User | A user has been disassociated. |
| Activity | Login Success | A user has log in successfully. |
| Activity | Logout | A user has log out successfully. |
| Activity | Change Password | The user password has been changed. |
| Activity | Change User Role | The user role has been changed. |
| Channel | Create Channel | A chat channel is created. |
| Channel | Delete Channel | A chat channel is deleted. |
| Message | Message Send | A chat message is sent in the chat room. |
| Message | Message Reply | A chat message is replied in the chat room. |
| Message | Message Update | A chat message is updated in the chat room. |
| Message | Message Delete | A chat message is deleted in from the chat room. |

[src: forticasb-admin-guide-24-4-b, p.341-342]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
