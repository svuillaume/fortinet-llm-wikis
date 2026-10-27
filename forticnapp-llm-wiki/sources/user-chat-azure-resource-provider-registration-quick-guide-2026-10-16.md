---
title: "Azure CLI Service Registration and Provider: Azure Resource Provider Registration, Quick Guide (user-supplied)"
path: chat message (inline text), 2026-10-16 (original location on disk not stated)
inline: true
topic: integrations
tags: [azure, az-cli, cloud-shell, resource-provider, microsoft.cloudshell]
updated: 2026-10-16
size: 2426
sha1: n/a (inline chat text, no file)
status: current
---

**Source:** a quick guide pasted by the user in chat and ingested with `llm-wiki-ingest`. It ends with the line "Microsoft documentation: Azure Resource Provider Registration" as text only (no URL), so the Microsoft page was not identified or re-checked. The pasted text contained a shell-escaped `\!=` in the final script; it is `!=` below.

**Objective:** check whether an Azure resource provider is registered and register it if needed, from Azure Cloud Shell (Bash).

## Steps (as given)

1. **Select the subscription:** `az account set --subscription <SUBSCRIPTION_ID>`; verify with `az account show --query "{Name:name, ID:id}" -o table`.
2. **Check registration** (example `Microsoft.CloudShell`): `az provider show --namespace Microsoft.CloudShell --query registrationState -o tsv`. Results: `Registered` (no action), `NotRegistered` (register), `Registering` (in progress).
3. **Register if needed:** `az provider register --namespace Microsoft.CloudShell --wait` (`--wait` blocks until registration completes). Permissions stated: Subscription Owner, Contributor, or a custom role with the registration permission.
4. **Verify:** repeat the step 2 command; expected output `Registered`.
5. **Bonus, all providers:** `az provider list --query "[].{Provider:namespace,Status:registrationState}" -o table`.

## One-command version

```bash
PROVIDER="Microsoft.CloudShell"
STATUS=$(az provider show --namespace "$PROVIDER" --query registrationState -o tsv)
if [ "$STATUS" != "Registered" ]; then
    echo "Registering $PROVIDER..."
    az provider register --namespace "$PROVIDER" --wait
else
    echo "$PROVIDER is already registered."
fi
```

Replace `Microsoft.CloudShell` with the provider your Azure service needs.

## Not stated in the source

Which providers a FortiCNAPP Azure integration requires, and whether this guide is part of FortiCNAPP onboarding, are not stated. `NotRegistered`/`Registering` are the only non-registered states listed; Azure may report others (such as `Unregistering`), which the source does not cover.
