---
title: "FortiCNAPP Kubernetes compliance integration (user-pasted docs)"
path: "chat paste 2026-10-21 (no file, no URL)"
url: "none"
topic: cwpp
updated: unknown
ingested: 2026-10-21
sha1: none (inline chat text, no file)
status: current
evidence: vendor-documentation
---

**Source:** FortiCNAPP product documentation pasted by the user in chat, covering core integration concepts and the Kubernetes compliance integration (Node Collector, Cluster Collector, Cloud Collector). No publication date or URL was given. The paste repeated the same text twice; ingested once.

**Topic:** [[cwpp]]

## Key facts

- Integration types: Configuration (CSPM, identity risk), Audit logs (CloudTrail, Azure Activity Logs, GCP Audit Logs, and EKS/GKE Kubernetes audit logs), Agentless Workload Scanning, DSPM (AWS and Azure only, configured via Terraform/CLI). Integration methods: automated (recommended), cloud provider templates, guided (deprecated), CLI, Terraform, manual.
- Kubernetes compliance integration monitors CIS EKS 1.1.0 and CIS GKE 1.4.0 configuration compliance. Supported: Amazon EKS and GKE (Standard). Not supported: EKS Fargate and GKE Autopilot. Kubernetes v1.10+ and Helm v3.1+.
- Three collectors feed the data: Node Collector (DaemonSet on every node, runs hourly, sends within 2 hours of install, pods named `lacework-agent-*`); Cluster Collector (one pod per cluster, non-root, read-only get/list ClusterRole, runs every 24 hours, pod named `lacework-agent-cluster-*`); Cloud Collector (the Configuration integration, daily at the Resource Management Collection Schedule).
- Full collection needs all three to have run at least once. Console collection status reads Full, Partial, or No collection.
- Prerequisites: a Linux agent access token (a new token is recommended if only compliance is wanted); an existing AWS Configuration integration (EKS) or Google Cloud Configuration integration (GKE); AWS CLI or gcloud configured.
- EKS audit logging must be enabled per cluster (`aws eks update-cluster-config ... audit`) for the audit-log integration.
- Install paths: Helm (`lacework/lacework-agent` chart; compliance-only sets `laceworkConfig.datacollector=disable`), or Terraform module `lacework/agent/kubernetes` ~> 2.0 with `lacework_cluster_exclusive` for compliance-only. `laceworkConfig.kubernetesCluster` (or `lacework_cluster_name`) must match the cluster name in the cloud provider, or the console shows Partial collection.
- Troubleshooting: check Node Collector logs for config parse errors and for `k8sNodeCollector is enabled`; check Cluster Collector logs for `Completed discovery` and `Collection status OK`, and for `Sending` lines with `collectionStatusType` STARTED/COMPLETED and empty `errorMessage`. On EKS with KIAM or similar, metadata requests from pods can be blocked, causing EC2MetadataError and Partial collection; set `clusterAgent.hostNetworkAccess=true` if the IMDS hop limit is 1.
- Compliance Changed alerts need at least two full evaluations, usually under 48 hours after integration. New Violations can appear after the first evaluation.

## Not captured

Helm and Terraform parameter tables were summarised, not copied in full. Optional parameters (`clusterAgent.proxyUrl`, image tags) are noted only by name. The pasted text had no images. The doc's agent version requirement and the Kubernetes Compliance FAQ link targets were not provided.
