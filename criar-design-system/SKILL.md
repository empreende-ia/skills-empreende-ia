---
name: criar-design-system
description: "Conduz qualquer pessoa — inclusive quem não é designer — da marca dela até um design system completo, visível e instalável: descoberta de marca, direção visual proposta (nunca perguntada), tokens.css, showcase.html verificado por screenshot, README de voz e visual, e a skill instalada em ~/.claude/skills/ pra todo projeto futuro herdar a identidade. Use quando alguém disser /criar-design-system, 'quero um design system', 'preciso de identidade visual', 'cria a paleta/tokens da minha marca', 'meu site tem cara de template', 'meus projetos cada um tem uma cara', ou quando um projeto novo for começar sem identidade definida."
user-invocable: true
---

# /criar-design-system — da marca aos tokens, do token à skill

Você **não vai escolher cores bonitas**. Você vai extrair uma identidade de um negócio real e
transformá-la em três coisas que existem depois que a conversa acaba:

| Artefato | Para quem | Onde vive |
|---|---|---|
| `tokens.css` | máquinas | raiz da skill do DS |
| `showcase.html` | humanos | raiz da skill do DS — abre com duplo clique |
| `SKILL.md` + `README.md` | agentes de IA | `~/.claude/skills/<marca>-design/` |

Se ao final existir só uma paleta no chat, a skill falhou.

---

## Os 7 princípios do método

Leia antes de perguntar qualquer coisa. Tudo nesta skill sai daqui.

| # | Princípio | O que ele impede |
|---|---|---|
| 1 | **Marca antes de cor.** A paleta é consequência do posicionamento. | O azul genérico que serviria pra qualquer empresa. |
| 2 | **Uma cor de assinatura, não uma paleta.** Um sistema forte é 1 cor + neutros bem escolhidos. Secundárias existem no token e quase nunca na tela. | O arco-íris de 6 cores que não deixa nada ser reconhecível. |
| 3 | **Tokens antes de componentes.** Cor, tipo, espaço, raio, elevação e motion primeiro. | Botão bonito e o resto do produto órfão. |
| 4 | **Voz junto com visual.** A tabela "falar / não falar" é obrigatória. | Um DS que resolve metade do trabalho e deixa o texto na mão de quem escrever. |
| 5 | **Duas ou três assinaturas memoráveis.** No DS de referência: o ponto esmeralda no wordmark, o glow no lugar da sombra, os números em gradiente. | Um sistema correto e esquecível. |
| 6 | **O DS precisa ser visível.** Showcase HTML standalone. | "Confia, ficou bom" — ninguém aprova o que não viu. |
| 7 | **O DS precisa ser instalável.** Uma skill, não um PDF. | O DS morrer na terceira semana porque dá trabalho lembrar dele. |

> **A régua do princípio 2:** conte as cores que aparecem numa tela cheia do produto.
> Mais de 3 (assinatura + 2 neutros) e você não fez um sistema, fez uma decoração.

---

## Regras de condução

1. **Máximo 4 perguntas por rodada.** Questionário de 20 itens faz a pessoa desistir na terceira.
2. **Use `AskUserQuestion` com opções prontas.** Escolher é mais fácil que redigir. Sem a ferramenta, faça perguntas numeradas com alternativas em texto.
3. **Toda pergunta vem com default explícito:** *"se você não souber, eu assumo X."* "Sei lá" tem que manter o fluxo andando.
4. **Nunca pergunte "que estilo você quer".** Quem não é designer não sabe responder — e quem sabe responde "moderno e clean", que não significa nada. Proponha e deixe apontar. **Reconhecer é mais fácil que lembrar.**
5. **Nunca pergunte "qual cor você gosta".** A cor preferida da pessoa não é a cor da marca dela. Se ela impuser uma cor, aceite — mas escolha o tom, os neutros e o papel dela no sistema.
6. **Nunca pergunte o que dá pra descobrir sozinho.** Se existe site, Instagram, logo, repositório ou print, abra antes e traga como fato: *"vi que seu site hoje usa um azul #2563eb e Poppins — mantenho, ajusto ou troco?"*
7. **Se disserem "faz você mesmo" / "vai logo"**, pare de perguntar: preencha com defaults, marque cada escolha inventada com `[SUPOSIÇÃO]` e entregue o DS inteiro.
8. **Nunca entregue um antipadrão.** Antes de fechar a Rodada 1, leia `references/antipadroes.md` e confira a direção proposta contra a lista. Um clichê de IA queima toda a credibilidade do resultado.
9. **Escreva em pt-BR.** Nomes de token em inglês (`--bg-card`, `--fg-muted`) — é o que o resto do mundo lê. Documentação e conversa em português.

---

## RODADA 0 — DESCOBERTA DE MARCA

Comece **sempre** aqui, mesmo que a pessoa chegue dizendo "quero azul e branco".

> Não pergunte a solução, pergunte o negócio. Quem não sabe descrever um estilo sabe muito bem
> descrever o cliente que ela quer e o concorrente que ela não quer parecer.

Antes de perguntar: **se existe qualquer superfície pública da marca, abra.** Site, Instagram, PDF,
repositório, logo no computador. Traga o que achou como fato na primeira mensagem.

### As 4 perguntas (use `AskUserQuestion`)

**1. O que o negócio faz e vende — em uma frase?**
Peça a frase, não a categoria. *"Consultoria"* não serve; *"eu desenho automações de WhatsApp pra
empresas que já cansaram de template"* serve.
→ Default se travar: ofereça 3 leituras a partir do que você viu e deixe escolher.

**2. Para quem? Quem paga?** (opções prontas, múltipla escolha)
`empresa grande / diretoria` · `pequeno negócio / dono` · `consumidor final` · `desenvolvedor / técnico` ·
`paciente / aluno / cliente de serviço` · `investidor / mercado financeiro`
→ Default: `pequeno negócio / dono`.

**3. O que a marca NÃO é?** — a pergunta mais valiosa da rodada. (múltipla escolha + campo livre)
`não é barata` · `não é corporativa/engravatada` · `não é infantil` · `não é hypada/startupeira` ·
`não é artesanal/fofa` · `não é técnica demais` · `não é agressiva/vendedora`
→ Default: `não é corporativa` + `não é hypada`.
> Anti-posicionamento é mais fácil de nomear que posicionamento, e recorta a direção visual com
> muito mais precisão. Registre cada "não é" — vira restrição na Rodada 1.

**4. Me mostra alguma coisa.** *(sempre peça — é o que mais muda a qualidade)*
> - **print** de uma marca/site que você gosta — e me diz o que especificamente você gosta nela
> - **link** do seu site, Instagram ou de um concorrente
> - **logo, cores ou fontes** que você já usa e não quer perder
> - **print de um concorrente que você acha ruim** (vale tanto quanto o bom)
>
> Pode arrastar aqui. Se não tiver nada, eu sigo pela descrição — mas aí eu escolho por você.

**Se mandarem referência: abra de fato** (Read na imagem, WebFetch no link) e devolva o que extraiu,
em 3 a 5 linhas, com o que é aproveitável e o que não é:

> Do print que você mandou eu tirei: fundo claro quase branco (#FAFAF9), uma face serifada só no
> título, tudo alinhado à esquerda, muito espaço vazio, uma cor só de destaque (laranja queimado).
> O que **não** vou trazer: a foto de banco de imagem e o botão com sombra dura.

Se não mandarem nada, registre `[SEM REFERÊNCIA — direção escolhida pela IA]` e siga.

### Feche a rodada com a leitura em uma frase

> Então: **[o que faz]** pra **[quem]**, que precisa parecer **[3 adjetivos]** e nunca **[o que não é]**.
> É isso?

Só depois do "é isso" vá pra Rodada 1.

---

## RODADA 1 — DIREÇÃO VISUAL

**Não pergunte que estilo a pessoa quer.** Proponha **2 ou 3 direções concretas e distintas**,
derivadas das respostas da Rodada 0, e deixe apontar.

Leia `references/direcoes-visuais.md` — ele tem o arquétipo de negócio de cada tipo de cliente e a
direção que costuma servir (temperatura, face, papel da cor, densidade). As propostas saem dali,
filtradas pelo "o que a marca NÃO é".

### Como montar as 3 propostas

| Proposta | Papel | Regra |
|---|---|---|
| **A — a esperada** | o que o arquétipo pede, bem executado | Segura quem quer parecer da categoria. |
| **B — o contraste** | a virada oposta em temperatura ou densidade | É onde nasce marca. Quase sempre é a escolhida quando a pessoa disse muitos "não é". |
| **C — a da referência** | destilada do print/link que ela mandou | Só existe se houve referência. Sem referência, entregue 2. |

> **Régua:** se as três propostas puderem usar a mesma foto de capa, elas não são distintas.
> Refaça. Duas variações de tom da mesma cor **não** são duas direções.

### O que cada proposta precisa ter — obrigatório

1. **Nome** com personalidade (não "Opção 1"): *"Escritório de Arquitetura"*, *"Terminal"*, *"Clínica Calma"*.
2. **Cor de assinatura em hex** — uma só, com o nome do tom: `#B45309 — âmbar queimado`.
3. **Base**: claro, escuro, ou claro com seções escuras. Diga qual e por quê.
4. **Faces tipográficas**: display + texto (+ mono se fizer sentido), com a fonte de onde vêm
   (Google Fonts / Fontshare / paga).
5. **Uma frase de personalidade**: *"parece o caderno de um arquiteto: muito branco, uma cor só, nada centralizado."*
6. **Uma assinatura memorável** já nomeada: o detalhe que vai fazer alguém reconhecer a marca.

### Apresentação

Use `AskUserQuestion` com uma opção por direção. Coloque **nome + hex + faces** no rótulo/descrição e
use o campo de **preview** pra mostrar as três lado a lado — amostra de cor, o nome da marca renderizado
na face de display e a frase de personalidade. Ver decide mais rápido que ler.

Se não houver preview disponível, gere um `direcoes.html` de 1 tela com as 3 colunas, tire screenshot,
mostre, e **aí** pergunte.

Ofereça sempre uma quarta saída: **"nenhuma dessas — o que te incomodou?"**. O que incomoda é
informação melhor que o que agrada.

### Antes de fechar

Rode a direção escolhida contra `references/antipadroes.md`. Se bater em qualquer item da lista,
**ajuste antes de mostrar**, não depois de ouvir.

---

## RODADA 2 — TOKENS

Gere `tokens.css` completo seguindo **`references/anatomia-de-tokens.md`** — ele tem o inventário
obrigatório, o porquê de cada grupo e as armadilhas.

Sem perguntas nesta rodada. Você já tem tudo que precisa. Decida e mostre.

**Antes da primeira linha: crie a pasta e escreva já lá dentro.** Nada de gerar no diretório atual pra
mover depois — arquivo de DS solto na raiz de outro projeto é lixo que ninguém acha.

```bash
mkdir -p ~/.claude/skills/<marca>-design/assets
```

`tokens.css` (Rodada 2), `showcase.html` (Rodada 3), `SKILL.md` e `README.md` (Rodada 4) nascem todos
aí. A Rodada 4 vira **conferência**, não mudança de lugar.

**Ordem de trabalho:**

1. **Escala da assinatura** — 5 tons (300/400/500/600/700) a partir do hex escolhido. O 500 é a assinatura.
2. **Neutros** com a mesma temperatura da assinatura (fria com fria, quente com quente). Cinza neutro
   ao lado de cor quente deixa a marca suja.
3. **Superfícies e texto**, nos dois temas — claro e escuro, sempre os dois.
4. **Verificação de contraste**: todo par texto/fundo declarado precisa passar AA (4.5:1 texto normal,
   3:1 texto ≥24px ou bold ≥18.66px). Calcule, não estime.
   > Armadilha recorrente: a cor de assinatura em texto pequeno sobre fundo claro quase nunca passa.
   > A saída é ter um token dedicado (`--primary-on-light`) com o tom 2 passos mais escuro.
5. **Tipo, espaço, raio, elevação, motion** — todos, mesmo os que o projeto de hoje não usa.
6. **Gradientes e assinaturas da marca** — as 2 ou 3 decididas na Rodada 1, como token nomeado.
7. **Classes semânticas** (`.<prefixo>-card`, `.<prefixo>-btn`, `.<prefixo>-pill`, `.<prefixo>-wordmark`)
   pra dar pra usar a marca sem cablear variável por variável.

**Régua de pronto dos tokens:**

- [ ] Nenhum hex solto fora do bloco `:root` — componente usa `var()`.
- [ ] Todo token declarado no tema escuro existe também no claro (e vice-versa).
- [ ] Todo token tem nome de **papel** (`--fg-muted`), nunca de **valor** (`--cinza-claro`).
- [ ] Font-family tem fallback de sistema no fim da pilha.
- [ ] Existe token de foco visível (`--ring`) — acessibilidade não é opcional.
- [ ] A cor de assinatura **não** é a mesma do estado de sucesso.

---

## RODADA 3 — SHOWCASE (e a verificação por screenshot)

Gere `showcase.html` a partir de **`references/template-showcase.html`** — arquivo único, standalone,
que abre com duplo clique, sem build e sem CDN obrigatório.

Seções mínimas: capa com o wordmark · paleta com copiar-hex · escala tipográfica · espaço e raio ·
elevação · motion · componentes (botão, card, input, pill, badge, tabela) · **as assinaturas da marca** ·
**a tabela falar / não falar** · o par certo/errado · toggle claro/escuro.

### Verifique antes de mostrar — não negociável

Nunca diga "ficou pronto" sem ter olhado. Tire screenshot e **você** olhe primeiro.

**Desktop — 1440px:**

```bash
# headless, sem abrir janela — funciona no Mac com Chrome instalado
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --hide-scrollbars \
  --screenshot="/tmp/showcase.png" --window-size=1440,3000 \
  "file:///caminho/showcase.html"
```

**Mobile — 375px, e aqui tem uma armadilha medida.** `--window-size=375,…` **não** entrega uma
viewport de 375 CSS px: o Chrome headless tem largura mínima (medido no Chrome 150: `clientWidth`
485 pedindo 375). Ele diagrama em ~485 e **recorta** a imagem em 375 — o que aparece é texto cortado
na direita, que você lê como "estourou no mobile" quando não estourou nada. Falso positivo garantido.

O jeito confiável é embutir o showcase num iframe de 375 e fotografar a página de fora:

```bash
cat > /tmp/mob.html <<'HTML'
<!DOCTYPE html><html><head><meta charset="utf-8">
<style>html,body{margin:0;background:#888}
iframe{width:375px;height:2400px;border:0;display:block;margin:0 auto}</style></head>
<body><iframe src="file:///caminho/showcase.html"></iframe></body></html>
HTML

"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --hide-scrollbars \
  --screenshot="/tmp/showcase-375.png" --window-size=520,2400 \
  "file:///tmp/mob.html"
```

A faixa cinza dos dois lados é a moldura: **o conteúdo tem que caber na coluna branca de 375**.
Se vazar por cima do cinza ou aparecer barra de rolagem dentro do iframe, aí sim estourou.

Alternativa: MCP `claude-in-chrome` (`navigate` + `computer` screenshot). Depois, **leia as imagens
com o Read** e passe a régua:

| Checagem | Reprova se |
|---|---|
| Token faltando | Aparece bloco preto, branco ou transparente onde deveria ter cor |
| Fonte não carregou | O display renderizou igual ao texto (caiu no fallback) |
| Dominância da assinatura | A cor de assinatura ocupa mais que ~10% da tela |
| Contraste real | Texto muted sobre card fica ilegível na imagem |
| Mobile 375px | Existe rolagem lateral, ou tabela/paleta estourando |
| Tema claro | Foi só o escuro invertido e ficou sujo |
| Antipadrão | Bate em qualquer item de `references/antipadroes.md` |

Se qualquer linha reprovar: **conserte e tire outro screenshot**. Só então mostre.

Ao mostrar, mande a imagem + o caminho do arquivo + uma pergunta fechada:
*"o que você mudaria: a cor, a fonte, ou o espaço?"* — três opções decidem mais rápido que "o que achou?".

---

## RODADA 4 — EMPACOTAR E INSTALAR

O DS vira uma pasta em `~/.claude/skills/<marca>-design/`:

```
~/.claude/skills/<marca>-design/
├── SKILL.md        ← gerado de references/template-skill.md (com os campos de convenção)
├── README.md       ← o manual: marca, voz, visual, iconografia, armadilhas
├── tokens.css      ← fonte da verdade
├── showcase.html   ← a prova visual
└── assets/         ← logo/wordmark SVG, favicon (se existirem)
```

### O `README.md` — as seções obrigatórias

Espelha o padrão do DS de referência (`~/.claude/skills/henrique-gabriel-design/README.md`):

1. **Posicionamento** — o que é, pra quem, tagline, links.
2. **Fundamentos de conteúdo** — idioma, pessoa verbal (eu/nós/você), caixa e pontuação, emoji (sim/não),
   e a **tabela falar / não falar** (mínimo 5 pares). Sem isso o DS não está pronto.
3. **Fundamentos visuais** — paleta com papel de cada cor, tipografia (incl. tracking), espaço, fundos,
   animação, hover/press, bordas e elevação, raios, o componente-assinatura, layout, imagens.
4. **Iconografia** — qual biblioteca, espessura, tamanhos, cor, e o que **não** usar.
5. **As assinaturas da marca** — as 2 ou 3, escritas como receita reproduzível (não como adjetivo).
6. **Ressalvas e substituições** — fonte paga substituída, cor do site divergindo do spec, etc.

### O `SKILL.md` gerado — a convenção de detecção

Use `references/template-skill.md`. O frontmatter **precisa** ter:

```yaml
---
name: <marca>-design
description: "Use esta skill para gerar qualquer interface, peça ou artefato da marca <Marca> ..."
user-invocable: true
type: design-system            # ← marcador da convenção (obrigatório)
ds-tokens: tokens.css          # ← arquivo de tokens na raiz da skill (obrigatório)
ds-brand: <Marca>              # opcional, recomendado
ds-signature: "#RRGGBB"        # opcional, recomendado
---
```

### Instalação — conferência, porque os arquivos já nasceram no lugar

```bash
ls -la ~/.claude/skills/<marca>-design            # os 4 arquivos + assets/
head -10 ~/.claude/skills/<marca>-design/SKILL.md # frontmatter com type e ds-tokens
open ~/.claude/skills/<marca>-design/showcase.html
```

Se por algum motivo os arquivos foram gerados em outro lugar, mova (não copie — duas cópias divergem):

```bash
mkdir -p ~/.claude/skills/<marca>-design
mv <origem>/{SKILL.md,README.md,tokens.css,showcase.html} ~/.claude/skills/<marca>-design/
[ -d <origem>/assets ] && mv <origem>/assets ~/.claude/skills/<marca>-design/
```

Depois **rode o comando de varredura** (seção abaixo): se a marca não aparecer na lista, ela não está
instalada de verdade — não importa que os arquivos existam.

Se a pessoa quiser o DS versionado com o projeto, instale também em `<projeto>/.claude/skills/` —
mesma estrutura, mesma convenção.

### Aponte o CLAUDE.md do projeto para o DS

É o que faz o DS sobreviver à terceira semana. Acrescente ao `CLAUDE.md` do projeto:

```markdown
## Design system
Este projeto usa o design system **<Marca>** (skill `<marca>-design`).
Antes de escrever qualquer CSS, componente ou tela, leia
`~/.claude/skills/<marca>-design/README.md` e use `tokens.css` como fonte da verdade.
Proibido: hex solto no componente, fonte fora das declaradas, cor de destaque
que não seja a de assinatura. Na dúvida sobre um valor, use o token mais próximo — nunca invente um.
```

---

## RODADA 5 — APROVAÇÃO VISUAL

A verificação da Rodada 3 é sua: ela pega **defeito**. Esta é da pessoa: ela pega **discordância**.
São coisas diferentes, e é por isso que esta rodada existe e vem **depois** de instalar.

### 1. Abra o showcase no navegador — de verdade

Não mostre o caminho pedindo que ela abra. Quem roda comando é você; ela só aprova. Detecte o sistema
antes:

```bash
DS=~/.claude/skills/<marca>-design
case "$(uname -s)" in
  Darwin)      open "$DS/showcase.html" ;;
  Linux)       xdg-open "$DS/showcase.html" >/dev/null 2>&1 & ;;
  MINGW*|MSYS*|CYGWIN*) start "" "$DS/showcase.html" ;;
  *)           cmd.exe /c start "" "$DS/showcase.html" 2>/dev/null || xdg-open "$DS/showcase.html" ;;
esac
```

### 2. Diga o que ela está olhando — três ou quatro linhas

Sem isso a pessoa encara a página inteira sem saber onde reparar. Diga, nesta ordem:

> - **A cor de assinatura é `#B45309`** — é a direção "Escritório de Arquitetura" que você escolheu na
>   Rodada 1, âmbar queimado sobre papel quase branco.
> - **As assinaturas da marca** são o overline com fio atravessando e o número em tabular: é por elas
>   que alguém vai reconhecer a marca. Repare nelas primeiro.
> - **Foi decidido por mim** o que está marcado `[SUPOSIÇÃO]`: a escala de raio e o peso do título.
>   Corrija sem cerimônia.
> - **Repare especialmente em:** a capa com o wordmark e o bloco de componentes. É onde o sistema
>   se prova.

### 3. Pergunte se tem ajuste — com opções prontas

`AskUserQuestion`. Nunca "o que você achou?": pergunta aberta devolve "ficou legal" e a discordância
só aparece três dias depois. Ofereça as saídas mais prováveis:

`está aprovado` · `a cor não é bem essa` · `a tipografia não combina` · `está pesado / apertado demais` ·
`quero ver no celular` · `outra coisa (me conta o quê)`

A opção **"quero ver no celular"** vale sempre que houver dúvida de leitura: mande o PNG de 375px que
você já tem da Rodada 3, ou tire outro.

### 4. Se houver ajuste, é um laço — não uma pergunta única

Para cada volta: **aplique só o que ela apontou** → reverifique por screenshot (Rodada 3) → reabra no
navegador → pergunte de novo. Não redesenhe o resto por conta própria: ajuste pedido é ajuste pedido,
e "aproveitei e melhorei aqui também" é como se perde a confiança de quem já tinha aprovado o resto.

Só se sai do laço com a aprovação explícita.

> **A régua dos três laços.** Um ajuste que a pessoa **pede** é ajuste. Uma direção nova que ela
> **descobre que queria** é outra rodada — a 1, não esta. Se no terceiro laço ainda não houve
> aprovação, pare e diga isso a ela: provavelmente a direção escolhida não era a dela, e o caminho é
> voltar às propostas da Rodada 1 (ou montar uma quarta a partir do que incomodou). Continuar
> ajustando cor por cor gasta a paciência dela e não conserta uma direção errada.

### 5. Aprovou: propague para os arquivos instalados

**É aqui que mais dá errado.** A pessoa aprova a versão que está na pasta de trabalho enquanto a skill
instalada continua com a versão anterior — e o DS que todo projeto futuro vai ler é a versão errada.

Depois do "aprovado": reinstale ou sincronize, e **confirme** que os quatro arquivos instalados batem
com os aprovados.

```bash
# se por algum motivo trabalhou fora da pasta instalada, sincronize e confira
cp -R <pasta de trabalho>/. "$DS"/
for f in SKILL.md README.md tokens.css showcase.html; do
  cmp -s "<pasta de trabalho>/$f" "$DS/$f" && echo "ok   $f" || echo "DIVERGE  $f"
done
```

Os arquivos nasceram direto na pasta instalada (o recomendado, Rodada 2)? Ainda assim confirme os
quatro e rode a varredura uma última vez. Conferência barata evita a descoberta cara.

### 6. Feche dizendo o que ela tem agora

Três linhas, sem rodeio:

> - **Skill instalada:** `<marca>-design`
> - **Caminho:** `<caminho absoluto>`
> - **Como usar em outro projeto:** peça "usa o design system `<marca>-design`" no começo da conversa,
>   ou cole o bloco de `CLAUDE.md` da Rodada 4 no projeto — aí toda sessão futura já nasce com a
>   identidade certa.

E o antes e o depois: o pedido original de uma linha ao lado dos 4 arquivos entregues.

---

## A convenção de detecção — como outras skills acham os DS instalados

Para que qualquer skill (ou você, numa sessão futura) descubra os design systems da máquina, um DS se
identifica por **sinal duplo** — barato de verificar e difícil de dar falso positivo:

| Sinal | Regra |
|---|---|
| **(a) Frontmatter** | `type: design-system` **e** `ds-tokens: <arquivo>` no `SKILL.md` |
| **(b) Arquivo** | O arquivo apontado por `ds-tokens` existe **na raiz da skill** |

Os dois precisam ser verdade. Frontmatter sem arquivo é um DS quebrado (avise); arquivo sem
frontmatter é CSS solto (ignore).

**O arquivo de tokens é o que `ds-tokens` declarar** — qualquer nome, desde que exista na raiz.
Se o campo faltar ou apontar pra arquivo inexistente, a varredura ainda tenta três nomes conhecidos,
nesta ordem: `tokens.css` · `colors_and_type.css` · `design-tokens.css` (o DS de referência usa o do
meio, por retrocompatibilidade). Não encontrou nenhum: **DS quebrado**, e a varredura diz isso.

### Comando de varredura

Três cautelas embutidas: usa `find` em vez de glob (zsh aborta o comando inteiro quando um glob não
casa); **só lê as 20 primeiras linhas**, para checar o frontmatter de verdade — senão qualquer arquivo
que *documente* o campo (este aqui, por exemplo) vira falso positivo; e imprime o campo `name` do
frontmatter, não o nome da pasta — **é pelo `name` que a skill é invocada**, e os dois podem divergir.

```bash
# lista os design systems: skill · marca · assinatura · arquivo de tokens
# varre os dois lugares onde skill mora; acrescente outras pastas depois de ./.claude/skills
find ~/.claude/skills ./.claude/skills -maxdepth 2 -name SKILL.md 2>/dev/null | while read -r f; do
  head -20 "$f" | grep -qE '^type:[[:space:]]*design-system[[:space:]]*$' || continue
  d=$(dirname "$f"); fm=$(head -20 "$f")
  nm=$(  printf '%s\n' "$fm" | grep -m1 -E '^name:'      | sed -E 's/^name:[[:space:]]*//; s/["'"'"']//g')
  nm=${nm:-$(basename "$d")}
  decl=$(printf '%s\n' "$fm" | grep -m1 -E '^ds-tokens:' | sed -E 's/^ds-tokens:[[:space:]]*//; s/["'"'"']//g')
  tok=""
  for c in "$decl" tokens.css colors_and_type.css design-tokens.css; do
    [ -n "$c" ] && [ -f "$d/$c" ] && { tok="$d/$c"; break; }
  done
  [ -n "$tok" ] || { printf '%-26s  [DS QUEBRADO: tokens ausentes em %s]\n' "$nm" "$d"; continue; }
  brand=$(printf '%s\n' "$fm" | grep -m1 -E '^ds-brand:'     | sed -E 's/^ds-brand:[[:space:]]*//; s/["'"'"']//g')
  sig=$(  printf '%s\n' "$fm" | grep -m1 -E '^ds-signature:' | sed -E 's/^ds-signature:[[:space:]]*//; s/["'"'"']//g')
  printf '%-26s  %-20s  %-9s  %s\n' "$nm" "${brand:--}" "${sig:--}" "$tok"
done
```

Saída nesta máquina (caminho absoluto — `~` é expandido pelo shell antes do `find`):

```
henrique-gabriel-design     Henrique Gabriel      #10b981    /Users/<user>/.claude/skills/henrique-gabriel-design/colors_and_type.css
```

**DS que não foi instalado não aparece — e está certo.** Um kit de exemplos baixado tem DS conformes,
mas eles só entram na lista de instalados quando a pasta é copiada pra `~/.claude/skills/`. Pra
conferir sem instalar, acrescente **a pasta aberta agora** aos caminhos do `find` — nunca um caminho
fixo, porque cada máquina descompacta o material num lugar diferente:

```bash
find ~/.claude/skills ./.claude/skills . -maxdepth 3 -name SKILL.md 2>/dev/null \
  | while read -r f; do ...   # resto igual
```

Com o kit do curso aberto, isso lista `kiln-design` · `nogueira-prumo-design` · `fervo-design` ·
`amparo-design` · `cotejo-design`.

Versão curta, só pra saber se existe algum:

```bash
find ~/.claude/skills ./.claude/skills -maxdepth 2 -name SKILL.md 2>/dev/null \
  | xargs -I{} sh -c 'head -20 "{}" | grep -qE "^type:[[:space:]]*design-system[[:space:]]*$" && echo "{}"'
```

**Use isso no começo de qualquer trabalho visual.** Se já existe um DS instalado para a marca em
questão, não crie outro — leia o que existe. Criar o segundo DS da mesma marca é o jeito mais rápido
de não ter nenhum.

---

## Adotar o DS num projeto que já existe

Projeto com código rodando não se refaz — se **converte**, e em ordem.

### 1. Levantamento (antes de mudar uma linha)

```bash
grep -rnoE '#[0-9a-fA-F]{3,8}\b' src/ --include=*.{ts,tsx,js,jsx,css,scss,vue,svelte} | sort -u | head -60
grep -rnoE 'rgba?\([^)]*\)' src/ --include=*.{css,scss,tsx,jsx} | sort -u | head -40
grep -rn 'font-family' src/ | head -20
```

Mostre o resultado: *"seu projeto tem 23 cores diferentes hardcoded e 3 fontes. O DS tem 1 cor de
assinatura e 2 fontes. Vou mapear as 23 pras 9 do sistema."*

### 2. Mapa de conversão

Monte a tabela `cor encontrada → token` **antes** de editar, e mostre pra pessoa aprovar.
Cor que não mapeia em nada geralmente é bug antigo, não decisão de design.

### 3. Tailwind — a conversão certa

Não substitua hex por hex. Aponte o Tailwind para as variáveis, e o resto do código continua igual:

```js
// tailwind.config.ts
theme: {
  extend: {
    colors: {
      primary:  { DEFAULT: 'var(--primary-500)', 400: 'var(--primary-400)', 700: 'var(--primary-700)' },
      bg:       { base: 'var(--bg-base)', card: 'var(--bg-card)', elevated: 'var(--bg-elevated)' },
      fg:       { DEFAULT: 'var(--fg)', muted: 'var(--fg-muted)', subtle: 'var(--fg-subtle)' },
      border:   { DEFAULT: 'var(--border)', muted: 'var(--border-muted)' },
    },
    borderRadius: { md: 'var(--radius-md)', lg: 'var(--radius-lg)', xl: 'var(--radius-xl)' },
    fontFamily:   { sans: 'var(--font-sans)', mono: 'var(--font-mono)' },
  }
}
```

Se o projeto é shadcn/ui, mantenha os nomes `--background` / `--foreground` / `--primary` que ele
espera e **derive** dos seus tokens — não brigue com a convenção da lib.

### 4. Ordem de conversão

`tokens.css` importado no entrypoint → cores → tipografia → raio e sombra → espaçamento.
**Uma camada por vez, com screenshot entre elas.** Converter tudo de uma vez e descobrir que quebrou
não deixa saber o quê quebrou.

### 5. Amarre

Aponte o `CLAUDE.md` (bloco da Rodada 4) e, se der, deixe a regra de lint: nenhum hex novo em `src/`.

---

## Modo aula

Se a pessoa disser que está **gravando, ensinando ou fazendo demo**, mude a condução:

1. **Narre o princípio antes de cada rodada.** *"Rodada 0 — repare que eu não vou perguntar cor
   nenhuma. Cor é consequência; a gente ainda nem sabe o que essa marca não é."*
2. **Mostre a pergunta que você NÃO fez.** O contraste didático mais forte da skill é:
   *"o caminho comum aqui seria perguntar 'qual estilo você quer'. Eu não pergunto — eu proponho
   três e deixo apontar, porque reconhecer é mais fácil que lembrar."*
3. **Erre de propósito, uma vez.** Mostre uma direção clichê (roxo→azul, Inter, tudo centralizado),
   nomeie por que é clichê pela lista de antipadrões, e corrija ao vivo. Vale mais que dez acertos.
4. **Abra o screenshot na tela.** O momento em que o showcase aparece é o clímax da aula — não pule
   pra descrição em texto.
5. **Encene a Rodada 5.** Peça um ajuste de mentira ("essa cor tá clara demais"), aplique, reverifique
   por screenshot e reabra no navegador. É o que ensina a distinção mais importante do fim do método:
   *"o screenshot é pra eu ver se quebrou; abrir no navegador é pra você ver se discorda. São coisas
   diferentes, e as duas precisam acontecer."*
6. **Feche com o antes e depois:** a frase de uma linha que a pessoa escreveu, ao lado da árvore de
   arquivos instalada e do `CLAUDE.md` apontando pra ela.
7. **Deixe a lição de casa:** *"rode `/criar-design-system` pra sua própria marca e me manda o
   showcase"* — o entregável é visual, então dá pra corrigir turma inteira em um scroll.

**Ritmo sugerido pra uma aula de ~40min:** Rodada 0 (7min) · Rodada 1 (9min, com o erro proposital) ·
Rodada 2 (6min, narrando as armadilhas de token) · Rodada 3 (9min, incluindo o screenshot) ·
Rodada 4 (4min, instalação e CLAUDE.md) · Rodada 5 (5min, com o ajuste encenado).

---

## Régua de pronto — o DS só está entregue quando

- [ ] Existe **uma** cor de assinatura, e ela aparece em menos de 10% da tela do showcase.
- [ ] Existem **2 ou 3 assinaturas** memoráveis, escritas como receita reproduzível.
- [ ] Os tokens cobrem cor, tipo, espaço, raio, elevação e motion — nos dois temas.
- [ ] Todo par texto/fundo declarado passa AA.
- [ ] O `README.md` tem a tabela **falar / não falar** com pelo menos 5 pares.
- [ ] O `showcase.html` abre com duplo clique e foi **verificado por screenshot** em 1440 e 375.
- [ ] A skill está instalada em `~/.claude/skills/<marca>-design/` com `type: design-system` e `ds-tokens`.
- [ ] O comando de varredura lista a nova skill.
- [ ] O `CLAUDE.md` de pelo menos um projeto aponta pro DS.
- [ ] Nada na direção final bate em `references/antipadroes.md`.
- [ ] A pessoa **abriu no navegador e aprovou** (Rodada 5) — e os arquivos instalados são os aprovados.
- [ ] O caminho de instalação usado foi **reportado** na mensagem final.

---

## Arquivos de apoio

| Arquivo | Quando ler |
|---|---|
| `references/anatomia-de-tokens.md` | Rodada 2 — inventário obrigatório e armadilhas |
| `references/direcoes-visuais.md` | Rodada 1 — arquétipos de negócio, faces e cores por direção |
| `references/antipadroes.md` | Fim da Rodada 1 e fim da Rodada 3 — sempre as duas vezes |
| `references/template-showcase.html` | Rodada 3 — esqueleto comentado do showcase |
| `references/template-skill.md` | Rodada 4 — esqueleto do SKILL.md gerado |

**Exemplo canônico de qualidade:** `~/.claude/skills/henrique-gabriel-design/` (README.md +
colors_and_type.css). Leia para calibrar profundidade. **Copie o método, nunca o estilo** — dark +
esmeralda é a marca de uma pessoa específica, não o resultado padrão desta skill.
