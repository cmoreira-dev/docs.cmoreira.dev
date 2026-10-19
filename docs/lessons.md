---
description: "O que quebrou ou surpreendeu ao operar a plataforma."
---

# Lições aprendidas

- **Fronteiras de IaC têm de ser disjuntas.** Dois controladores no mesmo state se desfazem mutuamente.
- **Defaults seguros têm custo no consumidor.** Um chart genérico com `securityContext` restrito obriga as imagens
  a rodar sem root e em porta não privilegiada. Compensa, mas tem de estar documentado no chart.
- **Dependências acopladas se movem juntas.** Em stacks de ML/GPU (runtime, CUDA, bibliotecas numéricas), atualizar
  uma peça isolada quebra as outras. Agrupe as atualizações e teste a pilha inteira.
- **Nem todo repositório tem CI em PR.** Onde só há build no merge, valide localmente antes de integrar.
- **Documentação que vive longe do código envelhece.** Detalhe técnico junto do repositório; aqui só o que vale
  generalizar.
- **CI verde não prova que algo foi planeado.** O filtro por git do Terragrunt só vê alterações ao ficheiro de
  configuração da unidade; uma mudança só dentro do módulo local ou de um lockfile dá uma lista vazia e o pipeline passa
  sem planear nada. Descubra a unidade pelo ficheiro alterado e falhe alto quando um ficheiro de infra não pertencer a
  nenhuma unidade.
- **"Só de leitura" nem sempre é.** Para o Terraform planear uma release Helm, a identidade tem de listar Secrets do
  namespace, e isso inclui chaves de sessão do próprio GitOps. Quem as lê é admin na prática. Em vez de uma identidade
  "só de leitura" que não existe, mova esse plano para o passo que já tem credenciais de admin.
- **Separe por raio de impacto, não por repositório.** O que mexe em nós ou VMs pede um passo humano; o resto aplica-se
  sozinho. E o que o pipeline assume (os seus próprios papéis) não pode ser gerido por ele: fica no bootstrap manual.
- **Adotar é provar zero diferenças.** Ao trazer recursos existentes para IaC, o primeiro plano tem de dar "sem
  alterações"; qualquer diferença é um stop. Para a configuração gerada do SO, a prova é o hash do resultado por nó, igual
  ao anterior.
- **Placas pequenas: 64 bits.** Um runner de CI numa placa ARM de 32 bits falhou (TLS e runtime de Node). Reinstalar
  em 64 bits custou menos do que contornar.
