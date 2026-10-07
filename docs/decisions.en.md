---
description: "Architecture decisions with context, choice and accepted cost."
---

# Decisions

Format: context, choice, accepted cost.

| Decision | Context | Choice | Cost accepted |
|---|---|---|---|
| How to deliver | Several apps on one cluster, run by one person | GitOps with continuous reconciliation | Large blast radius on shared addons |
| CI authentication | Pipelines must reach the cloud without stored keys | Federated OIDC, no keys | Needs the cloud reachable at build time |
| Secrets | Apps need sensitive values without them landing in Git | Managed store + in-cluster operator | Runtime dependency on the store |
| Cluster distribution | Few nodes, no time to maintain a traditional OS | Immutable, API-managed OS | Learning curve; no SSH to "just fix it" |
| Ingress | No open ports on the home router | Gateway API over an edge tunnel | Fewer ready-made options than classic Ingress |
| IaC | Shared foundation plus resources owned by each app | Two tiers with disjoint boundaries | Two ways to operate Terraform |
| Dependencies | Many repositories, constant updates | Org-wide Renovate; majors treated as projects | Major bumps are never automatic |
| Complexity | Single operator: every component has a maintenance cost | Remove what doesn't pay for itself | Fewer "catalog" features |
