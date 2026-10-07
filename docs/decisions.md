# Decisões

Formato: contexto, escolha, custo.

| Decisão | Escolha | Custo aceito |
|---|---|---|
| Como entregar | GitOps com reconciliação contínua | Raio de impacto grande em addons compartilhados |
| Autenticação do CI | OIDC federado, sem chaves | Depende da cloud estar acessível no build |
| Segredos | Cofre gerenciado + operador no cluster | Dependência de runtime do cofre |
| Distribuição do cluster | Sistema imutável, gerido por API | Curva de aprendizado; sem SSH para "dar um jeito" |
| Ingress | Gateway API sobre um túnel de borda | Menos opções prontas que o Ingress clássico |
| IaC | Dois níveis com fronteiras disjuntas | Dois modos de operar Terraform |
| Dependências | Renovate org-wide; majors tratados como projeto | Major bumps nunca são automáticos |
| Complexidade | Remover componentes que não pagam o custo | Menos funcionalidades "de catálogo" |
