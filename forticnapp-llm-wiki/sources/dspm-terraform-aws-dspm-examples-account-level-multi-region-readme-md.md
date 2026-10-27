---
title: Integrate AWS with Lacework for DSPM Across Multiple Regions
path: /Users/svuillaume/dspm/terraform-aws-dspm/examples/account-level-multi-region/README.md
topic: dspm
updated: 2026-04-10
size: 2105
sha1: 8abcba0664fb
status: current
---

**Original path:** `/Users/svuillaume/dspm/terraform-aws-dspm/examples/account-level-multi-region/README.md`

**Topic:** [[dspm]]

## Summary (first paragraph of source)

The following example integrates an AWS account with Lacework for Data Security Posture Management (DSPM) scanning deployed across multiple AWS regions. A `global_region` is specified for shared resources (like the S3 output bucket), while scanners are deployed to each region in the `regions` list.
