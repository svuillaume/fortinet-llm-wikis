---
title: Update rego package names for Opal custom policies
path: /Users/svuillaume/scriptsv2.0/code-security/iac/update_custom_policies/README.md
topic: code-security
updated: 2026-05-22
size: 2296
sha1: 69b547d206b9
status: current
---

**Original path:** `/Users/svuillaume/scriptsv2.0/code-security/iac/update_custom_policies/README.md`

**Topic:** [[code-security]]

## Summary (first paragraph of source)

As part of improvements to Lacework's Opal engine for Infrastructure-As-Code policies; Lacework has renamed some package in the library of rego code provide in Opal. Where previously functions were available in the `lacework` package and were available via `import data.lacework`, they are now in a `iac` package which is available via `import data.lacework.iac`
