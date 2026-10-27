---
title: GitHub Events
summary: Event list for GitHub Events supported by legacy FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# GitHub Events

Events traced on the cloud app's Activity page; usable as criteria in policies and filters. Table reconstructed from wrapped PDF text; screenshots not extracted. Event type labels for some rows are inferred from the wrapped layout; the first rows (Add Member through Convert To Outside Collaborator) appear under User, and Repository-related rows from Change Repository Visibility onward under Repository.

| Event Type | Event | Description |
|---|---|---|
| User | Add Member | Add a member to the organization |
| User | Add Outside Collaborator | Add a person to the repository. (This person is not an existing organization member and does not exist in outside collaborator) |
| User | Remove Member | Remove a member from the organization |
| User | Remove Outside Collaborator | Remove a person from all of the repositories where this person belongs to. (This person is not an organization member but an outside collaborator) |
| User | Change Role | Change an organization member's role between owner and member |
| User | Convert To Outside Collaborator | Convert an organization member to outside collaborator |
| Team | Add Team | Add team in organization |
| Team | Add Team Member | Add member in existing team |
| Team | Remove Team Member | Remove member from team |
| Team | Delete Team | Delete the team from organization |
| Team | Change Parent Team | This event contains three cases: add a parent team to team; change the parent team of team; remove the parent team of team |
| Repository | Change Repository Visibility | Repository visibility can be change between public and private. |
| Repository | Change Repository Privilege Base Permission | Change repository access base permission for organization members. |
| Repository | Update Team's Role In Repository | Update team's role in the repository. |
| Repository | Update People's Role In Repository | This event contains two cases: update an organization member's role in the repository and update an outside collaborator's role in the repository |
| Repository | Add People To Repository (Collaborators And Teams In Repository) | This event contains three cases: add an existing organization member to the repository; add the person that doesn't belong to this organization in the repository (this person becomes an outside collaborator); add an existing outside collaborator to the repository |
| Repository | Remove People From Repository | This event contains two cases: remove an existing organization member from the repository; remove an outside collaborator from the repository |
| Repository | Add Team To Repository | Add an existing organization team into the repository |
| Repository | Remove Team From Repository | Remove team from the repository |
| File | Upload File | Upload new file |
| File | Delete File | Delete a file |
| File | Modify File | Make changes of a file |
| (Branch/Repository) | Create Branch | Create a branch in the repository |
| (Branch/Repository) | Delete Branch | Delete a branch from repository |
| (Branch/Repository) | Create Repository | Create a repository of the organization |
| (Branch/Repository) | Delete Repository | Delete a repository of the organization |
| (Branch/Repository) | Rename Repository | Change name of the repository |
| (Folder) | Add Folder | Add a new folder in the branch |
| (Folder) | Delete Folder | Delete a folder from the branch |

[src: forticasb-admin-guide-24-4-b, p.332-334]

## Related
- [App events overview](app-events-overview.md)
- [Audit logs](audit-logs.md)
- [Overview Features index](index.md)
