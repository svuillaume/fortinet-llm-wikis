---
title: Use Existing IAM Roles Example
path: /Users/svuillaume/dspm/awls/terraform-aws-agentless-scanning/examples/use-existing-iam-roles-multi-region/README.md
topic: dspm
updated: 2026-04-10
size: 2738
sha1: 3423db0c3aef
status: current
---

**Original path:** `/Users/svuillaume/dspm/awls/terraform-aws-agentless-scanning/examples/use-existing-iam-roles-multi-region/README.md`

**Topic:** [[dspm]]

## Summary (first paragraph of source)

In this example the **global** resources and **regional** resources are added. Global resources include the single per-account resources like S3 bucket and AWS Secret. Regional resources include a VPC, and ECS cluster. Roles for both global and regional resouces are supplied. This assumes that the roles were created manually (outside Terraform) with the correct policies attached. A suffix is appli
