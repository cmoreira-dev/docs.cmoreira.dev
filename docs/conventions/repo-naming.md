# Nomes de repositórios

O prefixo diz o tipo do repositório e como ele é operado.

| Prefixo | Tipo |
|---|---|
| `gitops.*` | Workload GitOps (descoberto automaticamente) |
| `iac.*` | Estado vivo de infraestrutura |
| `api.*` | Backend |
| `ui.*` | Frontend |
| `docs.*` | Documentação |

Não inventar prefixos novos sem atualizar a convenção. Cada repositório documenta a si mesmo no próprio `docs/`.
