---
title: Normalized Share Types
summary: Mapping of per-application share permissions to the five FortiCASB normalized share types, plus the Appendix B summary taxonomy.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Normalized Share Types

Normalized share types categorize file access permissions of all supported cloud applications. Instead of retaining per-application permissions, they are converted into 5 share types: Private Access, Public Editable, Group Editable, Group Readable, Public Readable. Tables below reproduce the guide; some cells carry extraction artifacts (a bare number such as "22" or "202" where an identifier or description was lost) and are shown as extracted. [src: forticasb-admin-guide-24-4-b, p.410]

## Private Access

Permissions accessible only by the file owner. [src: forticasb-admin-guide-24-4-b, p.410-412]

| Application | Share permission | Description |
|---|---|---|
| AWS S3 | S3_OBJECT_OWNER_WRITE_OBJ | Owner Write Object |
| AWS S3 | S3_OBJECT_OWNER_WRITE_OBJ_PERM | Owner Write Object Permissions |
| Azure | AZURE_BLOBCONTAINER_PUBLICACCESS_NONE | Private Only |
| Azure | AZURE_BLOB_PRIVATE | Private Only |
| Box | BOX_SHARE_VIEWER | Viewer |
| Box | BOX_SHARE_OWNER | Owner |
| Box | BOX_SHARE_VIEWER_UPLOADER | Viewer Uploader |
| Box | BOX_SHARE_PREVIEWER_UPLOADER | Previewer Uploader |
| Confluence | CONFLUENCE_SHARE_OWNER | Users Own File |
| Dropbox | DROPBOX_SHARE_VIEWER | Viewer |
| Dropbox | DROPBOX_SHARE_OWNER | Owner |
| Dropbox | DROPBOX_LINK_PASSWORD | Link_password |
| Egnyte | EGNYTE_SHARE_EDITOR | User Can Edit Folder content |
| Egnyte | EGNYTE_SHARE_VIEWER | User Can View Folder content |
| Egnyte | EGNYTE_SHARE_OWNER | Users Own Folder |
| Egnyte | EGNYTE_SHARE_FULL_ACCESS | User has Full Access |
| GitHub | GITHUB_REPO_READ | Read |
| GitHub | GITHUB_REPO_ADMIN | Admin |
| GitHub | GITHUB_REPO_NONE | None |
| GitHub | GITHUB_REPO_TRIAGE | Triage |
| GitHub | GITHUB_REPO_MAINTAIN | Maintain |
| Google Workspace | GOOGLE_USER_READER | User View |
| Google Workspace | GOOGLE_USER_OWNER | User Owner |
| Google Workspace | GOOGLE_USER_WRITER | User Edit |
| Google Workspace | GOOGLE_USER_COMMENTER | User Comment |
| Google Workspace | GOOGLE_USER_ORGANIZER | User TeamDrive Member |
| Google Cloud | GOOGLECLOUD_BUCKET_USER_EDIT_BKT | User Can Edit Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_SERVICEACCOUNT_EDIT_BKT | Service Account Can Edit Bucket |
| Google Cloud | (identifier not extracted: "22") | User reads Object |
| Google Cloud | GOOGLECLOUD_OBJECT_OWNPROJECT_READ_OBJ | Own project reads Object |
| Google Cloud | GOOGLECLOUD_OBJECT_PROJECT_READ_OBJ | Project reads Object |
| Google Cloud | GOOGLECLOUD_OBJECT_OWNER_READ_OBJ | Owner reads Object |
| Google Cloud | GOOGLECLOUD_BUCKET_USER_READ_BKT | User Can Read Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_SERVICEACCOUNT_READ_BKT | Service Account Can Read Bucket |
| Google Cloud | GOOGLECLOUD_OBJECT_OWNER_OWN_OBJ | Owner owns Object |
| Google Cloud | GOOGLECLOUD_OBJECT_USER_OWN_OBJ | User owns Object |
| Office365 | OFFICE365_SHARE_READ | View |
| Office365 | OFFICE365_SHARE_OWNER | Owner |
| Salesforce | SALESFORCE_SHARE_READ | Viewer |
| Webex | WEBEX_SHARE_OWNER | (description extracted as "202") |
| Webex | WEBEX_SHARE_DIRECT | File Direct Recipient |

## Public Editable

Accessible and editable by any user. [src: forticasb-admin-guide-24-4-b, p.412-413]

| Application | Share permission | Description |
|---|---|---|
| AWS S3 | S3_OBJECT_PUBLIC_WRITE_OBJ | Public Write Object |
| Confluence | CONFLUENCE_SHARE_EDITOR | User Can Edit File |
| Dropbox | DROPBOX_SHARE_EDITOR | Editor |
| Dropbox | DROPBOX_LINK | Link_public |
| Egnyte | EGNYTE_LINK_ANYONE_DOWNLOAD | Link Shared with Anyone Read and Download |
| Google Workspace | GOOGLE_ANYONE_COMMENTER | Anyone Can Comment |
| Google Workspace | GOOGLE_ANYONE_WRITER | Anyone Can Edit |
| Google Workspace | GOOGLE_LINK_ANYONE_COMMENTER | Anyone With Link Can Edit |
| Google Workspace | GOOGLE_LINK_ANYONE_WRITER | Anyone With Link Can Edit |
| Google Cloud | GOOGLECLOUD_OBJECT_ALLUSERS_OWN_OBJ | All users own Object |
| Google Cloud | GOOGLECLOUD_OBJECT_ALLAUTHUSERS_OWN_OBJ | All users own Object |
| Office365 | OFFICE365_LINK_ALL_EDIT | Anyone Edit Link |

## Group Editable

Accessible and editable only by the group. [src: forticasb-admin-guide-24-4-b, p.413-415]

| Application | Share permission | Description |
|---|---|---|
| AWS S3 | S3_OBJECT_CROSS_WRITE_OBJ | Cross-account Write Object |
| Box | BOX_SHARE_EDITOR | Editor |
| Box | BOX_LINK | Link |
| Box | BOX_SHARE_COOWNER | Coowner |
| Dropbox | DROPBOX_LINK_TEAM_ONLY | Link_team_only |
| Egnyte | EGNYTE_GROUP_SHARE_EDITOR | Group Can Edit Folder content |
| Egnyte | EGNYTE_GROUP_SHARE_OWNER | Group Own Folder |
| Egnyte | EGNYTE_LINK_DOMAIN_DOWNLOAD | Link Shared to Domain - Read and Download |
| Egnyte | EGNYTE_LINK_PASSWORD_DOWNLOAD | Link Shared with Password Protection - Read and Download |
| Egnyte | EGNYTE_LINK_RECIPIENTS_DOWNLOAD | Link Shared to specific User Recepients - Read and Download |
| Egnyte | EGNYTE_LINK_GROUP_DOWNLOAD | Link Shared to Group - Read and Download |
| Egnyte | EGNYTE_GROUP_SHARE_FULL_ACCESS | Group has Full Access |
| Google Cloud | GOOGLECLOUD_BUCKET_GROUP_EDIT_BKT | Group Can Edit Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_DOMAIN_EDIT_BKT | Domain Can Edit Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_PROJECT_EDIT_BKT | Project Can Edit Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_ALLUSERS_EDIT_BKT | All Users Can Edit Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_ALLAUTHUSERS_EDIT_BKT | All Authenticated Users Can Edit Bucket |
| Google Cloud | GOOGLECLOUD_OBJECT_GROUP_OWN_OBJ | Group owns Object |
| Google Cloud | GOOGLECLOUD_OBJECT_DOMAIN_OWN_OBJ | Domain owns Object |
| Google Cloud | GOOGLECLOUD_OBJECT_OWNPROJECT_OWN_OBJ | Own project owns Object |
| Google Cloud | GOOGLECLOUD_OBJECT_PROJECT_OWN_OBJ | Project owns Object |
| Google Workspace | GOOGLE_GROUP_WRITER | Group Edit |
| Google Workspace | GOOGLE_DOMAIN_WRITER | People In The Domain Can Edit |
| Google Workspace | GOOGLE_LINK_DOMAIN_WRITER | People In The Domain With Link Can Edit |
| Google Workspace | GOOGLE_LINK_DOMAIN_COMMENTER | People In The Domain With Link Can Comment |
| Google Workspace | GOOGLE_DOMAIN_COMMENTER | People In The Domain Can Comment |
| Google Workspace | GOOGLE_GROUP_COMMENTER | Group Comment |
| Office365 | OFFICE365_SHARE_EDIT | Edit |
| Office365 | OFFICE365_LINK_LOGIN_EDIT | People In Organization Can Edit |
| Office365 | OFFICE365_LINK_USER_EDIT | People With The Link Can Edit |
| Salesforce | SALESFORCE_SHARE_EDIT | Collaborator |
| Salesforce | SALESFORCE_LINK | Link |
| Webex | WEBEX_SHARE_GROUP | File Group Recipient |

## Group Readable

Readable only by a specific group of users. [src: forticasb-admin-guide-24-4-b, p.415-416]

| Application | Share permission | Description |
|---|---|---|
| AWS S3 | S3_OBJECT_CROSS_READ_OBJ | Cross-account Read Object |
| AWS S3 | S3_OBJECT_CROSS_READ_OBJ_PERM | Cross-account Read Object Permissions |
| AWS S3 | S3_OBJECT_CROSS_WRITE_OBJ_PERM | Cross-account Write Object Permissions |
| Egnyte | EGNYTE_GROUP_SHARE_VIEWER | Group Can View Folder content |
| Egnyte | EGNYTE_LINK_DOMAIN_PREVIEW | Link Shared to Domain - Read only |
| Egnyte | EGNYTE_LINK_PASSWORD_PREVIEW | Link Shared with Password Protection - Read only |
| Egnyte | EGNYTE_LINK_RECIPIENTS_PREVIEW | Link Shared to specific User Recepients - Read Only |
| Egnyte | EGNYTE_LINK_GROUP_PREVIEW | Link Shared to Group - Read Only |
| Google Cloud | GOOGLECLOUD_OBJECT_GROUP_READ_OBJ | Group reads Object |
| Google Cloud | GOOGLECLOUD_OBJECT_ALLAUTHUSERS_READ_OBJ | All Authenticated users reads Object |
| Google Cloud | GOOGLECLOUD_BUCKET_GROUP_READ_BKT | Group Can Read Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_DOMAIN_READ_BKT | Domain Can Read Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_PROJECT_READ_BKT | Project Can Read Bucket |
| Google Cloud | GOOGLECLOUD_BUCKET_ALLAUTHUSERS_READ_BKT | All Authenticated Users Can Read Bucket |
| Google Workspace | GOOGLE_GROUP_READER | Group View |
| Google Workspace | GOOGLE_DOMAIN_READER | People In The Domain Can View |
| Google Workspace | GOOGLE_LINK_DOMAIN_READER | People In The Domain With Link Can View |
| Office365 | OFFICE365_LINK_LOGIN_READ | People In Organization Can View |
| Office365 | OFFICE365_LINK_USER_READ | People With The Link Can View |

## Public Readable

Readable by any user. [src: forticasb-admin-guide-24-4-b, p.417]

| Application | Share permission | Description |
|---|---|---|
| AWS S3 | S3_OBJECT_PUBLIC_READ_OBJ | Public Read Object |
| AWS S3 | S3_OBJECT_PUBLIC_READ_OBJ_PERM | Public Read Object Permissions |
| AWS S3 | S3_OBJECT_PUBLIC_WRITE_OBJ_PERM | Public Write Object Permissions |
| Azure | AZURE_BLOBCONTAINER_PUBLICACCESS_CONTAINER | Public Read Access on Container Level |
| Azure | AZURE_BLOBCONTAINER_PUBLICACCESS_BLOB | Public Read Access on Container and Blob Level |
| Azure | AZURE_BLOB_PUBLIC_READ | Public Read Access on Blob |
| Confluence | CONFLUENCE_SHARE_VIEWER | User Can View File |
| Egnyte | EGNYTE_LINK_ANYONE_PREVIEW | Link Shared with Anyone - Read only |
| Google Cloud | GOOGLECLOUD_OBJECT_ALLUSERS_READ_OBJ | All users reads Object |
| Google Cloud | GOOGLECLOUD_BUCKET_ALLUSERS_READ_BKT | All Users Can Read Bucket |
| Google Workspace | GOOGLE_ANYONE_READER | Anyone Can View |
| Google Workspace | GOOGLE_LINK_ANYONE_READER | Anyone With Link Can View |
| Office365 | OFFICE365_LINK_ALL_READ | Anyone View Link |

## Appendix B summary taxonomy

Appendix B of the guide describes normalization with a coarser list, which differs from the five types above (not reconciled in the sources). Share types with similar file access permission are grouped under one FortiCASB normalized share type. [src: forticasb-admin-guide-24-4-b, p.563]

| Normalized type | Cloud app share types | Description | Supported applications |
|---|---|---|---|
| Editor | File collaborator, Editor, Project Editor, Edit Link Access, etc. | Any user, group, or anyone who can edit the file | Salesforce, Office 365, Box, Dropbox, GitHub, Google Workspace, AWS S3, Google Cloud Storage, Egnyte |
| Viewer | File Viewer, Group Viewer, Project Viewer, View Link Access, etc. | Any user, group, project who can view the file | Salesforce, Office 365, Box, Dropbox, GitHub, Google Workspace, AWS S3, Google Cloud Storage, Azure, Egnyte |
| Commenter | User Commenter, Group Commenter, etc. | Anyone who can comment on the file | Google Workspace |
| Private Access | Private User, Private Team, Private Group | Any private user, group, domain that can access the file privately | Dropbox, Azure, Egnyte |
| Others | Previewer, Uploader, Triager, File Recipient | Non-ordinary access such as previewer, uploader, recipient | Salesforce, Box, Google Workspace, Dropbox, GitHub, WebEx, Egnyte |

## Related

- [Files](files.md)
- [Cloud application features index](index.md)
