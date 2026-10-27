---
title: FortiCNAPP multi-tenant / sub-account support and legacy SAML (user-ingested note)
path: inline chat ingestion 2026-10-15 (no file on disk)
inline: true
topic: product-overview
tags: [FortiCNAPP Multi Tenant, Sub Account, legacy-saml, fortiCloud-authentication, organization]
updated: 2026-10-15
sha1: cb9364d5a448
status: current
---

**Source:** inline note provided by the user on 2026-10-15 via `llm-wiki-ingest`, tagged **FortiCNAPP Multi Tenant or Sub Account**. Product-team guidance (author/origin not stated); treat as authoritative but unversioned.

## Content (verbatim)

> already supports multi-tenancy, but not yet for customers authenticating through FortiCloud.
> We can enable legacy SAML authentication for new customers, allowing them to create a multi-tenant environment, although there are some caveats. and It's technically not an interim solution.
> When FortiCloud authentication went GA, we intentionally placed legacy SAML functionality behind a feature flag.
> Since FortiCloud SAML is cumbersome to configure and doesn't support JIT provisioning, we retained legacy SAML authentication for customers requiring it.
> Enabling this places the customer in a legacy authentication state, which still supports converting a standalone account into an organization.

## Key facts

- **Multi-tenancy (organization with sub-accounts) is supported in FortiCNAPP today, but not yet for customers who authenticate through FortiCloud.**
- **Path for new customers who need multi-tenancy:** enable **legacy SAML authentication**, which lets them create a multi-tenant environment (organization + sub-accounts). "Some caveats" apply; the note does not list them.
- **Not an interim solution:** legacy SAML is a deliberate, retained capability, not a stopgap.
- **Why it exists:** at FortiCloud authentication GA, legacy SAML was intentionally put **behind a feature flag**. FortiCloud SAML is cumbersome to configure and **does not support JIT (just-in-time) provisioning**, so legacy SAML was kept for customers who need it.
- **Side effect:** enabling it puts the customer in a **legacy authentication state**, which still supports **converting a standalone account into an organization**.

## Related wiki pages

- [[product-overview]] — FortiCNAPP organizations (enrollment model) and FortiCloud Organizations
- Source stub `user-chat-forticare-forticnapp-org-mapping-2026-10-14` — FortiCNAPP org/sub-account to FortiCloud Organization/member-account migration mapping
- Source stub `user-chat-forticloud-organizations-2026-10-14` — FortiCloud Organizations definition
- Source stub `forticnapp-docs-organization-overview` — enrollment (one-time, irreversible, up to 100 accounts)
- Source stub `tmp-personal-project-new-wiki-llm-wiki-wiki-operations-external-idp-setup-for-forticloud-md` — external IdP SAML for FortiCloud

## Conflict / Note

No hard conflict, but this **refines** two existing statements in [[product-overview]]:
- The org/sub-account to FortiCloud migration mapping implies organizations are a FortiCloud-side concept; this note says **FortiCloud-authenticated customers cannot yet create a FortiCNAPP multi-tenant environment**, and new multi-tenant customers go through legacy SAML.
- The enrollment note's open item (how the enrolling account's authentication method applies now that FortiCloud login is replacing legacy login) is partly answered: legacy SAML remains available behind a feature flag. The caveats and the timeline for FortiCloud-native multi-tenancy are still **unknown**.
