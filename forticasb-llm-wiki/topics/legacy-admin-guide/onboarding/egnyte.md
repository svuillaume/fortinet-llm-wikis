---
title: Onboarding Egnyte
summary: Administrator prerequisite and OAuth add/update steps for Egnyte in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---
# Onboarding Egnyte

FortiCASB pulls data from Egnyte via RESTful API (portal access "with OAuth2.0 authentication"), monitors user activities and provides DLP Data Analysis for files on Egnyte. Screenshots were not extracted. [src: forticasb-admin-guide-24-4-b, p.118]

## Prerequisites
- The Egnyte account must be an **Administrator**; all other roles are NOT supported. [src: forticasb-admin-guide-24-4-b, p.119]

## Add Egnyte account
1. Log into FortiCASB.
2. **Overview > Dashboard** > **Add New** > **Egnyte** > **Add Selected Cloud App**.
3. Enter the **Egnyte Domain**, e.g. `https://DOMAIN.egnyte.com`.
4. Click **Grant Access@Egnyte**.
5. On the Egnyte OAuth page click **Allow Access**.

Important: the user added in FortiCASB must be the same user currently logged in on Egnyte. After OAuth validation, adding may take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.119-120]

## Update Egnyte account
1. Log into FortiCASB; **Overview > Dashboard**.
2. Open the Egnyte account menu, select **Update Cloud Account**.
3. Enter the **Egnyte Domain** (`https://DOMAIN.egnyte.com`); same-user warning applies.
4. Click **Grant Access@Egnyte**.
5. On the Egnyte OAuth page click **Allow Access**.

May take 15 minutes; check status in **Overview > Dashboard**.

[src: forticasb-admin-guide-24-4-b, p.121-122]

## Related
- [Onboarding index](index.md)
- [Citrix ShareFile](citrix-sharefile.md)
- [Polling intervals](../polling-intervals.md)
