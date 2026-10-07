---
description: "High-level notes on a homelab platform run with production practices: patterns, decisions and lessons."
---

# Homelab platform: how and why

High-level notes on a personal platform run with production practices: real Kubernetes, infrastructure as
code, GitOps and pipelines with no static credentials.

This site shows **patterns, decisions with trade-offs and lessons learned**. The technical detail of each
component (configuration, endpoints, runbooks, roadmap) lives next to the code, in private repositories.

## In one picture

```mermaid
flowchart TB
    dev["Developer"] -- "PR + merge" --> git["Git repositories"]
    git -- "CI: image build" --> reg["Image registry"]
    git -- "desired state" --> argo["GitOps controller"]
    argo -- "reconciles" --> k8s["Kubernetes cluster"]
    reg -. "pull" .-> k8s
    cloud["Cloud: identity and secrets"] -. "OIDC / secrets" .-> k8s
    user["User"] --> edge["Edge (tunnel, no open ports)"] --> k8s
```

## Where to start

- **[Architecture](architecture/index.md)**: the layers and how they relate.
- **[Decisions](decisions.md)**: what was chosen, what was left out and what each choice costs.
- **[Lessons learned](lessons.md)**: what broke or surprised.
- **[Case studies](case-studies/computer-vision.md)**: real applications, described abstractly.

## Principles

- **Everything declarative.** Git is the only source of desired state.
- **No long-lived credentials.** Federated identity in CI and secrets injected at runtime.
- **Convention over configuration.** A repository's name already says what it does.
- **Docs next to the code.** Each repository documents itself; this site summarizes what is worth sharing.
