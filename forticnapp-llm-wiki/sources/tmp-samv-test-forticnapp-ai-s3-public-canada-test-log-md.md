---
title: Test log: S3 public buckets in Canada regions
path: /Users/svuillaume/tmp/samv_test/forticnapp-ai/s3-public-canada-test-log.md
topic: product-overview
updated: 2026-10-06
size: 2061
sha1: db753abaa27b
status: current
---

**Original path:** `/Users/svuillaume/tmp/samv_test/forticnapp-ai/s3-public-canada-test-log.md`

**Topic:** [[product-overview]]

## Summary (first paragraph of source)

1. Cache search "S3 bucket public access region Canada" -> no hit. 2. Policy search "public" -> found lacework-global-100/101 (S3 global List/Put policy grants) as reference shape; not an exact match (they check bucket-policy grants, not ACL/PolicyStatus public flag), used only as a join-pattern reference (`LW_CFG_AWS_S3 with (...)`). 3. lql_list_datasources name_contains "S3" -> confirmed LW_CFG_
