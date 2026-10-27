---
title: Automated Configuration (user-ingested, FortiCNAPP admin doc)
path: inline chat ingestion 2026-10-14 (no file on disk)
inline: true
topic: integrations
updated: 2026-10-14
sha1: 7ad5d9e88051
status: current
---

**Source:** inline note provided by the user on 2026-10-14 via `llm-wiki-ingest`. Verbatim excerpt from the FortiCNAPP admin guide section "Automated configuration". Treated as authoritative FortiCNAPP product documentation.

## Content (verbatim)

> Automated configuration
> Use automated integration to quickly deploy FortiCNAPP monitoring into your cloud account.
>
> Automated integration supports the following integration types:
>
> Configuration
>
> Audit log
>
> Kubernetes audit log (for AWS and GCP)
>
> Agentless Workload Scanning
>
> For more information about integration types, see Integration types.
>
> How the automated integration works
> During an automated integration, FortiCNAPP uses Terraform and cloud-native services to deploy and configure all required resources in your environment.
>
> Once you provide credentials and initiate the integration, the process proceeds as follows:
>
> Preflight validation
>
> FortiCNAPP uses your credentials to verify that all required permissions are available and that prerequisite services are enabled. It also discovers existing resources that can be reused.
>
> Terraform initialization and planning
>
> FortiCNAPP generates a Terraform configuration that defines the required resources for the integration. It initializes the Terraform runtime and creates an execution plan based on your account structure and selected options.
>
> Resource deployment
>
> Terraform applies the execution plan to create and configure resources in your account. This may include IAM roles and policies, storage resources, encryption keys, messaging services, and other components required by the integration.
>
> Where supported, FortiCNAPP uses orchestration services such as CloudFormation (including StackSets for organization-wide deployments) to distribute resources across accounts.
>
> Custom resource handling
>
> For steps that require logic beyond native infrastructure provisioning (such as registering the integration with FortiCNAPP or coordinating multi-account setup), FortiCNAPP deploys and invokes short-lived helper components such as Lambda functions.
>
> Integration registration and validation
>
> After infrastructure deployment completes, FortiCNAPP validates that all resources are correctly configured and registers the integration using the created roles and endpoints.
>
> Transition to runtime access
>
> The temporary credentials used for deployment are no longer used. FortiCNAPP operates using the deployed cross-account role or service identity, which has scoped permissions to access data (for example, logs or configuration state).
>
> Prerequisites
> Permissions
> Due to the complexity of permissions, we recommend that for your first deployment you use an account with full administrator access. This access is only used to create the necessary resources in your cloud account and to grant FortiCNAPP permissions to access your cloud resources for analysis.
>
> We recommend that you obtain temporary credentials for this account for this integration. For instructions, see Obtaining temporary cloud account credentials.
>
> AWS and Google Cloud IAM policies
> If you are more experienced with access control, you may create a custom IAM policy with limited permissions and attach the policy to specific roles or users. Example policies are available in the FortiCNAPP console as part of the integration.
>
> Azure application
> Integration with Azure requires an Azure application configured to allow access to the subscription to be monitored. See Creating an Azure app for integration.
>
> Additionally, configure the application with the following permissions:
>
> In the subscription to be monitored, assign the Owner role to this application.
>
> In Entra ID, assign the Application Adminstrator and Privileged Role Administrator roles to the application.
>
> Using automated configuration
> To integrate FortiCNAPP with your cloud account using automated configuration:
> Log in to the FortiCNAPP console.
>
> Go to Settings > Integrations > Cloud accounts and click Add New.
>
> Select the appropriate cloud provider, select Automated configuration, and then click Next.
>
> Specify whether this is an account or organization level integration.
>
> For Azure, specify whether this is a Subscription or Tenant level integration.
>
> An organization level integration will integrate all accounts within your organization.
>
> Select the needed integration types.
>
> Enter your account credentials.
>
> In Default region, select the region where the FortiCNAPP resources will be deployed for the integrations.
>
> Note: This option is only available for AWS and GCP integrations.
>
> Click Next.
>
> FortiCNAPP checks your environment and presents the Discovery Summary showing the environment values.
>
> If needed, expand each integration at the bottom of the Discovery Summary to modify the integration.
>
> Click Integrate.
>
> The selected integrations are created for your cloud account.
>
> Click on an integration type to view the list of cloud resources created for the integration.
>
> The LaceworkTag and LaceworkIntegration tags are added to the cloud resources.
>
> Click Exit.
>
> If any of the selected integration types are not created successfully, FortiCNAPP rolls back the resources created for all integration types so that you can fix the error that caused an integration type to fail and then run automated configuration again.
>
> Resources created by the integration — tags
> lacework_tag=self-deployment, lacework_integration values: agentless, cloudtrail, activitylog, auditlog, configuration, eks_audit_log, gke_audit_log.

## Key facts

- **Scope:** Automated configuration = **Terraform + cloud-native services** orchestrated by FortiCNAPP against your cloud account.
- **Supported integration types:** Configuration (CSPM), Audit log, Kubernetes audit log (AWS and GCP only), Agentless Workload Scanning. **DSPM is NOT part of automated configuration** — must be Terraform/CLI.
- **Flow:** Preflight → Terraform init+plan → Resource deployment (optionally via CloudFormation StackSets) → Custom-resource handling via short-lived helpers (e.g. **Lambda**) → Registration & validation → Transition to runtime access (temporary creds dropped; FortiCNAPP keeps using the deployed cross-account role / service identity).
- **Permissions:** First deployment recommended with **full-administrator temporary credentials** on the cloud account. Advanced users can use a custom IAM policy on AWS/GCP (console shows example policies).
- **Azure specifics:** Needs an Azure **App Registration** that is **Owner** on the target subscription, plus **Application Administrator** and **Privileged Role Administrator** in Entra ID.
- **Default region:** selectable for AWS and GCP only (not Azure).
- **Scope levels:** account/organization (AWS/GCP), subscription/tenant (Azure). Org-level auto-picks up new sub-accounts.
- **Tagging:** created resources get `lacework_tag=self-deployment` and `lacework_integration=<type>`. Values: `agentless`, `cloudtrail`, `activitylog`, `auditlog`, `configuration`, `eks_audit_log`, `gke_audit_log`.
- **Rollback behavior:** if any selected integration type fails, FortiCNAPP rolls back **all** of them so you can fix and retry.
- **Console path:** Settings → Integrations → Cloud accounts → Add New → <Provider> → Automated configuration.

## Related wiki pages

- [[integrations]] — AWS/Azure/GCP/OCI onboarding synthesis
- [[terraform]] — module ecosystem (automated config generates Terraform under the hood)
- [[operations]] — tagging ties into Resource Groups filtering
- Source stub `user-chat-forticloud-organizations-2026-10-14` — complementary FortiCloud OU/tenancy context
