---
title: Single Account with Multiple Regions Example
path: /Users/svuillaume/dspm/awls/terraform-aws-agentless-scanning/examples/single-account-multi-region/README.md
topic: dspm
updated: 2026-04-10
size: 1878
sha1: 866464c1e4c2
status: current
---

**Original path:** `/Users/svuillaume/dspm/awls/terraform-aws-agentless-scanning/examples/single-account-multi-region/README.md`

**Topic:** [[dspm]]

## Summary (first paragraph of source)

In this example the **global** resources and **regional** resources are added. Global resources include the single per-account resources like IAM roles, policies, and S3 bucket. Regional resources include a VPC, and ECS cluster. A "one to many" relationship between **global** and **regional** exists so that scanning and snapshot usage avoids cross-region data transfer.
