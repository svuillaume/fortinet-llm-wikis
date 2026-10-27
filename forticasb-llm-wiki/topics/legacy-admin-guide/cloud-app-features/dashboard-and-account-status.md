---
title: Dashboard and Account Status
summary: Cloud application dashboard contents, account status and onboarding checklist, and how to delete a cloud account in legacy FortiCASB 24.4.b.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Dashboard and Account Status

Screenshots were not extracted from the source guide; descriptions below come from the surrounding text only.

## Cloud application dashboard

The per-application dashboard shows account status, Alert Overview, Policy Overview, Document Overview, Activity Overview, and Top 5 Policy Violation, High Risk Activities, and High Risk Documents. [src: forticasb-admin-guide-24-4-b, p.401]

## Account status and checklist

1. When the cloud account is successfully onboarded, the status shows **Connected**.
2. Click **Checklist > Details** to show the onboarding checklist.
3. All checklist items must be in **Pass** status for FortiCASB to retrieve security data on the cloud account.

[src: forticasb-admin-guide-24-4-b, p.401]

## Delete a cloud account

A cloud account can be deleted in two ways:

1. Go to **Overview > Dashboard**, click the configuration button and select **Delete Account**.
2. Open the cloud app drop-down menu (for example Salesforce), click the configuration button and select **Delete Account**.

A prompt appears; select **Delete Account** to confirm. Deletion takes a couple of hours; during that time another cloud account cannot be added. [src: forticasb-admin-guide-24-4-b, p.402-403]

## Related

- [Cloud application features index](index.md)
- [Files](files.md)
- [Onboarding](../onboarding/index.md)
