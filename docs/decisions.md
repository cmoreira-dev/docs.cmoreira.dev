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
| Onde vive a IaC | Cloud e cluster em repositórios separados, dois modelos de execução | Um repositório de fundação; `bootstrap/` manual e o resto automatizado | O executor da LAN é um ponto de falha para *mudar* a infra |
| Módulos de IaC | Código misturado com valores do ambiente e sem versões | Um repositório por módulo, versionado por tag; as unidades só têm configuração | Mais repositórios para manter |
| Quando aplicar | Um apply no cluster mexe em nós; um apply na cloud, não | O raio de impacto decide o portão: o seguro aplica-se após o merge, o resto por um passo humano com plano visível antes | Alguns changes precisam de dois cliques |
| O que o CI executa | Rodar tudo a cada PR é lento e esconde o que mudou | Só as unidades alteradas, descobertas pelo ficheiro alterado | Um seletor próprio para manter |
| Canal de chat | Uma interface simples para pessoas e para avisos | Servidor de chat aberto e auto-hospedado, com app comum no celular | Mais um serviço para manter; salas com bot sem criptografia ponta a ponta |
| Mensageiros comerciais | Um grupo com bot no app de uso diário | Só a API oficial; ponte não oficial descartada | Sem esse mensageiro enquanto não houver uma conta empresarial verificada |
| Modelo por tarefa | Modelo local é barato, mas fraco com ferramentas | Hospedado pequeno para agentes com ferramentas; local para resumo e dados pessoais | Custo por token nos agentes |
| Acesso remoto aos agentes | O controlador não tem autenticação própria | Identidade na borda mais validação do token no túnel | Duas camadas para configurar e renovar |
