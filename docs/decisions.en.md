# Decisions

Format: context, choice, cost.

| Decision | Choice | Cost accepted |
|---|---|---|
| How to deliver | GitOps with continuous reconciliation | Large blast radius on shared addons |
| CI authentication | Federated OIDC, no keys | Needs the cloud reachable at build time |
| Secrets | Managed store + in-cluster operator | Runtime dependency on the store |
| Cluster distribution | Immutable, API-managed OS | Learning curve; no SSH to "just fix it" |
| Ingress | Gateway API over an edge tunnel | Fewer ready-made options than classic Ingress |
| IaC | Two tiers with disjoint boundaries | Two ways to operate Terraform |
| Dependencies | Org-wide Renovate; majors treated as projects | Major bumps are never automatic |
| Complexity | Remove components that don't pay for themselves | Fewer "catalogue" features |
