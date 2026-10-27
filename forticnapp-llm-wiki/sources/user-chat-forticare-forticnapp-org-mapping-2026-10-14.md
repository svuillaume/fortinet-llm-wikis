---
title: FortiCare → FortiCloud → FortiCNAPP Organization mapping & migration
path: inline chat ingestion 2026-10-14 (no file on disk)
inline: true
topic: product-overview
updated: 2026-10-14
sha1: d46b04befee0
status: current
---

**Source:** inline note provided by the user on 2026-10-14 via `llm-wiki-ingest`. Addresses the FortiCNAPP→FortiCloud multitenancy migration — authoritative product/migration guidance.

## Content (verbatim)

> How do FortiCare Organizations map to existing FortiCNAPP Organizations?
> FortiCNAPP customers fall under two groups: single-account customers (single tenant) and organizations (multi-account). FortiCloud has a multitenancy solution called Organizations. FortiCloud Organization is a centralized account management service that consolidates multiple FortiCloud accounts into Organization/Organizational Units (OUs).
> Single account FortiCNAPP customers will become single accounts in FortiCloud. FortiCNAPP organizations will become organizations in FortiCloud, and FortiCNAPP sub accounts will become member accounts in FortiCloud. In FortiCloud, each sub account has its own license. In FortiCNAPP, and organization has one license, and there's no mechanism for assigning vCPU usage to subaccounts.
> To carry out the migration of organizational accounts from FortiCNAPP to FortiCloud, we will split the SKUs and assign each FortiCNAPP sub account its own SKU in FortiCloud. During the migration sub accounts will be assigned a single license unit as FortiCNAPP does not support assigning license units to subaccounts.

## Key facts

### Customer taxonomy
- FortiCNAPP customers split into two groups: **single-account (single-tenant)** and **organizations (multi-account)**.
- FortiCloud's **Organizations** feature consolidates multiple FortiCloud accounts into **Organizations / Organizational Units (OUs)**.

### Migration mapping (FortiCNAPP → FortiCloud)
| FortiCNAPP concept | FortiCloud concept |
|---|---|
| Single-account customer | Single FortiCloud account |
| FortiCNAPP organization | FortiCloud Organization |
| FortiCNAPP sub-account | FortiCloud **member account** |

### Licensing — important behavioral change
- **FortiCNAPP (today):** one license per organization. **No mechanism to assign vCPU usage to sub-accounts.**
- **FortiCloud (post-migration):** **each sub-account/member account has its own license.**
- **Migration mechanics:** FortiCNAPP SKUs are **split** so each FortiCNAPP sub-account gets its own SKU in FortiCloud. During migration, each sub-account is **assigned one license unit** (because FortiCNAPP cannot subdivide license units upstream).

## Related wiki pages

- [[product-overview]] — tenancy & FortiCloud Organization model (already synthesized)
- Source stub `user-chat-forticloud-organizations-2026-10-14` — complementary FortiCloud Organizations definition
- Source stub `downloads-forticnapp-itf-process-and-forticloud-iam-configuration-md` — ITF provisioning (new tenants)
- Source stub `tmp-personal-project-new-wiki-llm-wiki-wiki-internal-forticnapp-multicloud-org-md` — OU setup flow

## Conflict / Note

No conflict with existing pages. **New information not previously in the wiki:**
- Explicit N:1 → 1:1 **license split** at migration time.
- Mapping terminology (FortiCNAPP "sub-account" ≡ FortiCloud "member account").
- Statement that FortiCNAPP has **no sub-account vCPU allocation mechanism**.
