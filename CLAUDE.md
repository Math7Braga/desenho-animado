# Regras para o Claude Code neste repositório

Este repositório é a versão do Matheus da skill de desenho animado (three.js + Remotion). Fale em português do Brasil.

## Antes de começar qualquer tarefa
1. Leia o `ROADMAP.md` e descubra em que fase o projeto está (a primeira com tarefas `[ ]`).
2. Leia o `SKILL.md` — ele tem o passo a passo, os consertos e os valores do visual.
3. Se o pedido não estiver no plano, pergunte se é para adicionar ao `ROADMAP.md` (na fase certa ou em "Ideias guardadas").

## Ao terminar cada tarefa
1. Marque `[x]` no `ROADMAP.md`.
2. Faça um commit só daquela tarefa, começando com o número dela: `F3.2: estilo.ts lido por lights/ink/grade`.
3. Anote no `CHANGELOG.md`, na seção da versão em andamento (crie `## [vX.Y.0] — em andamento` se não existir).
4. Quando todas as tarefas de uma fase estiverem `[x]`: troque "em andamento" pela data, crie a tag da fase
   (`git tag vX.Y.0`) e faça `git push --follow-tags`.

## Organização
- `templates/` e `references/`: material original da skill — só altere numa tarefa do plano que peça isso.
- `projeto/`: o projeto Remotion que roda de verdade (criado na Fase 1).
- `estilos/<nome>/`: estilos visuais (Fase 3). `series/<serie>/`: séries e capítulos (Fase 4).
- `docs/`: benchmark, fluxo e decisões.
- Nunca commite vídeos renderizados, `node_modules/` nem pastas temporárias do Remotion (veja `.gitignore`).
- Rascunhos dentro de `out/` em `.txt`, nunca `.ts` (quebram o `tsc`).

## Regras do conteúdo
- História, bonecos e voz são sempre do Matheus. As referências servem só para estudar o visual.
- Fatos com fonte no topo do `SCRIPT.md`; datas e números conferidos antes de gravar.
