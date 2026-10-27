---
title: Terraform
summary: Lacework/FortiCNAPP Terraform modules and provider auth.
sources: [downloads-forticnapp-terraform-references-admin-guide-02-appendix-d-md, downloads-forticnapp-terraform-references-admin-guide-08-alert-profiles-md, downloads-forticnapp-terraform-references-admin-guide-03-getting-started-md, downloads-cnapp-tf-md, downloads-forticnapp-terraform-references-admin-guide-01-overview-and-modules-md, downloads-forticnapp-terraform-references-provider-auth-md, downloads-lacework-terraform-reference-md, downloads-forticnapp-terraform-references-module-index-md, scriptsv2-0-lw-oci-integration-readme-md, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-8453a6-txt, downloads-forticnapp-terraform-references-modules-azure-activity-log-md, downloads-forticnapp-terraform-references-modules-azure-ad-application-md, downloads-forticnapp-terraform-references-modules-aws-alerts-to-s3-md, downloads-forticnapp-terraform-references-modules-gcp-audit-log-md, downloads-forticnapp-terraform-references-modules-aws-cloudtrail-controltower-md, downloads-forticnapp-terraform-references-modules-aws-cloudtrail-md, downloads-forticnapp-terraform-references-modules-aws-config-md, downloads-forticnapp-terraform-references-modules-azure-config-md, downloads-forticnapp-terraform-references-modules-gcp-config-md, downloads-forticnapp-terraform-references-modules-oci-config-md, downloads-forticnapp-terraform-references-modules-aws-ecr-md, downloads-forticnapp-terraform-references-modules-aws-eks-audit-log-md, downloads-forticnapp-terraform-references-modules-gcp-gar-md, downloads-forticnapp-terraform-references-modules-gcp-gcr-md, downloads-forticnapp-terraform-references-modules-gcp-gke-audit-log-md, downloads-forticnapp-terraform-references-modules-aws-iam-role-md, downloads-forticnapp-terraform-references-modules-oci-iam-user-md, downloads-forticnapp-terraform-references-modules-azure-microsoft-entra-id-activity-log-md, downloads-forticnapp-terraform-references-modules-aws-org-configuration-md, downloads-forticnapp-terraform-references-modules-gcp-pub-sub-audit-log-md, downloads-forticnapp-terraform-references-modules-aws-s3-data-export-md, downloads-forticnapp-terraform-references-modules-aws-security-hub-outbound-md, downloads-forticnapp-terraform-references-modules-gcp-service-account-md, downloads-forticnapp-terraform-references-modules-aws-ssm-agent-md, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-540226-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-0c78cd-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-2400cf-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-c9342e-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-1f12c8-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-938a8a-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-435912-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-571b1f-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-f682ee-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-a381e3-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-d375f6-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-bf8721-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-465b9f-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-48dff3-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-69aa8d-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-27b8b2-txt]
updated: 2026-10-14
status: needs-review
---

# Terraform

Lacework/FortiCNAPP Terraform modules and provider auth.

## Scope

This page indexes **82** source documents routed to this topic.

## Synthesized content

The Lacework/FortiCNAPP Terraform ecosystem is two artifacts: the `lacework/lacework` **provider** (currently `v2.6.1`, partner tier, published 2026-09-23) that exposes custom resources for the FortiCNAPP control plane, and a catalog of ~32 cloud-side **modules** on the Terraform Registry under the `lacework` namespace that wire AWS, Azure, GCP, Kubernetes and OCI accounts into those resources [src: lacework-terraform-reference.md]. The manual Terraform path (hand-written `main.tf`) is reserved for complex scenarios or source-controlled, repeatable infrastructure-as-code deployments; wizard-style **Guided Configuration** and the FortiCNAPP CLI generators cover most common integrations [src: 01-overview-and-modules.md, cnapp_tf.md].

### Prerequisites

Supported Terraform versions are the latest `1.x` plus the prior three minor versions; `~> 0.14` and `~> 0.15` also work for most provider scenarios [src: 01-overview-and-modules.md]. You need FortiCNAPP administrator privileges, cloud administrator credentials (AWS Account Admin, Azure Global Admin/Owner, GCP Owner), and — strongly recommended — the FortiCNAPP CLI installed so the provider can reuse its `~/.lacework.toml` credentials [src: 01-overview-and-modules.md, 03-getting-started.md].

### Provider authentication

The provider supports three auth methods, in order of preference [src: 03-getting-started.md, lacework-terraform-reference.md]:

1. **CLI config file (recommended)** — `~/.lacework.toml` (or `%USERPROFILE%\.lacework.toml` on Windows), selected with `provider "lacework" { profile = "..." }` or `LW_PROFILE`.
2. **Environment variables** — `LW_ACCOUNT`, `LW_API_KEY`, `LW_API_SECRET` (or short-lived `LW_API_TOKEN`), plus `LW_SUBACCOUNT` and `LW_ORGANIZATION`. Setting account/key/secret overrides `LW_PROFILE`.
3. **Static credentials** — inline `account`, `api_key`, `api_secret` in the provider block (discouraged; leaks easily via VCS) [src: 03-getting-started.md].

API keys are created in the console under **Settings > Configuration > API keys** and downloaded as a JSON file containing `keyId`, `secret`, `subAccount`, and `account` [src: 03-getting-started.md]. For organizations, aliased provider blocks with `subaccount = "..."` switch between accounts, and `organization = true` grants org-level access (ignoring `subaccount`) [src: 03-getting-started.md, lacework-terraform-reference.md]. Pin provider versions with pessimistic constraints such as `version = "~> 1.15"` to accept bug fixes while blocking breaking majors [src: 03-getting-started.md].

### Module index

The registry publishes modules for each cloud, each paired with the matching provider resource (e.g. `lacework_integration_aws_cfg`, `_aws_ct`, `_azure_cfg`, `_gcp_cfg`, `_oci_cfg`) [src: lacework-terraform-reference.md].

| Module | Cloud | Purpose |
|---|---|---|
| `lacework/iam-role/aws` | AWS | Cross-account IAM role (shared by other modules) |
| `lacework/config/aws` | AWS | Configuration / CSPM integration |
| `lacework/cloudtrail/aws` | AWS | CloudTrail log ingestion |
| `lacework/cloudtrail-controltower/aws` | AWS | CloudTrail analysis for Control Tower orgs |
| `lacework/eks-audit-log/aws` | AWS | EKS audit log collection |
| `lacework/agentless-scanning/aws` | AWS | Agentless workload scanning |
| `lacework/dspm/aws` | AWS | Data Security Posture Management |
| `lacework/ecr/aws` | AWS | Amazon ECR registry integration |
| `lacework/ecs-agent/aws` | AWS | FortiCNAPP agent ECS task/daemon |
| `lacework/ssm-agent/aws` | AWS | SSM-based agent deployment to EC2 |
| `lacework/org-configuration/aws` | AWS | Organization-level config rollout |
| `lacework/alerts-to-s3/aws` | AWS | Export alerts to S3 via EventBridge |
| `lacework/s3-data-export/aws` | AWS | Data export to S3 |
| `lacework/security-hub-outbound/aws` | AWS | Send findings to AWS Security Hub |
| `lacework/ad-application/azure` | Azure | AD app registration for integrations |
| `lacework/config/azure` | Azure | Configuration / CSPM integration |
| `lacework/activity-log/azure` | Azure | Activity log ingestion |
| `lacework/microsoft-entra-id-activity-log/azure` | Azure | Entra ID activity log |
| `lacework/agentless-scanning/azure` | Azure | Agentless scanning |
| `lacework/dspm/azure` | Azure | DSPM |
| `lacework/service-account/gcp` | GCP | Service account for integrations |
| `lacework/config/gcp` | GCP | Configuration / CSPM |
| `lacework/audit-log/gcp` | GCP | Audit log ingestion |
| `lacework/pub-sub-audit-log/gcp` | GCP | Pub/Sub audit log |
| `lacework/gke-audit-log/gcp` | GCP | GKE audit log |
| `lacework/agentless-scanning/gcp` | GCP | Agentless scanning |
| `lacework/gar/gcp` | GCP | Artifact Registry |
| `lacework/gcr/gcp` | GCP | Container Registry |
| `lacework/admission-controller/kubernetes` | Kubernetes | Admission controller |
| `lacework/agent/kubernetes` | Kubernetes | FortiCNAPP agent (DaemonSet) |
| `lacework/config/oci` | OCI | Configuration / CSPM |
| `lacework/iam-user/oci` | OCI | IAM user for integrations |

[src: 01-overview-and-modules.md, cnapp_tf.md, lacework-terraform-reference.md]

### Single-role vs multi-role deployment

Each module is standalone and, by default, provisions its own cross-account IAM role — so applying several modules independently creates several roles [src: 04-single-role-deployment.md]. The recommended AWS pattern is the **single-role deployment**: call `lacework/iam-role/aws` once at the root, then pass `use_existing_iam_role = true` with `iam_role_external_id` and `iam_role_name` (and `iam_role_arn` where the module requires it) into `config`, `cloudtrail`, `ecr`, `ecs-agent`, `eks-audit-log`, and `agentless-scanning` [src: 04-single-role-deployment.md, 01-overview-and-modules.md]. The agentless-scanning module instead uses `use_existing_cross_account_role` with `cross_account_role_name`/`cross_account_role_arn`/`external_id` and runs with `global = true` and/or `regional = true` to separate per-account resources from per-region ones [src: 04-single-role-deployment.md]. Multi-role deployment — one module, one role — is the fallback for simple single-service integrations or when roles must be isolated for blast-radius reasons.

### Maintenance and upgrade patterns

Because FortiCNAPP continuously adds new datasources that require new cloud permissions, the symptom of a stale integration is `CSPAccessDeniedError` [src: 01-overview-and-modules.md, 06-maintain-cloud-integrations.md]. Re-running the latest Terraform script applies the new permissions. Two maintenance workflows apply (currently supported for `AwsCfg` only) [src: 06-maintain-cloud-integrations.md]:

- **Adopt an existing integration into Terraform** — gather the cloud account GUID, external ID, role ARN, role name, and integration name with `lacework cloud-accounts list` / `lacework cloud-account show <GUID>`, write a `module "aws_config"` block with `use_existing_iam_role = true` and those values, then run `terraform init -upgrade`, `terraform import module.aws_config.lacework_integration_aws_cfg.default <GUID>`, `terraform plan`, `terraform apply` [src: 06-maintain-cloud-integrations.md].
- **Update a module already under Terraform** — bump the module `version` constraint, review the README for breaking changes on major jumps, then `terraform init -upgrade && terraform plan && terraform apply`; minor-version bumps need no code change under a `~>` constraint [src: 06-maintain-cloud-integrations.md, 03-getting-started.md].

### Verbatim reference set (from the forticnapp-terraform skill)

The skill's 46 reference files are preserved under `skills/forticnapp/references/terraform/`: 12 Administration Guide pages (`admin-guide/01` to `12`, covering overview, getting started, single-role deployment, maintaining integrations, alert channels, profiles and rules, resource groups, DSPM), a module index with versions, a provider-auth page, and one file per module (`modules/<cloud>-<module>.md`) [src: skill-forticnapp-terraform]. Versions were captured 2026-10-13 and must be confirmed on the registry before pinning [src: skill-forticnapp-terraform]. Provider authentication prefers a CLI profile, then environment variables (`LW_ACCOUNT`, `LW_API_KEY`, `LW_API_SECRET` or `LW_API_TOKEN`, `LW_PROFILE`, `LW_SUBACCOUNT`, `LW_ORGANIZATION`), then static credentials; sub-accounts use aliased providers (`subaccount = "name"`) and organization-level resources use `organization = true`, which needs the Organization Administrator role [src: skill-forticnapp][src: skill-forticnapp-terraform].

## Sources

- [Appendix D - Terraform for FortiCNAPP](../../sources/downloads-forticnapp-terraform-references-admin-guide-02-appendix-d-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/02-appendix-d.md`
- [Configuring alert profiles with Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-08-alert-profiles-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/08-alert-profiles.md`
- [Getting started with Terraform for FortiCNAPP](../../sources/downloads-forticnapp-terraform-references-admin-guide-03-getting-started-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/03-getting-started.md`
- [Integration using Terraform](../../sources/downloads-cnapp-tf-md.md) — `/Users/svuillaume/Downloads/cnapp_tf.md`
- [Integration using Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-01-overview-and-modules-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/01-overview-and-modules.md`
- [Lacework (FortiCNAPP) Terraform Provider — Authentication & Features](../../sources/downloads-forticnapp-terraform-references-provider-auth-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/provider-auth.md`
- [Lacework (FortiCNAPP) Terraform Reference — Provider Authentication and All 32 Modules](../../sources/downloads-lacework-terraform-reference-md.md) — `/Users/svuillaume/Downloads/lacework-terraform-reference.md`
- [Lacework / FortiCNAPP Terraform Modules (registry.terraform.io, namespace `lacework`)](../../sources/downloads-forticnapp-terraform-references-module-index-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/module-index.md`
- [Lacework OCI integration](../../sources/scriptsv2-0-lw-oci-integration-readme-md.md) — `/Users/svuillaume/scriptsv2.0/lw-oci-integration/README.md`
- [Lacework Provider](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-8453a6-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-8453a6.txt`
- [lacework/activity-log/azure 4.1.0](../../sources/downloads-forticnapp-terraform-references-modules-azure-activity-log-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/azure-activity-log.md`
- [lacework/ad-application/azure 2.0.1](../../sources/downloads-forticnapp-terraform-references-modules-azure-ad-application-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/azure-ad-application.md`
- [lacework/alerts-to-s3/aws 0.4.2](../../sources/downloads-forticnapp-terraform-references-modules-aws-alerts-to-s3-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-alerts-to-s3.md`
- [lacework/audit-log/gcp 4.0.3](../../sources/downloads-forticnapp-terraform-references-modules-gcp-audit-log-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-audit-log.md`
- [lacework/cloudtrail-controltower/aws 0.5.1](../../sources/downloads-forticnapp-terraform-references-modules-aws-cloudtrail-controltower-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-cloudtrail-controltower.md`
- [lacework/cloudtrail/aws 2.11.0](../../sources/downloads-forticnapp-terraform-references-modules-aws-cloudtrail-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-cloudtrail.md`
- [lacework/config/aws 0.26.0](../../sources/downloads-forticnapp-terraform-references-modules-aws-config-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-config.md`
- [lacework/config/azure 3.1.0](../../sources/downloads-forticnapp-terraform-references-modules-azure-config-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/azure-config.md`
- [lacework/config/gcp 3.2.5](../../sources/downloads-forticnapp-terraform-references-modules-gcp-config-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-config.md`
- [lacework/config/oci 0.5.1](../../sources/downloads-forticnapp-terraform-references-modules-oci-config-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/oci-config.md`
- [lacework/ecr/aws 0.9.3](../../sources/downloads-forticnapp-terraform-references-modules-aws-ecr-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-ecr.md`
- [lacework/eks-audit-log/aws 1.2.0](../../sources/downloads-forticnapp-terraform-references-modules-aws-eks-audit-log-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-eks-audit-log.md`
- [lacework/gar/gcp 0.4.7](../../sources/downloads-forticnapp-terraform-references-modules-gcp-gar-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-gar.md`
- [lacework/gcr/gcp 2.3.8](../../sources/downloads-forticnapp-terraform-references-modules-gcp-gcr-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-gcr.md`
- [lacework/gke-audit-log/gcp 0.6.4](../../sources/downloads-forticnapp-terraform-references-modules-gcp-gke-audit-log-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-gke-audit-log.md`
- [lacework/iam-role/aws 0.4.5](../../sources/downloads-forticnapp-terraform-references-modules-aws-iam-role-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-iam-role.md`
- [lacework/iam-user/oci 0.3.4](../../sources/downloads-forticnapp-terraform-references-modules-oci-iam-user-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/oci-iam-user.md`
- [lacework/microsoft-entra-id-activity-log/azure 0.5.0](../../sources/downloads-forticnapp-terraform-references-modules-azure-microsoft-entra-id-activity-log-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/azure-microsoft-entra-id-activity-log.md`
- [lacework/org-configuration/aws 1.1.6](../../sources/downloads-forticnapp-terraform-references-modules-aws-org-configuration-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-org-configuration.md`
- [lacework/pub-sub-audit-log/gcp 0.6.2](../../sources/downloads-forticnapp-terraform-references-modules-gcp-pub-sub-audit-log-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-pub-sub-audit-log.md`
- [lacework/s3-data-export/aws 1.3.4](../../sources/downloads-forticnapp-terraform-references-modules-aws-s3-data-export-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-s3-data-export.md`
- [lacework/security-hub-outbound/aws 0.2.0](../../sources/downloads-forticnapp-terraform-references-modules-aws-security-hub-outbound-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-security-hub-outbound.md`
- [lacework/service-account/gcp 2.0.3](../../sources/downloads-forticnapp-terraform-references-modules-gcp-service-account-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-service-account.md`
- [lacework/ssm-agent/aws 1.0.2](../../sources/downloads-forticnapp-terraform-references-modules-aws-ssm-agent-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-ssm-agent.md`
- [lacework\_fortidspm\_deployment\_status](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-540226-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-540226.txt`
- [lacework\_integration\_aws\_agentless\_scanning](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-0c78cd-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-0c78cd.txt`
- [lacework\_integration\_aws\_cfg](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-2400cf-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-2400cf.txt`
- [lacework\_integration\_aws\_ct](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-c9342e-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-c9342e.txt`
- [lacework\_integration\_aws\_eks\_audit\_log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-1f12c8-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-1f12c8.txt`
- [lacework\_integration\_aws\_fortidspm](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-938a8a-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-938a8a.txt`
- [lacework\_integration\_aws\_org\_agentless\_scanning](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-435912-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-435912.txt`
- [lacework\_integration\_azure\_ad\_al](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-571b1f-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-571b1f.txt`
- [lacework\_integration\_azure\_al](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-f682ee-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-f682ee.txt`
- [lacework\_integration\_azure\_cfg](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-a381e3-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-a381e3.txt`
- [lacework\_integration\_azure\_fortidspm](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-d375f6-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-d375f6.txt`
- [lacework\_integration\_gcp\_agentless\_scanning](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-bf8721-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-bf8721.txt`
- [lacework\_integration\_gcp\_cfg](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-465b9f-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-465b9f.txt`
- [lacework\_integration\_gcp\_gke\_audit\_log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-48dff3-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-48dff3.txt`
- [lacework\_integration\_gcp\_pub\_sub\_audit\_log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-69aa8d-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-69aa8d.txt`
- [lacework\_integration\_oci\_cfg](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-27b8b2-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-27b8b2.txt`
- [Maintain cloud integrations with Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-06-maintain-cloud-integrations-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/06-maintain-cloud-integrations.md`
- [Manage alert channels with Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-07-alert-channels-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/07-alert-channels.md`
- [Manage alert rules with Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-09-alert-rules-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/09-alert-rules.md`
- [Manage cloud integrations with Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-05-manage-cloud-integrations-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/05-manage-cloud-integrations.md`
- [Managing resource groups with Terraform](../../sources/downloads-forticnapp-terraform-references-admin-guide-10-resource-groups-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/10-resource-groups.md`
- [Raw Githubusercontent Com Lacework Terraform Provider Lacewo 43A652](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-provider-lacewo-43a652-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-provider-lacewo-43a652.txt`
- [Readme](../../sources/scriptsv2-0-lw-oci-integration-tf-module-readme-md.md) — `/Users/svuillaume/scriptsv2.0/lw-oci-integration/tf_module/README.md`
- [Readme](../../sources/scriptsv2-0-aws-system-manager-readme-md.md) — `/Users/svuillaume/scriptsv2.0/AWS-System-Manager/README.md`
- [Single role Terraform deployment](../../sources/downloads-forticnapp-terraform-references-admin-guide-04-single-role-deployment-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/admin-guide/04-single-role-deployment.md`
- [Terraform Integrations for AWS, Azure, GCP and OCI](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-operations-terraform-integrations-overview-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/operations/terraform-integrations-overview.md`
- [Terraform Modules for Configuration (CSPM) Integrations and Access Identities](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-operations-terraform-config-and-access-modules-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/operations/terraform-config-and-access-modules.md`
- [Terraform Provider for Lacework / FortiCNAPP](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-operations-terraform-provider-lacework-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/operations/terraform-provider-lacework.md`
- [terraform-<PROVIDER>-<NAME>](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-config-cont-06d3e9-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-config-cont-06d3e9.txt`
- [terraform-aws-cloudtrail](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-cloudtrail-b31e7e-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-cloudtrail--b31e7e.txt`
- [terraform-aws-cloudtrail-controltower](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-cloudtrail-13d9b0-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-cloudtrail--13d9b0.txt`
- [terraform-aws-config](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-config-main-6bb806-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-config-main-6bb806.txt`
- [terraform-aws-eks-audit-log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-eks-audit-l-853a79-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-eks-audit-l-853a79.txt`
- [terraform-aws-iam-role](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-iam-role-ma-d1de5c-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-iam-role-ma-d1de5c.txt`
- [terraform-aws-org-configuration](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-org-configu-067842-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-org-configu-067842.txt`
- [terraform-azure-activity-log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-azure-activity-e10a06-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-azure-activity--e10a06.txt`
- [terraform-azure-ad-application](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-azure-ad-applic-d9111d-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-azure-ad-applic-d9111d.txt`
- [terraform-azure-config](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-azure-config-ma-fa39b8-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-azure-config-ma-fa39b8.txt`
- [terraform-azure-microsoft-entra-id-activity-log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-azure-microsoft-eca9ef-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-azure-microsoft-eca9ef.txt`
- [terraform-gcp-config](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-gcp-config-main-ea77d3-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-gcp-config-main-ea77d3.txt`
- [terraform-gcp-gke-audit-log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-gcp-gke-audit-l-6e5ae3-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-gcp-gke-audit-l-6e5ae3.txt`
- [terraform-gcp-pub-sub-audit-log](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-gcp-pub-sub-aud-2f0a9a-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-gcp-pub-sub-aud-2f0a9a.txt`
- [terraform-gcp-service-account](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-gcp-service-acc-a76701-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-gcp-service-acc-a76701.txt`
- [terraform-oci-config](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-oci-config-main-48b7df-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-oci-config-main-48b7df.txt`
- [📦 Azure Terraform Resource Inventory](../../sources/downloads-readme-4-md.md) — `/Users/svuillaume/Downloads/README_4.md`
- [🔐 FortiCNAPP Terraform Provider — Authentication Guide](../../sources/downloads-readme-1-md.md) — `/Users/svuillaume/Downloads/README_1.md`
- [🖥️ Running `tf2html.sh` from Another Computer or Terminal](../../sources/downloads-tf2html-simple-steps-md.md) — `/Users/svuillaume/Downloads/tf2html-simple-steps.md`
- [🖥️ Running `tf2html.sh` from Another Computer or Terminal](../../sources/downloads-tf2html-simple-steps-1-md.md) — `/Users/svuillaume/Downloads/tf2html-simple-steps_1.md`
