---
title: Cwpp
summary: Workload protection: agent, AWLS (agentless), container, Kubernetes runtime.
sources: [user-paste-kubernetes-cluster-name-2026-10-21, user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-agent-vs-agentless-collection-md, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-agentless-workload-scanning-md, tmp-forticnapp-notes-awls-azure-tenant-single-region-readme-md, tmp-terraform-azure-agentless-scanning-preflight-check-readme-md, tmp-terraform-azure-agentless-scanning-examples-tenant-multi-region-readme-md, tmp-terraform-azure-agentless-scanning-contributing-md, tmp-terraform-azure-agentless-scanning-developer-guidelines-md, downloads-cspm-awls-md, tmp-personal-project-new-wiki-llm-wiki-raw-docs-fortinet-com-document-forticnapp-latest-administration-384984-txt, tmp-lw-cloudinit-forticnapp-notes-lw-agent-ecs-agent-md, tmp-forticnapp-notes-lw-agent-ecs-agent-md, tmp-personal-project-new-wiki-llm-wiki-wiki-operations-platform-overview-data-in-insights-out-md, tmp-personal-project-new-wiki-assets-forticnapp-scan-md, downloads-forticnapp-scan-md, my-workspace-lacework-tf-lw-agentless-wk-scanning-readme-md, tmp-personal-project-new-wiki-llm-wiki-raw-github-com-lacework-terraform-aws-agentless-scanning-release-ebb915-txt, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-kspm-md, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-kubernetes-admission-control-md, downloads-lw-forticnapp-main-readme-md, tmp-personal-project-new-wiki-llm-wiki-wiki-updates-2026-10-11-aws-agentless-scanning-v0-19-0-md, tmp-lw-cloudinit-forticnapp-notes-awls-azure-subs-single-region-awls-azure-md, tmp-forticnapp-notes-awls-azure-subs-single-region-awls-azure-md, tmp-lacework-feature-usage-report-txt, my-workspace-docker-scan-readme-md, downloads-lacework-monitoring-plaintext-txt, downloads-forticnapp-terraform-references-modules-kubernetes-admission-controller-md, downloads-forticnapp-terraform-references-modules-kubernetes-agent-md, downloads-forticnapp-terraform-references-modules-aws-agentless-scanning-md, downloads-forticnapp-terraform-references-modules-azure-agentless-scanning-md, downloads-forticnapp-terraform-references-modules-gcp-agentless-scanning-md, downloads-forticnapp-terraform-references-modules-aws-ecs-agent-md, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-kubernetes-hardening-fortinet-reference-md, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-oracle-kubernetes-engine-oke-md, tmp-personal-project-new-wiki-llm-wiki-wiki-threats-polygraph-v2-graph-neural-network-detection-md, tmp-terraform-azure-agentless-scanning-github-pull-request-template-md, tmp-terraform-azure-agentless-scanning-examples-custom-vnet-readme-md, tmp-terraform-azure-agentless-scanning-examples-subscription-single-region-readme-md, tmp-terraform-azure-agentless-scanning-examples-subscription-multi-region-readme-md, tmp-terraform-azure-agentless-scanning-release-notes-md, tmp-terraform-azure-agentless-scanning-examples-tenant-single-region-readme-md, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-agentless-s-d82df4-txt, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-azure-agentless-deab01-txt, tmp-terraform-azure-agentless-scanning-readme-md, tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-gcp-agentless-s-54a6b2-txt, tmp-terraform-azure-agentless-scanning-changelog-md, tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-cwpp-runtime-vulnerability-md, forticnapp-wiki-forticnapp-techtip-polygraph-faq-html, forticnapp-wiki-html-forticnapp-techtip-polygraph-faq-html, user-chat-kubernetes-compliance-integration-2026-10-21, user-chat-linux-agent-kubernetes-install-2026-10-21]
updated: 2026-10-21
status: needs-review
---

# Cwpp

Workload protection: agent, AWLS (agentless), container, Kubernetes runtime.

## Scope

This page indexes **52** source documents routed to this topic.

## Synthesized content

FortiCNAPP's CWPP capability combines **four complementary mechanisms** — host/container agents, Agentless Workload Scanning (AWLS), Kubernetes-aware runtime, and the Polygraph behavior model — to protect running workloads across AWS, Azure, and GCP. Agent and agentless are described as complementary rather than mutually exclusive [src: platform-overview-data-in-insights-out].

### Agent-based protection

The agent delivers real-time, host-level telemetry: processes, network activity, user changes, and file-system changes [src: platform-overview-data-in-insights-out]. It runs on Linux and Windows hosts, as a Kubernetes DaemonSet, or as a sidecar in AWS ECS Fargate [src: platform-overview-data-in-insights-out]. In the AWS monitoring model it is listed as providing real-time ingestion with real-time evaluation and host-level detections [src: lw_forticnapp-main-README].

Operational characteristics (both Windows v1.5+ and Linux):
- Typical disk footprint ~250 MB; RAM <50 MB (Windows) / ~36 MB (Linux); CPU <1% [src: lw_forticnapp-main-README].
- Minimum host 1 vCPU (2 recommended), 2 GB RAM (4 recommended), 5–10 GB free disk [src: lw_forticnapp-main-README].
- Auto-upgrade is on by default for Windows v1.5+ and for Linux from v7.6+; it can be disabled by MSI flag or `config.json` [src: lw_forticnapp-main-README].
- Behavioral baselining, threat-intel updates, and custom-policy push (CLI/API) are supported on both OSes; policy changes do not require an agent upgrade or restart [src: lw_forticnapp-main-README].

### Kubernetes cluster name discovery and missing clusters

FortiCNAPP can read a `KubernetesCluster` machine tag or the `KubernetesCluster` agent tag in `config.json`. If neither is available, it attempts to extract a name from an agent-data key such as `k8s.io/cluster-autoscaler/newprod.k8s.local:true`. Without these naming inputs, the cluster name does not display in the Kubernetes dashboard; an inactive cluster during the selected time window can also be absent. [src: user-paste-kubernetes-cluster-name-2026-10-21]

The supplied documentation recommends machine tags where supported and agent tags for self-built clusters. Ensure the agent can access cloud tags/metadata. Set the explicit name through Helm's `laceworkConfig.kubernetesCluster`, the ConfigMap's `config.json` tag, or the Kubernetes agent Terraform module's `lacework_cluster_name`; the Terraform name should match the cloud provider name. Updating the corresponding setting changes the reported name. [src: user-paste-kubernetes-cluster-name-2026-10-21]

**Source issues — needs review:** the paste's first JSON example misses a quote, its full Helm example omits the subcommand, and its instruction to apply a configuration change with `terraform apply -refresh-only` requires technical verification. These examples are preserved in the source stub and are not endorsed as runnable instructions. [src: user-paste-kubernetes-cluster-name-2026-10-21]

### Installing the agent on Kubernetes

The Linux agent runs on Kubernetes through four methods: Helm chart (recommended, from the `lacework` charts repo), DaemonSet (configmap or secret), Terraform (`lacework/agent/kubernetes`), or gVisor. It supports Kubernetes 1.9.x to 1.35 across AKS, EKS, GKE, OpenShift, Rancher and similar platforms, and runs privileged with host PID, network and volume access [src: user-chat-linux-agent-kubernetes-install-2026-10-21].

Set the cluster name through the `KubernetesCluster` machine tag on managed clusters, or the `KubernetesCluster` tag in `config.json` on self-built clusters. Agent data takes 10 to 15 minutes to appear under Agents, and the cluster appears under Workloads > Kubernetes [src: user-chat-linux-agent-kubernetes-install-2026-10-21]. The same DaemonSet can also carry the compliance collectors described above, so an existing agent install can add compliance without a second deployment [src: user-chat-kubernetes-compliance-integration-2026-10-21].

Helm settings cover tolerations, resource requests and limits, proxy URL, FIM, package and process scan, command-line filtering, and perfmode. The doc's Terraform snippet pins `lacework/agent/kubernetes` at `~> 1.0`, which conflicts with the 2.x module described in the stub below [src: user-chat-linux-agent-kubernetes-install-2026-10-21][src: downloads-forticnapp-terraform-references-modules-kubernetes-agent-md]. The doc also gives two different Kubernetes ranges (1.9.x to 1.35 and v1.10 to v1.30 for Helm) and two different chart-version ranges, so treat version support as unresolved.

### Agentless Workload Scanning (AWLS)

AWLS scans disks/snapshots on EC2, Azure VMs, and GCP Compute Engine every 12–24 hours (configurable), detecting OS-package and language-library vulnerabilities, secrets (SSH keys, cloud access keys, Kubernetes config), hardcoded credentials, and malware; it also discovers containers on scanned hosts [src: lw_forticnapp-main-README][src: platform-overview-data-in-insights-out]. Scans trigger alerts after completion [src: lw_forticnapp-main-README].

Deployment is Terraform-driven. The Azure module (`lacework/agentless-scanning/azure` 1.6.2) deploys a Container App Job runner, a NAT gateway, a Key Vault for Lacework credentials, a scanning storage account, and dedicated role definitions, under either `SUBSCRIPTION` or `TENANT` integration levels [src: azure-agentless-scanning]. Toggles cover `scan_host_vulnerabilities`, `scan_containers`, `scan_stopped_instances`, `scan_multi_volume`, `scan_frequency_hours`, and `filter_query_text` (an LQL query that constrains which resources are scanned) [src: azure-agentless-scanning]. Deprovisioning while a scan is in flight can orphan scanner VMs — the Azure README documents the `az vm delete` recovery step [src: terraform-azure-agentless-scanning-README].

The GCP module (`lacework/agentless-scanning/gcp` 2.1.8) uses Cloud Run Jobs plus Cloud Scheduler, Secret Manager, custom project/org IAM roles, and a GCS bucket, at `PROJECT` or `ORGANIZATION` scope [src: gcp-agentless-scanning]. The same host/container/stopped-instance toggles are exposed, and `bucket_lifecycle_rule_age` defaults to 30 days [src: gcp-agentless-scanning].

### Container & Kubernetes runtime

Kubernetes coverage layers posture, runtime, and admission:
- The DaemonSet agent provides node and container monitoring [src: platform-overview-data-in-insights-out].
- An audit-log integration (Terraform) watches the API layer [src: platform-overview-data-in-insights-out].
- A CIS cluster collector assesses configuration; findings appear under Compliance > Kubernetes and snapshots are queryable in LQL [src: platform-overview-data-in-insights-out].
- A `ValidatingAdmissionWebhook` scans images before they run, alongside Pod Security Admission enforcement [src: kubernetes-hardening-fortinet-reference].
- Registry/CI scanning covers ECR, Azure Container Registry, and GCP Artifact Registry; an admission controller can block images from entering a cluster [src: platform-overview-data-in-insights-out][src: lw_forticnapp-main-README].

### Kubernetes compliance integration

Kubernetes compliance monitors configuration against CIS EKS 1.1.0 and CIS GKE 1.4.0 benchmarks. It covers Amazon EKS and GKE Standard only; EKS Fargate and GKE Autopilot are unsupported [src: user-chat-kubernetes-compliance-integration-2026-10-21].

Three collectors feed it. The Node Collector runs as a DaemonSet on every node and reports hourly. The Cluster Collector runs as one non-root pod per cluster, reads the Kubernetes API with get/list rights, and reports every 24 hours. The Cloud Collector is the existing Configuration integration, which runs daily [src: user-chat-kubernetes-compliance-integration-2026-10-21]. Full collection needs all three to have run at least once. Data usually appears within 2 hours of install, and Compliance Changed alerts start after two evaluations [src: user-chat-kubernetes-compliance-integration-2026-10-21].

Install with Helm or the `lacework/agent/kubernetes` Terraform module. The cluster name in the install must match the provider's cluster name, or the console shows Partial collection [src: user-chat-kubernetes-compliance-integration-2026-10-21]. On EKS clusters with KIAM or similar proxies, pod metadata requests can be blocked, which causes EC2MetadataError and Partial collection [src: user-chat-kubernetes-compliance-integration-2026-10-21].

### Polygraph behavior model

Polygraph is the core behavioral engine: a time-based model that maps users, machines, containers, APIs, and their interactions to establish a baseline and detect deviations [src: lw_forticnapp-main-README]. It consumes CloudTrail, GCP/Azure audit logs, flow logs, and agent telemetry, evaluates continuously / event-driven, and triggers immediate alerts on deviation across AWS, Azure, and GCP [src: lw_forticnapp-main-README]. **Polygraph Exposure** is a visual layer built directly on top of the Polygraph that highlights internet-exposed assets using the same behavioral data plus CSP APIs and exposure metadata [src: lw_forticnapp-main-README]. In the Exposure Polygraph, alerts combine agent and agentless context — vulnerabilities, compliance violations, secrets, internet exposure — for investigation [src: platform-overview-data-in-insights-out].


### Release updates, Jul–Oct 2026 (newly ingested)

- **Polygraph v2** (July 2026, GA): graph-based anomaly alerts, described as a graph neural network over identities, actions, resources and source IPs. The earlier Polygraph v2 source stub (vendor description, single source) holds the detail. `(src: user-upload-forticnapp-news-releases-jul-oct-2026-2026-10-15)`
- **Agentless dashboard** (August 2026, GA). The source gives no further detail.
- **Vulnerability assessment** (September 2026): Google Container-Optimized OS (agent 8.4.0+ and Agentless), and Ubuntu 25.04 to 26.10 hosts, which may cause a spike in findings after the first feed update.
- **Risk score adjustment** (September 2026) when a FortiGate or other NGFW is detected inline.

### Composite Alerts and the feedback loop (newly ingested, 2026-10-16)

- Composite Alerts evaluate many signals at once rather than one rule or IOC: threat behaviors (access-control bypass, privilege escalation), IOCs from curated feeds, and anomalies (global, per-institution, or per-user/system/workload). Inputs can be rules, anomaly models or behavioral baselines, and are normalized into one scoring engine. `(src: user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16)`
- Signals play one of three roles: **decisive** (can justify an alert alone), **combinatorial** (predictive only with others), **contextual** (forensics only). `(src: user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16)`
- **False-positive feedback:** when closing a Composite Alert the user can label it true positive (confirmed threat or pen test) or false positive (benign behavior misclassified), and can report false negatives. Labels join a training corpus that retrains the scoring models; signals are Boolean or numeric, so the post says no customer-specific content enters training. `(src: user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16)`
- **Release gating:** nightly tests measure precision (TP/(TP+FP)) and recall (TP/(TP+FN)) on labeled scenarios, plus alert rate on recent unlabeled telemetry; precision, recall and alert-volume thresholds are formal release criteria. `(src: user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16)`
- Scope note: the post is about Composite Alert scoring and does not name Polygraph. How it relates to the Polygraph baseline above, and what a false-positive label does to a single tenant's alerts immediately, are not stated in the source. The source gives no numeric results; the 95% false-positive reduction in the Polygraph FAQ is a separate Forrester-study claim.

## Sources

- [Agent vs Agentless Data Collection](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-agent-vs-agentless-collection-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/agent-vs-agentless-collection.md`
- [Agentless Workload Scanning (AWLS) on AWS, Azure and GCP](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-agentless-workload-scanning-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/agentless-workload-scanning.md`
- [AWLS in Azure – Terraform Deployment Guide](../../sources/tmp-forticnapp-notes-awls-azure-tenant-single-region-readme-md.md) — `/Users/svuillaume/tmp/FortiCNAPP-Notes/awls-azure-tenant_single_region/README.md`
- [Azure Agentless Workload Scanner Preflight Check](../../sources/tmp-terraform-azure-agentless-scanning-preflight-check-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/preflight_check/README.md`
- [Azure Cloud Tenant-Level for Multiple Regions](../../sources/tmp-terraform-azure-agentless-scanning-examples-tenant-multi-region-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/examples/tenant-multi-region/README.md`
- [Contributing to the Lacework Terraform Modules](../../sources/tmp-terraform-azure-agentless-scanning-contributing-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/CONTRIBUTING.md`
- [Create the Lacework application within Azure Active Directory to grant](../../sources/tmp-terraform-azure-agentless-scanning-developer-guidelines-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/DEVELOPER_GUIDELINES.md`
- [Cspm+Awls](../../sources/downloads-cspm-awls-md.md) — `/Users/svuillaume/Downloads/cspm+awls.md`
- [Docs Fortinet Com Document Forticnapp Latest Administration  384984](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-docs-fortinet-com-document-forticnapp-latest-administration-384984-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/docs-fortinet-com-document-forticnapp-latest-administration--384984.txt`
- [Ecs Agent](../../sources/tmp-lw-cloudinit-forticnapp-notes-lw-agent-ecs-agent-md.md) — `/Users/svuillaume/tmp/lw_cloudinit/FortiCNAPP-Notes/lw_agent/ecs-agent.md`
- [Ecs Agent](../../sources/tmp-forticnapp-notes-lw-agent-ecs-agent-md.md) — `/Users/svuillaume/tmp/FortiCNAPP-Notes/lw_agent/ecs-agent.md`
- [FortiCNAPP Platform Overview: Data In, Insights Out, Who Uses It](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-operations-platform-overview-data-in-insights-out-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/operations/platform-overview-data-in-insights-out.md`
- [Forticnapp Scan](../../sources/tmp-personal-project-new-wiki-assets-forticnapp-scan-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/assets/forticnapp_scan.md`
- [Forticnapp Scan](../../sources/downloads-forticnapp-scan-md.md) — `/Users/svuillaume/Downloads/forticnapp_scan.md`
- [forticnapp_agentless_scanning](../../sources/my-workspace-lacework-tf-lw-agentless-wk-scanning-readme-md.md) — `/Users/svuillaume/my_workspace/lacework_tf/lw_agentless_wk_scanning/README.md`
- [Github Com Lacework Terraform Aws Agentless Scanning Release Ebb915](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-github-com-lacework-terraform-aws-agentless-scanning-release-ebb915-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/github-com-lacework-terraform-aws-agentless-scanning-release-ebb915.txt`
- [KSPM (Kubernetes Security Posture Management)](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-kspm-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/kspm.md`
- [Kubernetes Admission Control](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-kubernetes-admission-control-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/kubernetes-admission-control.md`
- [FortiCNAPP Kubernetes compliance integration (user-pasted docs)](../../sources/user-chat-kubernetes-compliance-integration-2026-10-21.md) — chat paste, 2026-10-21
- [Install Linux Agent on Kubernetes (user-pasted docs)](../../sources/user-chat-linux-agent-kubernetes-install-2026-10-21.md) — chat paste, 2026-10-21
- [Lacework Agent Comparison: Windows vs Linux](../../sources/downloads-lw-forticnapp-main-readme-md.md) — `/Users/svuillaume/Downloads/lw_forticnapp-main/README.md`
- [Lacework AWS agentless scanning module: v0.19.0](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-updates-2026-10-11-aws-agentless-scanning-v0-19-0-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/updates/2026-10-11-aws-agentless-scanning-v0-19-0.md`
- [Lacework Azure Agentless Scanning Deployment - AWLS](../../sources/tmp-lw-cloudinit-forticnapp-notes-awls-azure-subs-single-region-awls-azure-md.md) — `/Users/svuillaume/tmp/lw_cloudinit/FortiCNAPP-Notes/awls-azure-subs_single_region/awls-azure.md`
- [Lacework Azure Agentless Scanning Deployment - AWLS](../../sources/tmp-forticnapp-notes-awls-azure-subs-single-region-awls-azure-md.md) — `/Users/svuillaume/tmp/FortiCNAPP-Notes/awls-azure-subs_single_region/awls-azure.md`
- [Lacework Feature Usage Report](../../sources/tmp-lacework-feature-usage-report-txt.md) — `/Users/svuillaume/tmp/lacework_feature_usage_report.txt`
- [Lacework FortiCNAPP – Demos & Use Cases](../../sources/my-workspace-docker-scan-readme-md.md) — `/Users/svuillaume/my_workspace/docker_scan/README.md`
- [Lacework Monitoring Plaintext](../../sources/downloads-lacework-monitoring-plaintext-txt.md) — `/Users/svuillaume/Downloads/lacework_monitoring_plaintext.txt`
- [lacework/admission-controller/kubernetes 0.1.3](../../sources/downloads-forticnapp-terraform-references-modules-kubernetes-admission-controller-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/kubernetes-admission-controller.md`
- [lacework/agent/kubernetes 2.5.2](../../sources/downloads-forticnapp-terraform-references-modules-kubernetes-agent-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/kubernetes-agent.md`
- [lacework/agentless-scanning/aws 0.19.0](../../sources/downloads-forticnapp-terraform-references-modules-aws-agentless-scanning-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-agentless-scanning.md`
- [lacework/agentless-scanning/azure 1.6.2](../../sources/downloads-forticnapp-terraform-references-modules-azure-agentless-scanning-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/azure-agentless-scanning.md`
- [lacework/agentless-scanning/gcp 2.1.8](../../sources/downloads-forticnapp-terraform-references-modules-gcp-agentless-scanning-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/gcp-agentless-scanning.md`
- [lacework/ecs-agent/aws 0.5.3](../../sources/downloads-forticnapp-terraform-references-modules-aws-ecs-agent-md.md) — `/Users/svuillaume/Downloads/forticnapp-terraform/references/modules/aws-ecs-agent.md`
- [Managed Kubernetes Hardening (AKS / GKE / OKE) with Fortinet](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-kubernetes-hardening-fortinet-reference-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/kubernetes-hardening-fortinet-reference.md`
- [Oracle Kubernetes Engine (OKE) Security](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-oracle-kubernetes-engine-oke-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/oracle-kubernetes-engine-oke.md`
- [Polygraph v2: Graph Neural Network Cloud Threat Detection](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-threats-polygraph-v2-graph-neural-network-detection-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/threats/polygraph-v2-graph-neural-network-detection.md`
- [Pull Request Template](../../sources/tmp-terraform-azure-agentless-scanning-github-pull-request-template-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/.github/pull-request-template.md`
- [Readme](../../sources/tmp-terraform-azure-agentless-scanning-examples-custom-vnet-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/examples/custom-vnet/README.md`
- [Readme](../../sources/tmp-terraform-azure-agentless-scanning-examples-subscription-single-region-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/examples/subscription-single-region/README.md`
- [Readme](../../sources/tmp-terraform-azure-agentless-scanning-examples-subscription-multi-region-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/examples/subscription-multi-region/README.md`
- [Release Notes](../../sources/tmp-terraform-azure-agentless-scanning-release-notes-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/RELEASE_NOTES.md`
- [Single tenant Example](../../sources/tmp-terraform-azure-agentless-scanning-examples-tenant-single-region-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/examples/tenant-single-region/README.md`
- [terraform-aws-agentless-scanning](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-aws-agentless-s-d82df4-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-aws-agentless-s-d82df4.txt`
- [terraform-azure-agentless-scanning](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-azure-agentless-deab01-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-azure-agentless-deab01.txt`
- [terraform-azure-agentless-scanning](../../sources/tmp-terraform-azure-agentless-scanning-readme-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/README.md`
- [terraform-gcp-agentless-scanning](../../sources/tmp-personal-project-new-wiki-llm-wiki-raw-raw-githubusercontent-com-lacework-terraform-gcp-agentless-s-54a6b2-txt.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/raw/raw-githubusercontent-com-lacework-terraform-gcp-agentless-s-54a6b2.txt`
- [v1.6.2](../../sources/tmp-terraform-azure-agentless-scanning-changelog-md.md) — `/Users/svuillaume/tmp/terraform-azure-agentless-scanning/CHANGELOG.md`
- [Workload Protection and Runtime Vulnerability Context (CWPP)](../../sources/tmp-personal-project-new-wiki-llm-wiki-wiki-cloud-security-cwpp-runtime-vulnerability-md.md) — `/Users/svuillaume/tmp/personal_project/new_wiki/llm_wiki/wiki/cloud-security/cwpp-runtime-vulnerability.md`
- [FortiCNAPP - AI-Driven Data](../../sources/forticnapp-wiki-forticnapp-techtip-polygraph-faq-html.md) — `/Users/svuillaume/forticnapp-wiki/FortiCNAPP-TechTip-Polygraph-FAQ.html`
- [FortiCNAPP - AI-Driven Data](../../sources/forticnapp-wiki-html-forticnapp-techtip-polygraph-faq-html.md) — `/Users/svuillaume/forticnapp-wiki/html/FortiCNAPP-TechTip-Polygraph-FAQ.html`
- [How Feedback Loops and Machine Learning Power High-Precision Intrusion Detection](../../sources/user-upload-fortinet-blog-feedback-loops-intrusion-detection-2026-10-16.md) — `chat upload 781cf743-attachment.txt`

## Synthesized catalog

| Document | Summary | Source |
|---|---|---|
| [FortiCNAPP - AI-Driven Data](../../sources/forticnapp-wiki-forticnapp-techtip-polygraph-faq-html.md) | **Summary:** Using Artificial Intelligence to continuously turn cloud log activity into relevant and actionable security insights. | `/Users/svuillaume/forticnapp-wiki/FortiCNAPP-TechTip-Polygraph-FAQ.html` |
| [FortiCNAPP - AI-Driven Data](../../sources/forticnapp-wiki-html-forticnapp-techtip-polygraph-faq-html.md) | **Summary:** Using Artificial Intelligence to continuously turn cloud log activity into relevant and actionable security insights. | `/Users/svuillaume/forticnapp-wiki/html/FortiCNAPP-TechTip-Polygraph-FAQ.html` |

- [How FortiCNAPP derives the K8s cluster name](../../sources/user-paste-kubernetes-cluster-name-2026-10-21.md) — user-supplied documentation, 2026-10-21; source issues flagged.
