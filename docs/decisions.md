---
description: "Decisões de arquitetura com contexto, escolha e custo aceito."
---

# Decisões

Formato: contexto, escolha, custo aceito.

| Decisão | Contexto | Escolha | Custo aceito |
|---|---|---|---|
| Como entregar | Vários apps num cluster, operados por uma pessoa | GitOps com reconciliação contínua | Raio de impacto grande em addons compartilhados |
| Autenticação do CI | Pipelines precisam falar com a cloud sem chaves guardadas | OIDC federado, sem chaves | Depende da cloud estar acessível no build |
| Segredos | Apps precisam de valores sensíveis sem eles irem para o Git | Cofre gerenciado + operador no cluster | Dependência de runtime do cofre |
| Distribuição do cluster | Poucos nós, sem tempo para manter um SO tradicional | Sistema imutável, gerido por API | Curva de aprendizado; sem SSH para "dar um jeito" |
| Ingress | Nenhuma porta aberta no roteador de casa | Gateway API sobre um túnel de borda | Menos opções prontas que o Ingress clássico |
| IaC | Fundação compartilhada e recursos que pertencem a cada app | Dois níveis com fronteiras disjuntas | Dois modos de operar Terraform |
| Dependências | Muitos repositórios, atualizações constantes | Renovate org-wide; majors tratados como projeto | Major bumps nunca são automáticos |
| Complexidade | Operador único: cada componente tem custo de manutenção | Remover o que não paga o custo | Menos funcionalidades "de catálogo" |
