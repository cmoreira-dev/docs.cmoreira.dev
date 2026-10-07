---
description: "The platform's four layers (provisioning, cluster, delivery, applications) and how they relate."
---

# Architecture overview

The platform has four layers, each with one clear tool and owner.

| Layer | Responsibility | Tool (type) |
|---|---|---|
| Provisioning | Cloud resources and VMs | Terraform/Terragrunt |
| Cluster | Operating system and Kubernetes | Immutable, API-driven distribution |
| Delivery | Getting Git state into the cluster | GitOps controller (Argo CD) |
| Applications | Each app's code and image | Per-repository CI |

Compute is hybrid: the cluster runs on owned hardware, and what is worth managed (image registry, IaC state,
secret storage) lives in the cloud.

```mermaid
flowchart TB
    iac["IaC: provisions cloud and VMs"] --> cluster["Kubernetes cluster"]
    gitops["GitOps controller"] -- "reconciles continuously" --> cluster
    repos["gitops.* repositories"] --> gitops
    cloud["Cloud: registry, state, secrets"] -. "federated identity" .-> cluster
```

**Golden rule:** only the delivery layer changes cluster state. Provisioning and bootstrap are triggered
manually; from the GitOps controller onwards everything is continuously reconciled and any drift is reverted.

Patterns in detail: [GitOps](gitops-pattern.md), [identity and secrets](identity-and-secrets.md),
[two-tier IaC](two-tier-iac.md).
