# Política de documentação pública

## Modelo

1. **Cada repositório é dono da sua documentação técnica detalhada**: arquitetura, diagramas, runbooks,
   configuração, endpoints, decisões, backlog e roadmap. Fica no `docs/` do repositório, junto do código.
2. **Este site é só alto nível:** padrões, decisões com trade-offs, lições e diagramas genéricos. Produtos
   aparecem como casos de estudo abstratos.

## O que pode e o que não pode aqui

**Pode:** visão geral, padrões, decisões com trade-offs, lições, diagramas genéricos, how-tos com placeholders.

**Não pode:** documentação detalhada de componentes, conteúdo de produto (roadmap, backlog, marca, preços,
clientes), identificadores operacionais (IPs, hostnames internos, caminhos de segredos, IDs de contas),
nomes de repositórios privados e vulnerabilidades em aberto. Uma lição só é publicada depois de corrigida.

## Hábito antes de cada commit

Liste todo identificador concreto adicionado no diff e confirme que nenhum está na lista acima.
Use placeholders: `<app>.example.dev`, `<node-ip>`, `/<escopo>/<segredo>`, "App A".
