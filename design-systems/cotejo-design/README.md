# Cotejo — Design System

**Posicionamento:** a plataforma de fechamento contábil e financeiro para controladorias que
encerram o mês no dia 1.
**Para quem:** analista de controladoria, contador, CFO de empresa média, escritório contábil.
Gente que passa seis horas por dia olhando para uma tabela e precisa achar a divergência de
R$ 1.204,00 antes do almoço.
**O que NÃO é:** um app de finanças pessoais, um dashboard de apresentação, uma tela de pitch.
Ninguém "navega" no Cotejo. As pessoas trabalham nele.

**Arquétipo:** dados, finanças, operação. **O número é o conteúdo** — todo o resto da interface
existe para não atrapalhar a leitura dele.

---

## Índice dos arquivos

| Arquivo | O que é |
|---|---|
| `tokens.css` | A fonte da verdade. Variáveis dos dois temas e classes `.ctj-*`. Nenhum valor visual nasce fora daqui. |
| `showcase.html` | A prova visual, standalone. Abre com duplo clique, sem rede, sem CDN. Tem alternador de tema funcionando. |
| `README.md` | Este manual: marca, voz, fundamentos visuais, regras de componente. |
| `SKILL.md` | Frontmatter de skill do Claude Code, com os campos de convenção de design system. |

---

## VOZ

O Cotejo escreve como um bom relatório contábil: afirma o fato, dá o número, aponta o que fazer.
Não anima, não pede desculpa, não explica a própria emoção.

### Regras de escrita

- **Idioma:** português do Brasil. Termo contábil em português (competência, conciliação,
  estorno, provisão, razão, balancete). Nada de "closing", "reconciliation", "cash burn".
- **Pessoa:** o produto fala de si na terceira pessoa — *"o Cotejo travou a competência"* — e trata
  o usuário por **você**. **Nunca** "nós", "a gente", "nossa equipe". Quem fala é um sistema, e um
  sistema não tem equipe dentro da tela.
- **Modo:** afirmativo e no presente. *"A competência está travada."* Não *"a competência não
  poderá ser editada no momento."*
- **Pontuação:** toda frase termina em ponto, inclusive rótulo de erro e texto de ajuda.
  **Zero ponto de exclamação.** Zero reticências. Travessão (—) para encaixar oração; nunca
  hífen duplo.
- **Número:** nunca aparece sem unidade e sem período de referência. *"R$ 1.204.887,43 em
  31/07/2026"*, não *"1204887"*. Percentual com duas casas; ponto percentual escrito **p.p.**
- **Data:** sempre `dd/mm/aaaa` por extenso numérico, ou `mmm/aa` em rótulo de coluna (`jul/26`).
- **Título:** sentence case. Nunca Title Case, nunca CAIXA-ALTA fora de overline e cabeçalho de
  coluna.
- **Erro:** diz o que aconteceu, o valor envolvido e o próximo passo. *"Dígito verificador
  inválido."* — não *"Ops, algo deu errado."*

### Falar / não falar

| Falar | Não falar |
|---|---|
| "Conciliado." | "Tudo certo!" |
| "Competência 07/2026." | "Este mês." |
| "Divergência de R$ 1.204,00 na conta 4.2.03." | "Encontramos uma pequena diferença." |
| "Fechamento travado por 3 pendências." | "Não foi possível continuar." |
| "Estorne o lançamento para liberar a conta." | "Ops, algo deu errado. Tente novamente." |

### Nunca aparece

Emoji. Ponto de exclamação. "Ops", "poxa", "eita". Gerundismo ("vou estar verificando").
Metáfora de jornada ("sua trilha financeira"). Adjetivo de marketing em rótulo de dado
("resultado incrível"). Número sem unidade.

---

## PALETA

A assinatura é **azul-aço**. Alta e baixa têm cor própria, deslocada da marca de propósito:
azul-aço é **ação**, jade é **alta**, tijolo é **baixa**. Se a marca também significasse "subiu",
o usuário perderia a diferença entre "isto é um botão" e "isto é um resultado".

### Assinatura — azul-aço (igual nos dois temas)

| Papel | Token | Hex | Onde usar |
|---|---|---|---|
| Ponta clara | `--steel-300` | `#7FA8D1` | Texto, link e mark sobre fundo escuro. Sparkline no tema escuro. |
| Hover no escuro | `--steel-400` | `#4E86BE` | Preenchimento do botão primário no tema escuro; segunda série de gráfico. |
| **A assinatura** | `--steel-500` | **`#2E6DA4`** | Preenchimento do botão primário no claro, anel de foco, borda de seleção, sparkline no claro. |
| Hover no claro | `--steel-600` | `#245685` | Hover do primário no claro; texto de link pequeno no claro. |
| Pressionado | `--steel-700` | `#1B4468` | Estado pressionado no claro; cauda de gradiente, se houver. |

### Superfícies

| Papel | Token | Claro | Escuro | Onde usar |
|---|---|---|---|---|
| Página | `--bg-base` | `#F4F6FA` | `#0A0F1A` | Fundo do app. Marinho quase preto no escuro; nunca `#000`. |
| Superfície | `--bg-surface` | `#FFFFFF` | `#101827` | Card, painel, corpo da tabela, topbar. |
| Elevada | `--bg-elevated` | `#EAEEF5` | `#17202F` | Input, cabeçalho e rodapé de tabela, linha em hover, nota. |
| Rebaixada | `--bg-sunken` | `#E3E9F1` | `#080D16` | Trilho, well, estado pressionado de botão secundário. |

### Texto e bordas

| Papel | Token | Claro | Escuro | Onde usar |
|---|---|---|---|---|
| Texto | `--fg` | `#0D1522` | `#E8EDF4` | Número, título, corpo. |
| Texto de apoio | `--fg-muted` | `#4A5A6E` | `#9BA9BC` | Parágrafo, rótulo de coluna, descrição. |
| Texto discreto | `--fg-subtle` | `#5D6C7E` | `#78889C` | Caption, unidade, código de conta, placeholder. |
| Borda | `--border` | `#D5DDE8` | `#223046` | Contorno de card, input e tabela. |
| Divisória | `--border-muted` | `#E4EAF2` | `#1A2434` | Hairline entre linhas de tabela e de lista. |
| Borda forte | `--border-strong` | `#B9C6D6` | `#33445E` | Cabeçalho de tabela, rodapé de total, contorno do secundário. |

### Alta, baixa e pendência

| Papel | Token | Claro | Escuro | Onde usar |
|---|---|---|---|---|
| Alta · jade | `--pos` | `#0E6F53` | `#3FB98A` | Variação positiva, crédito, badge "Conciliado". |
| Baixa · tijolo | `--neg` | `#A03027` | `#E0705F` | Variação negativa, débito, atraso, botão destrutivo. |
| Pendência | `--warn` | `#9A6407` | `#E0A33A` | "Em revisão", prazo curto, aviso não bloqueante. |

Todos passam 4,5:1 sobre a superfície do respectivo tema. **Cor nunca informa sozinha:** a
variação sempre carrega triângulo de direção + sinal (`+` / `−`), e o badge sempre carrega um
ponto à esquerda. Quem não distingue matiz lê a forma.

---

## TIPOGRAFIA

Duas famílias, **as duas nativas do sistema operacional**. Nenhuma webfont, nenhum `@import`,
nenhum CDN. A razão é operacional, não estética: painel financeiro abre atrás de VPN corporativa,
em rede de escritório e em máquina antiga. Fonte que não carrega é número que não aparece. Além
disso, a mono nativa é a única garantia de dígito de largura fixa de verdade.

```css
--font-sans: ui-sans-serif, -apple-system, "Segoe UI Variable Text", "Segoe UI",
             Roboto, system-ui, "Helvetica Neue", Arial, sans-serif;
--font-mono: ui-monospace, "SF Mono", SFMono-Regular, Menlo, Consolas,
             "Liberation Mono", "DejaVu Sans Mono", monospace;
```

### Regras

1. **Todo número é mono e tabular.** `font-family: var(--font-mono)` +
   `font-variant-numeric: tabular-nums`. Vale para célula de tabela, KPI, input de valor, tooltip,
   e-mail e PDF. A classe pronta é `.ctj-num`.
2. **Todo número alinha à direita.** Rótulo à esquerda, valor à direita. A vírgula decimal fica no
   mesmo eixo em toda a coluna — é o que permite comparar magnitude sem ler.
3. **Negativo entre parênteses** em valor contábil (`(98.320,10)`), como manda a convenção.
   O sinal de menos fica reservado para variação percentual (`−3,25%`).
4. **Escala:** 36 · 28 · 22 · 18 · 17 · 16 · 14 · 13 · 12 px. Não existe display de 72px — a tela é
   para trabalhar. **Piso absoluto de 12px**, corpo em 16px.
5. **Tracking:** −0,02em no display, −0,01em em título de 22 a 28px, **zero** no corpo e na célula,
   +0,14em em caixa-alta pequena (overline e cabeçalho de coluna).
6. **Pesos:** 400 corpo · 500 rótulo, botão e badge · 600 título e cabeçalho · 700 KPI, total e
   wordmark. Nada acima de 700.
7. **Line-height:** 1,55 no corpo, 1,25 no título, 1,2 na célula de tabela e no badge.

---

## ESPAÇO E DENSIDADE

Base de 4px. O passo de trabalho é 8 e 12px, não 24. **Densidade é decisão de marca:** linha de
34px, recuo lateral de 12px na célula e hairline de 1px cabem 24 contas numa tela de notebook sem
rolar. Um card de canto 16px com respiro de 32px cabe seis — e o analista rola quatro vezes para
bater um total.

| Token | Valor | Papel |
|---|---|---|
| `--row-h` | 34px | Altura padrão da linha de dado. |
| `--row-h-compact` | 28px | Modo adensado, para tabela com mais de 40 linhas. |
| `--section-y` | 48px | Respiro entre blocos. |
| `--container-prose` | 736px | Texto corrido — nunca mais largo que isso. |
| `--container-app` | 1280px | Grade do painel. |

---

## FORMA: RAIO, HAIRLINE E ELEVAÇÃO

- **Raio entre 3 e 6px, sempre.** `3px` badge e chip · `4px` botão e input · `5px` card e painel ·
  `6px` tabela e modal. `--radius-full` existe **só** para indicador circular e avatar.
  Raio grande arredonda a autoridade do número.
- **Hairline de 1px é lei.** Peso maior só no cabeçalho e no rodapé de total de tabela, e mesmo
  ali é 1px em `--border-strong`, não 2px.
- **Elevação depende do tema.** No claro é sombra difusa, com Y maior que metade do blur e alfa
  baixo. No escuro, sombra preta sobre marinho não existe: quem separa plano é a borda mais clara,
  e por isso as sombras do tema escuro carregam um `0 0 0 1px` branco a 3%.
- **Proibido:** sombra dura (`0 4px 4px rgba(0,0,0,.5)`), sombra interna, trilho de acento colorido
  na lateral de card, gradiente decorativo em área grande.

---

## COMPONENTES E ESTADOS

### Botão

Altura 32px, raio 4px, peso 500, fonte 14px. Quatro variantes:

| Variante | Papel | Repouso |
|---|---|---|
| Primário | O ato irreversível do fluxo. **Um por tela.** | Preenchido em `--action-bg`, texto em `--action-fg`. |
| Secundário | Ação frequente e reversível (exportar, filtrar). | Superfície + borda `--border-strong`. |
| Discreto | Ação de linha, dentro de tabela ou card. | Sem fundo, sem borda, texto `--fg-muted`. |
| Destrutivo | Estorno, exclusão, reabertura de competência. | **Contorno** tijolo, nunca preenchido — preencher botão perigoso convida ao clique. |

Estados: **hover** muda uma propriedade (o fundo) · **foco** é o anel `--ring` de 3px, obrigatório
e nunca removido · **pressionado** aprofunda um passo na rampa · **desabilitado** vai para
`--bg-elevated` com texto `--fg-subtle` e `cursor: not-allowed`.

No tema claro o hover **escurece**; no escuro, **clareia**. Não é simetria de valor — é o que
mantém o contraste do texto em cada fundo.

### Tabela de dados — componente-assinatura nº 1

Linha de 34px · cabeçalho fixo em `--bg-elevated` com caixa-alta de 12px · hairline
`--border-muted` entre linhas · linha em hover com `--row-hover` · linha selecionada com
`--row-select` **e hairline da marca em cima e embaixo** (nunca uma barra lateral) · rodapé de
total em `--bg-elevated` com borda superior forte · rolagem horizontal contida em
`.ctj-tablewrap`, jamais no `body`.

Coluna de variação: `.ctj-delta` com triângulo desenhado em CSS + sinal + cor. A polaridade padrão
é "subir é bom"; em custo, despesa, imposto e inadimplência use **`.ctj-delta--inverse`**, que
mantém a direção do triângulo e troca só a cor. Painel que pinta de verde a despesa estourada está
mentindo com CSS.

### Card de métrica com sparkline — componente-assinatura nº 2

Rótulo (13px, `--fg-muted`) · valor em mono tabular 36px/700 · sparkline SVG de 11 pontos
(`viewBox="0 0 120 34"`, `preserveAspectRatio="none"`, **todo traço com
`vector-effect: non-scaling-stroke`**) · rodapé com período de comparação e delta.
A linha tracejada marca o valor de abertura do período. Sem eixo, sem legenda, sem grade: o
sparkline responde "está subindo?" e nada mais. O ponto final é um subpath de comprimento zero com
`stroke-linecap: round` — vira círculo perfeito mesmo com o eixo X esticado.

### Campo

Altura 32px, raio 4px. **Todo input de valor é mono, tabular e alinhado à direita**
(`.ctj-input--num`). Prefixo de moeda colado no campo, sem borda entre os dois. Erro: borda
`--neg` + mensagem de 12px logo abaixo, com `aria-invalid` e `aria-describedby`. Foco sempre com
anel — `outline: none` sem substituto é proibido.

### Badge

12px, raio 3px, ponto de 5px à esquerda repetindo a informação da cor em forma. Cinco estados de
lançamento: Conciliado (pos) · Em revisão (warn) · Atrasada (neg) · Provisionado (info) ·
Rascunho (neutro).

---

## TEMAS

O Cotejo é o único DS do kit com **os dois temas completos**, e eles foram desenhados separadamente
— nenhum é o outro invertido. A implementação segue quatro camadas, nesta ordem:

```css
:root { /* claro: TODOS os tokens */ }
@media (prefers-color-scheme: dark) { :root { /* escuro automático */ } }
:root[data-theme="dark"]  { /* escuro forçado */ }
:root[data-theme="light"] { /* claro forçado — vence a media query */ }
```

Os dois últimos blocos vêm depois da media query e têm especificidade maior (0,2,0 contra 0,1,0),
então sobrescrevem **nos dois sentidos**. O alternador do showcase grava a escolha em
`localStorage` dentro de `try/catch` (arquivo aberto por `file://` pode bloquear).

**Regra dura:** todo token declarado no bloco escuro existe no `:root`. Token que só existe no
escuro renderiza transparente no claro — e só aparece no tema que ninguém testou.

---

## AS ASSINATURAS DA MARCA

Escritas como receita, não como adjetivo. São elas que fazem o Cotejo reconhecível de longe.

1. **O par que fecha (o mark).** Duas barras horizontais de mesma medida, rentes nas duas pontas,
   em `--brand-ink`, na altura da caixa-alta do wordmark — o filete duplo que a contabilidade
   desenha embaixo de um total encerrado. SVG inline (`viewBox="0 0 18 13"`, duas `rect` de
   `height=2.4` em `y=1.4` e `y=9.2`), nunca imagem. Ao lado, `COTEJO` em caixa-alta com
   `letter-spacing: 0.08em` e peso 700; depois um filete de 1px e o descritor em mono de 12px com
   `letter-spacing: 0.14em`. Em espaço apertado, saem primeiro o descritor e o filete — nunca o
   mark. O favicon é o mesmo par sobre quadrado `#0A0F1A` de raio 6.
2. **O filete duplo na estrutura.** O mesmo par, agora como régua: `.ctj-sectionmark` (1,75rem)
   abre a seção, `.ctj-doubleline` (largura total) fecha o total. Ambos são um bloco de 4px de
   altura com dois `linear-gradient` de 1px presos em `left top` e `left bottom` — sem borda, sem
   `<hr>` default.
3. **O par conferido (`.ctj-match`).** O mark vira dado: a barra de cima é o razão, a de baixo é o
   extrato, com o comprimento em `--match`. Conciliado = as duas do mesmo tamanho, e o glifo
   reverte ao próprio mark. A diferença aparece como **vão**, não só como cor — quem não distingue
   matiz continua lendo o estado. Variantes `--partial`, `--off` e `--none`.
4. **A coluna de variação.** Valor em mono tabular alinhado à direita, e ao lado um triângulo
   desenhado em CSS puro (`border-left/right transparent` + `border-bottom` em `currentColor`)
   seguido do sinal e do número. Direção sempre honesta; cor invertida por
   `.ctj-delta--inverse` quando subir é ruim.
5. **A linha selecionada sem barra lateral.** Fundo em `--row-select` mais
   `box-shadow: inset 0 1px 0 var(--steel-500), inset 0 -1px 0 var(--steel-500)` — dois hairlines
   da marca prendendo a linha em cima e embaixo. É seleção de planilha, não alerta de Bootstrap.

---

## RESSALVAS

1. **Sem fonte proprietária.** A pilha é 100% nativa, por decisão. Se algum dia uma face licenciada
   entrar, ela substitui apenas `--font-sans`; a mono continua nativa, porque é ela que garante o
   dígito tabular.
2. **Sem biblioteca de ícones.** O Cotejo desenha os poucos sinais que usa (mark, triângulo de
   delta, ponto de badge) em CSS ou SVG inline. Se um dia precisar de um conjunto, adote **uma**
   biblioteca de traço (Lucide ou Phosphor) em 1,5px e declare aqui — nunca duas na mesma tela.
3. **Os números do `showcase.html` são fictícios.** Servem de demonstração de formato, não de
   referência contábil.
