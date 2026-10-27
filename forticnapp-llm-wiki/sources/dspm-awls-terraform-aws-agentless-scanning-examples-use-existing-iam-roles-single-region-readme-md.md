---
title: Use Existing IAM Roles Example
path: /Users/svuillaume/dspm/awls/terraform-aws-agentless-scanning/examples/use-existing-iam-roles-single-region/README.md
topic: dspm
updated: 2026-04-10
size: 1821
sha1: d852a61fd51d
status: current
---

**Original path:** `/Users/svuillaume/dspm/awls/terraform-aws-agentless-scanning/examples/use-existing-iam-roles-single-region/README.md`

**Topic:** [[dspm]]

## Summary (first paragraph of source)

In this example the **global** and **regional** resouces are added in a single region. Global resouces include the single per-account resouces like S3 bucket. Regional resources include VPC, ECS cluster. Roles for both global and regional resouces are supplied. This assumes that the roles were created manually (outside Terraform) with the correct policies attached. A suffix is applied to predict w
