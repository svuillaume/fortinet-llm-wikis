---
title: "Install Linux Agent on Kubernetes (user-pasted docs)"
path: "chat paste 2026-10-21 (no file, no URL)"
url: "none"
topic: cwpp
updated: unknown
ingested: 2026-10-21
sha1: none (inline chat text, no file)
status: current
evidence: vendor-documentation
---

**Source:** FortiCNAPP product documentation pasted by the user in chat, covering installation of the Linux agent on Kubernetes by Helm, DaemonSet (configmap or secret), Terraform, and gVisor. No publication date or URL was given. The paste repeated the same text twice; ingested once.

**Topic:** [[cwpp]]

## Key facts

- Four install methods: Helm chart (recommended via the `lacework` charts repo), DaemonSet (any cluster, including AKS, EKS, GKE), Terraform (`terraform-kubernetes-agent` module), and gVisor (GKE Sandbox or containerd).
- Agent data appears in the console under Agents after 10 to 15 minutes. The cluster appears under Workloads > Kubernetes > Clusters. The datacollector pod runs privileged and needs host PID, network and volume access.
- Cluster name: set the `KubernetesCluster` machine tag on managed clusters (AKS, EKS, GKE), or set the `KubernetesCluster` tag in `config.json` for self-built clusters. The Helm `laceworkConfig.kubernetesCluster` value is shown as optional in this doc.
- Supported: Kubernetes 1.9.x to 1.35 (orchestrators AKS, EKS, EKS Fargate, GKE, MicroK8s, OpenShift, Rancher, ROSA; CNIs Weave, Calico, Flannel, Cilium, kubenet; Linkerd 2.11; Docker, containerd, CRI-O). ECS Fargate is listed.
- Helm install (North America): `helm upgrade --install --namespace lacework --create-namespace` with `laceworkConfig.accessToken`, `kubernetesCluster`, `env`, and chart `lacework/lacework-agent`. Outside North America, also set `laceworkConfig.serverUrl`.
- Helm chart from release tarball: chart v4.2 needs `version: 4.2.0.218` changed to `4.2.0` in Chart.yaml. The charts repo method does not need this edit.
- Helm options documented: container runtime and endpoint, tolerations (all nodes or subset), priorityClassCreate, CPU/memory requests and limits (defaults 200m/500m CPU, 512Mi/1450Mi memory), proxyUrl, FIM settings (enable, filePath, fileIgnore, noAtime, runAt, crawlInterval with 1320-minute default), active package detection (`codeaware.enable` all/experimental/false), package scan and process scan toggles and intervals, cmdlinefilter allow/disallow, image pull secrets, existing access-token secret, AWS metadata request interval, annotations, labels, tags, perfmode (ebpflite, lite, scan), stdout logging.
- Specific chart version installs: `--version` matches agent version (example chart 6.2.0). The chart repo table in the doc lists 5.5.2 to 6.2.0.
- OpenShift: install with cluster-admin, or with a service account after `oc adm policy add-scc-to-user privileged -z <sa>` and `laceworkConfig.serviceAccountName`.
- DaemonSet deployment: (a) configmap method applies `lacework-cfg-k8s.yaml` then `lacework-k8s.yaml` in namespace `lacework`; (b) secret method changes configMap to secret and `name` to `secretName`, creates secret `lacework-config` with `config.json` holding the access token, server URL and `KubernetesCluster` tag, then applies `lacework-k8s.yaml`. Config changes use `kubectl replace`.
- Terraform: `lacework/agent/kubernetes` module, version `~> 1.0` in the snippet, with `lacework_access_token`, `lacework_server_url` (EU and ANZ examples), `lacework_agent_tags = {KubernetesCluster = ...}`, and pod CPU/memory settings. Module 1.0+ dropped hashicorp/kubernetes 1.x; pin to `~> 0.1` if needed.
- gVisor: DaemonSet needs nodeAffinity on `sandbox.gke.io/runtime=gvisor` and a matching toleration. Install steps are the same as the DaemonSet method.
- Validation: `kubectl get pods -n lacework -o wide`, `kubectl get ds`, or `kubectl get pods -l name=lacework -o=wide --all-namespaces` for the Terraform/DaemonSet label.

## Not captured

Full parameter tables and the gVisor containerd configuration file were summarised. The Helm chart tarball contents were listed only by name. Images: none in the paste.
