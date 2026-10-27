---
title: "How FortiCNAPP derives the K8s cluster name"
path: "/Users/svuillaume/.codex/attachments/c333a896-994b-4ae8-92e1-ff31f952b2a8/Pasted text.txt"
url: "https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name"
topic: cwpp
updated: unknown
source_modified_utc: "2026-10-21T23:37:33.981866+00:00"
ingested: 2026-10-21
sha1: d41072d44c0ed1a03103dac27cf3902a081ed37f
status: needs-review
evidence: user-pasted-vendor-documentation
---

## Provenance

User-supplied Markdown text, attributed to the linked FortiCNAPP administration guide. The live documentation was not fetched; this entry describes the supplied version. The original attachment is unchanged. No matching content hash or prior stub for this document was found.

## Key facts from the supplied source

- FortiCNAPP can derive the cluster name from a `KubernetesCluster` machine tag or from the `KubernetesCluster` agent tag in `config.json`.
- If neither tag is available, the agent attempts to derive the name from an agent-data key such as `k8s.io/cluster-autoscaler/newprod.k8s.local:true`; the example name is `newprod.k8s.local`.
- A missing name or a cluster inactive during the dashboard's selected time window can explain an absent cluster.
- The source recommends machine tags where supported, with agent access to cloud metadata/tags. AWS and Google Cloud access configuration is linked; Azure access is described as automatic.
- For self-built clusters, the source recommends the agent configuration tag. Helm exposes it through `laceworkConfig.kubernetesCluster`; ConfigMap deployments put it in `data.config.json` and update the ConfigMap with `kubectl replace -f lacework-cfg-k8s.yaml -n lacework`.
- The Kubernetes agent Terraform module exposes `lacework_cluster_name` within `lacework_k8s_datacollector`; the value should match the cloud provider's cluster name.
- To change the reported name, update the corresponding Helm value, ConfigMap agent tag, or Terraform module variable.

## Review flags

- The first JSON example is malformed: it omits the opening quote on `KubernetesCluster`. The later ConfigMap examples include that quote.
- The full Helm example begins `helm --install` without the `install` or `upgrade` subcommand. Preserve as a source issue; do not copy as a runnable command.
- The source says `terraform apply -refresh-only` applies a module configuration change. Flag for technical verification before use; do not treat the pasted instruction as a validated deployment step.
- No new contradiction with the existing CWPP synthesis was found. Existing installation-source Terraform module version conflicts remain unresolved.

## Extraction limits

All supplied text was readable. The machine-tag section refers to an example after “the following tag” but supplies no tag image/table; that example cannot be recovered from the paste. No external pages, linked content, or images were fetched.

## Full supplied text

# How FortiCNAPP derives the K8s cluster name
When you deploy the FortiCNAPP agent in your Kubernetes (K8s) environment, the list of K8s clusters in which the agent is deployed displays in the [Kubernetes Dashboard](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/255093/kubernetes-dashboard) in the FortiCNAPP console.

This topic describes how FortiCNAPP derives the K8s cluster name, what you can do if the cluster name does not appear in the FortiCNAPP console, and how you can modify the cluster name that appears in the FortiCNAPP console.

## How FortiCNAPP derives the cluster name

Depending on your K8s environment and distribution, FortiCNAPP uses multiple methods to derive the cluster name.
1. If your K8s orchestrator supports machine tags, you can add a machine tag named KubernetesCluster for your cluster. FortiCNAPP can derive the cluster name from the machine tag. See [Add KubernetesCluster Machine Tag](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name#add-kubernetescluster-machine-tag-recommended).
2. The FortiCNAPP agent can also read the cluster name from its local config.json file if it is specified using the KubernetesCluster agent tag, as shown in the following example. For more information, see [Set KubernetesCluster Agent Tag in config.json File](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name#set-kubernetescluster-agent-tag-in-config-json-file).
   ```
   {
       "tokens":{"AccessToken":"YourAgentAccessToken"},
       "serverurl":"LaceworkServerURL", 
       "tags":{"Env":"k8s",KubernetesCluster":"prod.k8s.local"}
   }
   
   ```
3. When using the [Lacework Kubernetes Agent Terraform module](https://registry.terraform.io/modules/lacework/agent/kubernetes/latest), the Kubernetes cluster name can be set explicitly with the following variable in the lacework_k8s_datacollector module:
   ```
   lacework_cluster_name = "my-k8s-cluster"
   
   ```
   This should match the name defined in your cloud provider environment. For example, [list your Amazon Elastic K8s Service (EKS) clusters to discover the relevant name](https://docs.aws.amazon.com/cli/latest/reference/eks/list-clusters.html#examples).
4. If your K8s orchestrator does not have the KubernetesCluster machine tag and your config.json file does not have the KubernetesCluster agent tag, FortiCNAPP attempts to locate a key in the agent data set that resembles k8s.io/cluster-autoscaler/newprod.k8s.local:true to derive the cluster name. In this example, newprod.k8s.local is the cluster name.
5. If the machine tag, agent tag, or agent data set key is not available, the cluster name does not display in the [Kubernetes Dashboard](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/255093/kubernetes-dashboard) in the FortiCNAPP console.

## What should I do if a cluster does not display in the FortiCNAPP console?

A K8s cluster may not display in the K8s dashboard in the FortiCNAPP console if:
- The FortiCNAPP agent cannot read the cluster name in your K8s environment. See [How Lacework derives the cluster name](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name#how-lacework-derives-the-cluster-name).
- The cluster was not active during the time window you selected in the K8s dashboard in the FortiCNAPP console.
If a cluster is active, you can do one of the following to display the cluster name in the Kubernetes dashboard:
- [Add KubernetesCluster machine tag (recommended)](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name#add-kubernetescluster-machine-tag-recommended)
- [Set KubernetesCluster agent tag in config.json file](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name#set-kubernetescluster-agent-tag-in-config-json-file).
- [Set the lacework_cluster_name variable in the Lacework Kubernetes agent Terraform module](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/354468/how-forticnapp-derives-the-k8s-cluster-name#set-the-lacework-cluster-name-variable-in-the-lacework-kubernetes-agent-terraform-module).

## Add KubernetesCluster machine tag (recommended)

If your K8s orchestrator supports machine tags, do the following:
To add KubernetesCluster machine tag:
1. Add a machine tag named KubernetesCluster on your cluster and specify the cluster name as the tag value. For example, add the following tag on your EKS cluster using the instructions at [Tagging Your Amazon EKS Resources](https://docs.aws.amazon.com/eks/latest/userguide/eks-using-tags.html).
   
2. Ensure that the FortiCNAPP agent has access to the tags in your K8s orchestrator.
   - To provide access to tags on AWS, see [Configuring access to tags and metadata in AWS](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/853182/configuring-access-to-tags-and-metadata-in-aws).
   - To provide access to labels on Google Cloud, see [Configuring access to labels in Google Cloud](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/957128/configuring-access-to-labels-in-google-cloud).
   - The agent can automatically access tags on Microsoft Azure. Hence, no special configuration is required for Microsoft Azure.
We recommend this method because it enables the agent to automatically obtain the cluster name from your K8s orchestrator.

## Set KubernetesCluster Agent Tag in config.json File

You can set the KubernetesCluster agent tag in the config.json agent configuration file by doing any of the following. We recommend this method if you have built your own Kubernetes cluster rather than utilizing EKS, AKS, GKE, or similar orchestrator.
- If you use the FortiCNAPP Helm chart to deploy the agent, use the following option with the helm install or helm upgrade command:
  ```
  --set laceworkConfig.kubernetesCluster=YourClusterName
  
  ```
  ```
  helm --install --namespace lacework --create-namespace \
  --set laceworkConfig.accessToken=LACEWORK_AGENT_TOKEN \
  --set laceworkConfig.serverUrl=LACEWORK_SERVER_URL \
  --set laceworkConfig.kubernetesCluster=YourClusterName \
  lacework-agent lacework/lacework-agent
  
  ```
  For more information about using the FortiCNAPP Helm chart, see [Installing using Helm](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/663510/installing-linux-agent-on-kubernetes#install-using-helm).
- If you use the lacework-cfg-k8s.yaml configmap file to deploy the agent, do the following:
  1. Specify the cluster name using the KubernetesCluster tag in the config.json section of the lacework-cfg-k8s.yaml file as shown below:
     ```
     apiVersion: v1
     kind: ConfigMap
     metadata:
         name: lacework-config
     data:
         config.json: |
           {
             "tokens":{"AccessToken":"YourAgentAccessToken"},
             "serverurl":"LaceworkServerURL",
             "tags":{"Env":"k8s", "KubernetesCluster":"YourClusterName"}
           }
     
     ```
  2. Push the updated lacework-cfg-k8s.yaml file to the cluster.
     ```
     kubectl replace -f lacework-cfg-k8s.yaml -n lacework
     
     ```
  For more information about using the lacework-cfg-k8s.yaml configmap file, see [Deploying with a DaemonSet](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/663510/installing-linux-agent-on-kubernetes#deploy-with-a-daemonset).

## Set the lacework_cluster_name Variable in the Lacework Kubernetes Agent Terraform Module

When using the [Lacework Kubernetes Agent Terraform module](https://registry.terraform.io/modules/lacework/agent/kubernetes/latest), the Kubernetes cluster name can be set explicitly with the following variable in the lacework_k8s_datacollector module:
```
lacework_cluster_name = "my-k8s-cluster"

```
The name should match the name defined in your cloud provider environment. For example, [list your Amazon EKS clusters to discover the relevant cluster name](https://docs.aws.amazon.com/cli/latest/reference/eks/list-clusters.html#examples).

## How Can I Modify a Cluster Name in the FortiCNAPP console

FortiCNAPP allows you to change the cluster name reported by the FortiCNAPP agent in the [Kubernetes Dashboard](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/255093/kubernetes-dashboard) in the FortiCNAPP console.
- If you use the FortiCNAPP Helm chart to deploy the agent, use the following option with the helm install or helm upgrade command:
  ```
  --set laceworkConfig.kubernetesCluster=YourClusterName
  
  ```
  For more information about using the FortiCNAPP Helm chart, see [Installing using Helm](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/663510/installing-linux-agent-on-kubernetes#install-using-helm).
- If you use the lacework-cfg-k8s.yaml configmap file to deploy the agent, do the following:
  1. Specify the cluster name using the KubernetesCluster tag in the config.json section of the lacework-cfg-k8s.yaml file as shown below:
     ```
     apiVersion: v1
     kind: ConfigMap
     metadata:
         name: lacework-config
     data:
         config.json: |
          {
             "tokens":{"AccessToken":"YourAgentAccessToken"},
             "serverurl":"LaceworkServerURL",
             "tags":{"Env":"k8s", "KubernetesCluster":"YourClusterName"}
          }
     
     ```
  2. Push the updated lacework-cfg-k8s.yaml file to the cluster.
     ```
     kubectl replace -f lacework-cfg-k8s.yaml -n lacework
     
     ```
  For more information about using the lacework-cfg-k8s.yaml configmap file, see [DaemonSet deployment using a configmap](https://docs.fortinet.com/document/forticnapp/latest/administration-guide/663510/installing-linux-agent-on-kubernetes#daemonset-deployment-using-a-configmap).
- If you use the [Lacework Kubernetes Agent Terraform module](https://registry.terraform.io/modules/lacework/agent/kubernetes/latest), add the following variable to your main.tf file within the lacework_k8s_datacollector module:
  ```
  module "lacework_k8s_datacollector" {
      ...
      # This should match the name defined in your cloud provider environment.
      lacework_cluster_name   = "my-k8s-cluster"
  }
  
  ```
  You would then need to re-run terraform apply -refresh-only to apply the change ([check that your version of Terraform supports this command](https://developer.hashicorp.com/terraform/cli/commands/refresh#usage) before running).
