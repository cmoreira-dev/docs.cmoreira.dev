---
description: "Why the cluster runs on an immutable, API-managed operating system, and what that costs."
---

# Immutable-OS cluster

The Kubernetes cluster runs on **Talos Linux**: an OS with no shell, no SSH and no package manager, configured
entirely through a declarative API.

```mermaid
flowchart LR
    cfg["Declarative node config"] --> api["OS API"]
    api --> node["Node (immutable)"]
    node --> k8s["Kubernetes"]
```

## What changes in operations

- **Nodes are cattle, not pets.** To change a node you change its config and apply it; you don't log in.
- **Same image, different hardware.** The cluster mixes small ARM boards and one x86 machine with a GPU, all managed
  the same way.
- **Extensions go into the image**, not manual installs. GPU drivers, for example, are system extensions chosen
  when the image is built.

## Trade-offs

- (+) Smaller attack surface and reproducible node state.
- (+) OS upgrades are an API operation, with rollback.
- (−) No SSH to "just fix it": every diagnosis goes through the API and logs.
- (−) A learning curve and some VM-specific details (interface names, firmware) you only learn once.
- (−) Slow storage on small nodes demands discipline: write-heavy workloads stay off them.
