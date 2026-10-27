---
title: Deploying RCA on Kubernetes
path: /Users/svuillaume/tmp/personal_project/new_cnapp_ui/cnapp_rca/rca_ui/k8s/README.md
topic: rapid-cloud-assessment
updated: 2026-09-02
size: 19727
sha1: 9a2cffdae3d0
status: current
---

**Original path:** `/Users/svuillaume/tmp/personal_project/new_cnapp_ui/cnapp_rca/rca_ui/k8s/README.md`

**Topic:** [[rapid-cloud-assessment]]

## Summary (first paragraph of source)

Manifests live in [`k8s/`](k8s/). No Ingress, no cert-manager — exposed via a **NodePort** Service with a self-signed TLS cert, single replica only.
