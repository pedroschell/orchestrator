# orchestrator

Um subagente para o Claude Code que **planeja tarefas complexas antes de qualquer linha de código**: entende o objetivo, aponta os riscos, sugere os especialistas e a stack, e define a ordem de execução.

Em projetos grandes, o erro mais caro é começar a implementar pelo lado errado. Este agente existe para a etapa anterior: ele não implementa, não revisa e não escreve documentação. Só decide o caminho, e entrega o plano em no máximo três parágrafos.

## O que ele entrega

- a estratégia recomendada;
- os especialistas e a stack sugeridos;
- a ordem de execução;
- os riscos identificados;
- o próximo passo.

## Por que ele é enxuto de propósito

- Lê só o contexto necessário, para não gastar a janela de contexto da conversa principal.
- Prioriza a menor solução possível e evita decisões irreversíveis sem necessidade.
- Roda no modelo `opus` e só com ferramentas de leitura (`Read`, `Grep`, `Glob`, `WebFetch`, `WebSearch`), então não altera nada no projeto.

## Como instalar

Para todos os seus projetos:

```bash
mkdir -p ~/.claude/agents
curl -o ~/.claude/agents/orchestrator.md https://raw.githubusercontent.com/pedroschell/orchestrator/main/orchestrator.md
```

Ou só para um projeto, salvando o arquivo em `.claude/agents/orchestrator.md` dentro dele.

Depois, peça algo como *"usa o orchestrator para planejar a migração do banco"*. O Claude também aciona o agente sozinho quando a tarefa pede coordenação.

## Combina com

O [delivery-reviewer](https://github.com/pedroschell/delivery-reviewer), que revisa a entrega depois que ela fica pronta. O orchestrator planeja, o delivery-reviewer confere.

## Licença

MIT
