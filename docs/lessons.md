# Lições aprendidas

- **Fronteiras de IaC têm de ser disjuntas.** Dois controladores no mesmo state se desfazem mutuamente.
- **Defaults seguros têm custo no consumidor.** Um chart genérico com `securityContext` restrito obriga as imagens
  a rodar sem root e em porta não privilegiada. Compensa, mas tem de estar documentado no chart.
- **Dependências acopladas se movem juntas.** Em stacks de ML/GPU (runtime, CUDA, bibliotecas numéricas), atualizar
  uma peça isolada quebra as outras. Agrupe as atualizações e teste a pilha inteira.
- **Nem todo repositório tem CI em PR.** Onde só há build no merge, valide localmente antes de integrar.
- **Documentação que vive longe do código envelhece.** Detalhe técnico junto do repositório; aqui só o que vale
  generalizar.
