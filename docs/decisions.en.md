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
| Where IaC lives | Cloud and cluster in separate repositories, two execution models | One foundation repository; manual `bootstrap/` and everything else automated | The LAN executor is a point of failure for *changing* the infra |
| IaC modules | Code mixed with environment values, no versions | One repository per module, versioned by tag; units hold configuration only | More repositories to maintain |
| When to apply | A cluster apply touches nodes; a cloud apply does not | Blast radius decides the gate: the safe applies after merge, the rest by a human step with the plan visible first | Some changes need two clicks |
| What CI runs | Running everything on every PR is slow and hides what changed | Only the changed units, found from the changed file | A custom selector to maintain |
| Chat channel | A simple interface for people and for notices | Open, self-hosted chat server with an ordinary phone app | One more service to maintain; rooms with a bot aren't end-to-end encrypted |
| Commercial messengers | A group with a bot in the everyday app | Official API only; unofficial bridge dropped | No such messenger until there's a verified business account |
| Model per task | A local model is cheap but weak with tools | Small hosted model for agents with tools; local for summaries and personal data | Per-token cost on the agents |
| Remote access to the agents | The controller has no authentication of its own | Identity at the edge plus token validation at the tunnel | Two layers to configure and renew |
