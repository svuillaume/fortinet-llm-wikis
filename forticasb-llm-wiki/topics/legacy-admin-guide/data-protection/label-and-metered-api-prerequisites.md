---
title: Label and Metered API Prerequisites
summary: How to enable the Google Drive Labels API and the Microsoft Graph metered API for FortiCASB label features.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Label and Metered API Prerequisites

Screenshots were not extracted.

## Enable Google Drive Labels API
Required so FortiCASB can collect Google Drive label data for Data Security Policy configuration and Google Workspace documents' basic profile labels.
1. Log into Google Cloud Console with your Google Workspace account.
2. Open the navigation menu and go to **APIs & Services > Enable APIs & Services**.
3. Click **+ Enable APIs And Services**.
4. In API Library, search for "Drive Labels API" and click it.
5. Click **Enable**.
[src: forticasb-admin-guide-24-4-b, p.373-374]

## Enable Office 365 Metered API
Needed for Office 365 label integration. Consumption of metered APIs and services in Microsoft Graph incurs expense through the associated Azure subscription.
1. Log into Microsoft Azure with an account associated with an Azure subscription.
2. Launch Azure Cloud Shell.
3. Run the command, replacing the parameters:

```
az resource create --resource-group myResourceGroup --name myGraphAppBilling --resource-type Microsoft.GraphServices/accounts --properties "{\"appId\": \"\myClientID\"}" --location Global --subscription mySubscriptionID
```

| Parameter | Description |
|---|---|
| myResourceGroup | Any name for the resource group created when the script runs |
| myClientID | Client ID of the application to be enabled |
| mySubscriptionID | Azure Subscription ID used for billing |

The command returns JSON including `"location": "Global"`, `"properties": {"appId": "<myAppGUID>", "billingPlanId": ..., "provisioningState": "Succeeded"}` and `"type": "microsoft.graphservices/accounts"`.
(The command text is reproduced as printed, including the `\myClientID` escape.)
[src: forticasb-admin-guide-24-4-b, p.374-375]

## Related
- [policy-match-criteria.md](policy-match-criteria.md)
- [policy-actions.md](policy-actions.md)
- [index.md](index.md)
