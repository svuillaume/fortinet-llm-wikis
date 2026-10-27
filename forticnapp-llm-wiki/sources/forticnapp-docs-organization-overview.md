---
title: FortiCNAPP Organization overview (enrollment and org roles)
path: https://docs.fortinet.com/document/forticnapp/latest/administration-guide/068366/organization-overview
inline: true
topic: product-overview
updated: 2026-10-14
size: 4021
sha1: ca955708369f
status: current
---

**Original path:** https://docs.fortinet.com/document/forticnapp/latest/administration-guide/068366/organization-overview (matches the Organization overview page cited by the `forticnapp` skill as .../administration-guide/68366/organization-overview, so the URL is corroborated; originally matched by page title "Organization overview" in the FortiCNAPP Administration Guide. The page body could not be rendered for a check, and the text was supplied inline on 2026-10-14 without a URL). No version or last-updated date available.

**Topic:** [[product-overview]]

**Related:** [FortiCloud Organizations (Navigating FortiCloud Services)](pasted-forticloud-organizations-overview.md), [FortiCNAPP Multi-Account Organization Structure](tmp-personal-project-new-wiki-llm-wiki-wiki-internal-forticnapp-multicloud-org-md.md), [FortiCNAPP IAM Users and Access Profiles (Jan 2026 Changes)](tmp-personal-project-new-wiki-llm-wiki-wiki-internal-forticnapp-iam-access-profiles-md.md)

## Summary (first paragraph of source)

FortiCNAPP organizations are a part of FortiCloud Organizations. Enrolling in an organization (one-time, irreversible, up to 100 accounts) centralizes security, compliance and access control across all of a company's accounts.

## Verbatim text

> Organization overview
> FortiCNAPP organizations are a part of FortiCloud Organizations. See [FortiCloud Organizations](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/096943/navigating-forticloud-services#Organizations) for more information on managing the Organization and users.
> Enrolling in an organization allows you to centrally manage your environment's security, compliance, and access control by aggregating information from all your accounts. To use FortiCNAPP's organization capability, you must perform a one-time enrollment process using an existing account.
> An organization can contain multiple accounts so you can also manage components such as alerts, resource groups, team members, and audit logs at a more granular level inside an organization. A team member may have access to multiple accounts and can easily switch between them.
> Organization enrollment process
> The enrollment process is irreversible. Proceed only if you want to enroll all your company's accounts in the organization. An organization can contain a maximum of 100 accounts.
> Before you begin the organization enrollment process, determine which existing account to use for enrollment. This account's FortiCNAPP URL will be used for all accounts in the organization. This URL is also referred to as the organization URL.
> We recommend choosing an account where the individual you want to promote to an organization admin already exists as an account admin. Also consider that the organization and any underlying accounts assume the authentication method of the account used for the enrollment process.
> Choose the correct account. The enrollment process enrolls all your company's accounts in the organization and the process cannot be reversed.
> The general process is as follows:
>
> 1. Log in to the console with the chosen account.
> 2. Open Account Settings and click Organization View at the bottom of the page.
> 3. Verify the details about the account and click Get Started Now.
> 4. Verify that you want to enroll all listed accounts in the organization and click Continue.
> 5. Read the enrollment process details.
> 6. Select a current account admin to be promoted. This admin is granted the organization admin role. This admin gains organization-level admin privileges but also retains its previous account-level privileges.
> 7. Select the acknowledgment checkbox to confirm you want to complete the enrollment process with the chosen account and account admin.
> This enables the Complete Step button.
> 8. Click Complete Step to complete enrollment.
>
> The organization dashboard displays aggregated events and compliance for all accounts within the organization.
> After the enrollment process finishes, the option to start the enrollment process is no longer available for accounts within the new organization.
> After organization enrollment
> Completing organization enrollment introduces two organization-level roles: organization admin and organization user. Only organization admins and users can view organization settings. Only organization admins can edit organization settings. Authentication and usage settings, which were available at the account level before enrollment, are now available only at the organization level. So an account admin that is not granted any organization-level privileges cannot view authentication and usage pages. Determine if you should grant additional team members organization-level roles.
> Because you can set authentication only at the organization level, all accounts within the organization assume the authentication method of the account chosen for initial enrollment. This potential authentication change could affect some account admins' and users' ability to log in to the FortiCNAPP console until the change and necessary remediation steps are communicated within your organization.
> The new organization does not contain any custom alert routing or resource groups at the organization level. Determine if you should define organization-level alert routing and resource groups.
