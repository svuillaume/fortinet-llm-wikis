---
title: Troubleshooting - Licensing and Getting Started
summary: Symptom, cause and fix steps when a new or renewed FortiCASB license does not appear.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Troubleshooting: licensing and getting started

## New account, no license

| Symptom | Likely cause | Fix |
|---|---|---|
| New FortiCASB account shows no license | License not present on the primary FortiCloud account, or present but not yet added to a company | Check FortiCloud (steps below); if present, add it by creating a company; if absent, contact FortiCloud support |

1. Log into FortiCloud (https://support.fortinet.com/) with the primary FortiCloud account.
2. Top menu: Asset > Manage/View Products.
3. Check whether the purchased license is in the product list.
4. If listed, add the license by creating a company (see [Company and first-time setup](../company-and-first-time-setup.md)).
5. If not listed, contact FortiCloud support.

[src: forticasb-admin-guide-24-4-b, p.538-539]

## Renewed license not usable

| Symptom | Likely cause | Fix |
|---|---|---|
| Renewed license/contract not visible on the FortiCASB dashboard | Contract not in FortiCloud account, or not assigned to the company/business unit | Verify in FortiCloud; if present, assign it to the company/business unit in FortiCASB |

1. Log into FortiCloud with the primary account.
2. Asset > View Account Service.
3. Check whether the renewed license/contract is listed. If not, contact FortiCloud support.
4. If listed, it only needs to be assigned to the company/business unit in FortiCASB (see [Business units](../business-units.md) and [Licensing](../licensing.md)).

[src: forticasb-admin-guide-24-4-b, p.539]

## Related
- [Troubleshooting index](index.md)
- [Licensing](../licensing.md)
