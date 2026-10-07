---
description: "Naming convention: a repository's prefix says its type and how it is operated."
---

# Repository naming

The prefix says the repository's type and how it is operated.

| Prefix | Type |
|---|---|
| `gitops.*` | GitOps workload (auto-discovered) |
| `iac.*` | Live infrastructure state |
| `api.*` | Backend |
| `ui.*` | Frontend |
| `docs.*` | Documentation |

Do not invent new prefixes without updating the convention. Each repository documents itself in its own `docs/`.
