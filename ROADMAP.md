# Plano do projeto — desenho-animado

Base: [davixavier-coder/Animated-23D-Xavier](https://github.com/davixavier-coder/Animated-23D-Xavier) (MIT).
Objetivo: transformar a skill de shorts animados numa fábrica de **séries animadas em vários estilos**, com
**shorts verticais por capítulo** e **episódios longos de ~10 min para o YouTube** montados a partir deles.

Como acompanhar a evolução:
- Este arquivo: cada tarefa vira `[x]` quando termina.
- [`CHANGELOG.md`](CHANGELOG.md): o que mudou em cada versão, com data.
- Tags `v0.1.0`, `v0.2.0`…: uma por fase concluída (aba **Releases/Tags** do GitHub).
- Histórico de commits: um commit por tarefa, com o número dela na mensagem (ex.: `F3.2: ...`).

---

## Fase 0 — Base importada · `v0.1.0` ✅
- [x] 0.1 Copiar a skill original (templates, referências, scripts) para este repositório
- [x] 0.2 Criar plano (`ROADMAP.md`), histórico (`CHANGELOG.md`) e regras para o Claude Code (`CLAUDE.md`)

## Fase 1 — Rodar no PC (Windows) · `v0.2.0`
Meta: o exemplo da Torre de Pisa renderizando no seu computador, com tempo medido.
- [ ] 1.1 Conferir Node, ffmpeg e Google Chrome instalados
- [ ] 1.2 Montar o projeto em `projeto/` (cópia de `templates/projeto/` + exemplos em `src/videos/`) e `npm install`
- [ ] 1.3 Abrir o estúdio (`npx remotion studio src/index.ts`) e ver a Torre de Pisa
- [ ] 1.4 Script `scripts/benchmark` — renderiza 60 quadros em 1080x1920 e 1440x2560 e mede quadros/segundo
- [ ] 1.5 Registrar em `docs/benchmark.md`: placa de vídeo, CPU, RAM, tempo por quadro e estimativas (20 s, 70 s, 10 min)
- [ ] 1.6 Anotar os consertos específicos de Windows (pasta temporária, `--gl=angle`, caminho do Chrome)

## Fase 2 — Primeiro short próprio · `v0.3.0`
Meta: um short de 20-30 s do começo ao fim, com história pesquisada pelo Claude e voz sua.
- [ ] 2.1 Escolher o tema (o Claude sugere 5 com fatos verificáveis)
- [ ] 2.2 `SCRIPT.md` com fatos + fontes; você revisa datas e números
- [ ] 2.3 Gravar `voice.wav` e gerar `words.json` (tempo por palavra)
- [ ] 2.4 Cenas, mundo, bonecos e som
- [ ] 2.5 Fotos de conferência → correções → render final 1440x2560
- [ ] 2.6 Documentar o fluxo real (o que demorou, o que deu errado) em `docs/fluxo.md`

## Fase 3 — Sistema de estilos · `v0.4.0`
Meta: escolher o estilo na hora de fazer o vídeo (`estilo: cartoon-contorno`, `estilo: <outro>`…).
- [ ] 3.1 Estrutura `estilos/<nome>/` com: `referencias/` (imagens), `MEDIDAS.md` (cores, contorno, luz, lente, bonecos
      em números) e `estilo.ts` (todos os valores do visual num lugar só)
- [ ] 3.2 Tirar os valores fixos espalhados (`lights.ts`, `ink.ts`, `lensblur.ts`, `grade.ts`, `toon.ts`, `chars.ts`)
      e fazer eles lerem o `estilo.ts` escolhido
- [ ] 3.3 Estilo 1: `cartoon-contorno` — o visual original, sem mudar nada no resultado (conferir com fotos lado a lado)
- [ ] 3.4 Roteiro para criar estilo novo: salvar referências → medir → gerar `MEDIDAS.md` → ajustar `estilo.ts` →
      comparar lado a lado até a nota ficar ≥ 8
- [ ] 3.5 Estilo 2 (você escolhe as referências) — se pedir bonecos/acabamento muito diferentes, criar código próprio
- [ ] 3.6 Atualizar a skill: perguntar **qual estilo** (lista o que existe em `estilos/`) em vez de só 2D/3D

## Fase 4 — Séries em capítulos · `v0.5.0`
Meta: uma história contínua dividida em vários shorts, com personagens e cenários iguais em todos.
- [ ] 4.1 Estrutura `series/<serie>/`:
  - `BIBLIA.md` — premissa, personagens, regras do mundo, resumo de cada capítulo, ganchos abertos
  - `elenco.ts` — os personagens (`Char`) definidos uma vez e importados por todos os capítulos
  - `cenarios.ts` — lugares reaproveitáveis (truque de vários lugares num mundo só)
  - `capitulos/cap01/`, `cap02/`… — `SCRIPT.md`, `voice.wav`, `words.json`, `scene.ts`
- [ ] 4.2 Uma composição Remotion por capítulo (`<Serie>Cap01`, `Cap02`…), registradas automaticamente
- [ ] 4.3 Fórmula de capítulo: abre com 1 frase de "antes…" (recap curto), fecha com gancho para o próximo
- [ ] 4.4 Folha de personagens (frente, lado, costas) gerada antes do capítulo 1
- [ ] 4.5 Atualizar a skill: "novo capítulo da série X" lê a `BIBLIA.md` e continua de onde parou
- [ ] 4.6 Série piloto com 3 capítulos

## Fase 5 — Episódio longo para o YouTube (16:9, ~10 min) · `v0.6.0`
Meta: juntar os capítulos já lançados num vídeo horizontal de ~10 min, **renderizado de novo em 16:9** (não é o short
vertical esticado nem com barras pretas).

Por que dá para fazer bem: o mundo é 3D. A mesma cena pode ser filmada de novo com uma câmera horizontal,
mostrando mais cenário dos lados, sem perder nada.
- [ ] 5.1 Câmera por formato: cada chave de câmera (`CAMS`/`KEYS`) ganha um ajuste `wide` (fov horizontal, recuo,
      altura do `look`) — padrão calculado automaticamente, com ajuste manual só nos planos que precisarem
- [ ] 5.2 Cenários mais largos: conferir as bordas laterais (aparecem coisas que no vertical ficavam fora) e completar
- [ ] 5.3 Composição `<Serie>Longo` (1920x1080, saída 2560x1440) que encadeia os capítulos com `<Series>` do Remotion
- [ ] 5.4 Costura entre capítulos: corta o recap e o gancho repetidos, coloca transição (fusão ou flash) e, se quiser,
      uma vinheta curta de abertura e encerramento
- [ ] 5.5 Áudio contínuo: junta as vozes e os efeitos de cada capítulo e faz uma trilha que atravessa as emendas
- [ ] 5.6 Gera automaticamente: `capitulos_youtube.txt` (00:00 Capítulo 1 …) para a descrição e uma thumbnail 1280x720
- [ ] 5.7 Plano B rápido (quando não der tempo de re-renderizar): vertical no centro com fundo desfocado dele mesmo
- [ ] 5.8 Primeiro episódio longo com os capítulos da série piloto (precisa de ~9-12 capítulos de 60 s para 10 min)
- [ ] 5.9 Atualizar a skill: "faz o episódio longo da série X com os capítulos 1 a N"

## Fase 6 — Agilizar a produção · `v0.7.0`
- [ ] 6.1 Comando único por capítulo: roteiro aprovado + voz → fotos de conferência → render → QA → mp4 final
- [ ] 6.2 Render em fila (vários capítulos à noite) e limpeza automática das pastas temporárias do Remotion
- [ ] 6.3 Planilha/arquivo de controle: capítulo, status (roteiro, voz, render, publicado), data de publicação

---

## Ideias guardadas (sem fase ainda)
- Versão em inglês dos capítulos (mesma imagem, voz e trilha novas)
- Publicação automática junto da esteira de vídeos que você já tem
