# Amparo — Design System

**Posicionamento:** clínica integrada — nutrição, psicologia e fisioterapia no mesmo prontuário.
**Promessa:** cuidado que continua depois da consulta.
**Para quem serve:** clínica multidisciplinar, consultório, nutricionista, psicólogo, fisioterapeuta,
coach de saúde — qualquer negócio que precise transmitir **calma e credibilidade ao mesmo tempo**.
**O que NÃO é:** spa, wellness de banco de imagem, marketplace de saúde, healthtech de dashboard.
Amparo é uma clínica boa: acolhedora e competente, nessa ordem.

**Assinatura:** verde-sálvia profundo `#406D5D` sobre off-white frio `#F0F4F3`.

---

## Índice

| Arquivo | O que é |
|---|---|
| `README.md` | Este manual — marca, voz, fundamentos visuais, regras de componente. |
| `tokens.css` | **A fonte da verdade.** Variáveis e classes `.amp-*`. Nenhum valor visual nasce fora dele. |
| `showcase.html` | A prova visual, standalone. Abre com duplo clique, sem build e sem internet. |
| `SKILL.md` | Frontmatter de skill do Claude Code, com os campos de convenção de design system. |

---

## Quem é a Amparo

A Amparo atende quem já tentou resolver saúde em pedaços: um nutricionista que não fala com o
psicólogo, um fisioterapeuta que não sabe do exame. O acompanhamento dura doze semanas, tem
prontuário único e canal aberto entre consultas.

O paciente típico chega **ansioso e informado**. Ele já pesquisou, já leu coisa demais e desconfia de
promessa. O sistema visual existe para baixar essa ansiedade sem virar "conteúdo de bem-estar":
espaço generoso, texto que explica, números concretos, zero superlativo.

Onde a marca aparece: site, área do paciente, lembrete de consulta, laudo em PDF, ficha de anamnese,
material impresso da recepção.

---

## Fundamentos de conteúdo

- **Idioma:** português do Brasil. Termo clínico só aparece se vier explicado na mesma frase.
- **Pessoa:** **"a gente"** para a clínica (nunca "nós, a Amparo", nunca "a empresa"), **"você"** para
  o paciente. Primeira pessoa do singular só na assinatura de um profissional específico.
- **Caixa:** sentence case em título e botão. Caixa alta só no overline, com `0.16em` de tracking.
  Wordmark é sempre minúsculo.
- **Pontuação:** frase termina em ponto. **Exclamação não existe** na voz da marca — nem uma.
  Travessão (—) para atar oração; nunca hífen duplo.
- **Emoji:** não. Em nenhuma superfície, nem em mensagem de WhatsApp. O que hierarquiza é ícone de
  linha dentro do orbe.
- **Símbolos permitidos:** `·` (separador entre itens), `→` (só dentro de botão), `×` (multiplicação
  em dose e sessão: "3 × por semana"). Nada além disso.
- **Números:** prazo, preço, duração e quantidade sempre em algarismo. "Doze semanas" no texto
  corrido, `12 semanas` quando for dado. Nunca "rápido", "pouco tempo", "investimento acessível".

### Falar / não falar

| Falar | Não falar | Por quê |
|---|---|---|
| **Acompanhamento** | Tratamento milagroso | Promessa de resultado derruba a confiança do paciente informado. |
| **A gente explica** | Consulte um profissional | A clínica é o profissional. Empurrar para fora soa como esquiva. |
| **Leva doze semanas** | Resultado rápido | Prazo concreto acalma; adjetivo de velocidade gera ansiedade. |
| **Se algo não fizer sentido, escreva** | Dúvidas? Fale conosco! | Convite específico é acolhimento; slogan com exclamação é call center. |
| **Equipe integrada** | Time multidisciplinar de excelência | Superlativo empilhado esvazia. O diferencial é o prontuário único. |

### Padrões retóricos

- **Par de contraste com prazo:** afirmação vaga do mercado, depois o número da Amparo.
  *"Não é uma consulta avulsa. São doze semanas com o mesmo prontuário."*
- **Instrução seguida de permissão:** toda orientação difícil vem com um alívio.
  *"Oito horas de jejum. Água pode."*
- **Fecho curto que devolve o controle ao paciente:** *"Você decide o ritmo."* *"Nada fica em pé só
  porque foi escrito."*
- **Nunca:** pergunta retórica no título, chamada com "descubra", contagem regressiva.

---

## Paleta

### Assinatura — verde-sálvia

Sálvia é verde de erva, não verde de farmácia: saturação 26%, luminosidade média-baixa. Acalma porque
não pede atenção. **A assinatura é acento — mire em menos de 10% da tela.**

| Papel | Hex | Onde usar |
|---|---|---|
| `--primary-300` | `#9DBEB2` | Botão desabilitado, fundo de gráfico, ilustração de fundo. |
| `--primary-400` | `#5F9582` | Hover de borda de campo, traço de ilustração. |
| `--primary-500` | `#406D5D` | **A assinatura.** Botão primário, ícone no orbe, número em mono, borda de foco. |
| `--primary-600` | `#31594A` | Hover do botão preenchido, link em texto corrido. |
| `--primary-700` | `#234337` | Pressed, texto pequeno sobre tint, iniciais de avatar. |
| `--primary-wash` | `#E3EEEA` | **O fundo do orbe do ícone.** Também badge padrão e faixa de destaque. |

### Secundária — azul-névoa frio

| Papel | Hex | Onde usar |
|---|---|---|
| `--mist-200` | `#D8E1E8` | Fundo de tag de categoria, faixa de seção alternada. |
| `--mist-400` | `#839CAF` | Traço decorativo, ícone secundário, série 2 de gráfico. |
| `--mist-600` | `#445F74` | Texto de tag, rótulo de especialidade. |

**Nunca em botão.** Secundária em botão são duas marcas brigando na mesma tela.

### Neutros e superfícies

| Papel | Hex | Onde usar |
|---|---|---|
| `--bg-base` | `#F0F4F3` | A página. Off-white **frio**, viés azul-esverdeado. |
| `--bg-card` | `#F9FBFA` | Card, seção alternada. |
| `--bg-elevated` | `#FFFFFF` | Input, popover, menu, card em hover. |
| `--bg-overlay` | `rgba(31,46,41,.45)` | Fundo de modal. |
| `--border` | `#C1D1CC` | Borda padrão de campo e de container. |
| `--border-muted` | `#E0E6E4` | Divisória de lista, borda de card. |

A hierarquia sobe do fundo para a frente: página mais escura, card mais claro, elevado branco.
Inverter isso achata a tela inteira.

### Texto

| Papel | Hex | Contraste sobre `--bg-base` | Onde usar |
|---|---|---|---|
| `--fg` | `#1F2E29` | 12,8:1 | Corpo e títulos. |
| `--fg-muted` | `#4C625B` | 5,9:1 | Parágrafo de apoio, descrição de card. |
| `--fg-subtle` | `#5A726B` | 4,7:1 | Label, legenda, placeholder, copyright. |
| `--fg-on-primary` | `#FFFFFF` | 5,9:1 sobre `#406D5D` | Texto dentro de botão preenchido. |

### Semânticas

| Papel | Hex | Tint | Onde usar |
|---|---|---|---|
| `--success` | `#2C6D31` | `#DDEEDE` | Exame liberado, pagamento confirmado, laudo assinado. |
| `--warning` | `#8C5717` | `#F5EAD6` | Jejum, prazo, pendência de documento. |
| `--destructive` | `#943844` | `#F5E5E7` | Cancelar consulta, excluir dado, desmarcar. |
| `--info` | `#315672` | `#DFE9F1` | Orientação neutra, aviso da recepção. |

**A armadilha que este DS evita:** a assinatura é verde, então o sucesso **não** pode ser o mesmo
verde. `#2C6D31` está 34° de matiz longe da sálvia e com o dobro da saturação — lê como verde-folha,
não como a cor da clínica. Sem isso, o paciente perde a diferença entre "ação da Amparo" e "deu certo".

---

## Tipografia

**Duas famílias, ambas em pilha nativa. Zero webfont, zero `@import`, zero CDN.** A página abre já
composta, não pisca em Times, e funciona no tablet da recepção sem internet.

```css
--font-sans:  "Avenir Next", Avenir, "Segoe UI", system-ui, -apple-system,
              "Helvetica Neue", Helvetica, Arial, sans-serif;
--font-mono:  ui-monospace, "SF Mono", SFMono-Regular, Menlo, Consolas,
              "Liberation Mono", monospace;
--font-display: var(--font-sans);   /* apelido de propósito */
```

**Por que humanista:** Avenir e Segoe UI têm terminações abertas e "a" de dois andares. O texto soa
falado, não impresso. Uma grotesca geométrica fria (Inter, Space Grotesk) faz a mesma frase soar como
termo de consentimento.

`--font-display` é apelido de `--font-sans` **de propósito**: a marca fala com uma voz só, mudando
peso e tamanho, nunca família.

### Regras

- **Peso de título é 500.** Peso 600 só em botão, label e ênfase curta. **Peso 700 só em número.**
  Peso 800 não existe neste sistema. A marca não grita.
- **Tracking:** `-0.025em` no display (≥36px), `-0.012em` no heading, `0` no corpo, `+0.16em` no
  overline em caixa alta. Título grande com tracking 0 parece frouxo; caixa alta pequena com
  tracking 0 parece amassada.
- **Entrelinha do corpo é 1.7** — mais alta que o padrão de produto, de propósito. Texto de saúde é
  lido devagar, às vezes com medo.
- **Medida de linha:** 65 caracteres. `--container-prose` é 44rem justamente por isso.
- **Corpo em 16px, piso em 12px.** Nada abaixo disso, em nenhuma superfície.
- **Mono onde o alinhamento importa:** horário, dose, código do paciente, número de sessão.
  Sempre com `font-variant-numeric: tabular-nums` — `09h00` e `14h30` precisam ter a mesma largura,
  senão a coluna da agenda dança.

### Escala

`64 · 48 · 36 · 28 · 22 · 18 · 16 · 14 · 12` (px). Dez degraus contando `--fs-body-lg`.

---

## Espaço

Base 4px. **Espaço é o que comunica calma** — denso lê como pronto-socorro, arejado lê como
consultório com hora marcada. A Amparo é arejada, e isso é decisão de marca, não sobra de layout:

- `--section-y: 96px` entre blocos.
- `32px` de respiro interno no card, `40px` no card de destaque.
- `--container-prose: 704px` · `--container-content: 1152px` · `--container-wide: 1280px`.

Valor fora da escala (13px, 27px) é o que faz uma tela parecer "quase certa" sem ninguém saber apontar.

---

## Forma — raio e elevação

### Raio

**Nenhum canto reto em lugar nenhum.** O raio cresce com o elemento:

| Token | Valor | Onde |
|---|---|---|
| `--radius-sm` | 10px | Tag, chip |
| `--radius-md` | 14px | Input, select, textarea |
| `--radius-lg` | 20px | Card padrão |
| `--radius-xl` | 24px | Card de destaque, card de informação, cartão de horário |
| `--radius-2xl` | 28px | Painel, modal, container grande |
| `--radius-full` | pílula | **Botão**, orbe, avatar, badge |

**Botão é pílula. Sempre.** É decisão de marca: pílula é a forma mais amistosa que existe, e nenhuma
clínica do setor usa pílula com sálvia. Um único raio aplicado em tudo (o clássico "8px em tudo")
achata a hierarquia — botão, card e modal passam a dizer que estão no mesmo nível, e não estão.

### Elevação

**Decisão declarada: a marca usa sombra, não glow.** E a sombra **não é preta** — é a própria tinta
da marca (`#1F2E29`) em alpha mínimo. Preto puro sobre off-white frio deixa um halo cinza-sujo na
borda do card.

| Token | Valor | Onde |
|---|---|---|
| `--shadow-sm` | `0 2px 6px -2px rgba(31,46,41,.06)` | Card em repouso, botão preenchido |
| `--shadow-md` | `0 14px 30px -18px rgba(31,46,41,.16)` | Card em hover |
| `--shadow-lg` | `0 28px 56px -28px rgba(31,46,41,.20)` | Card de destaque, painel de formulário |
| `--shadow-xl` | `0 40px 80px -40px rgba(31,46,41,.24)` | Modal |
| `--shadow-inset` | `none` | Declarado só para dizer: **a marca não usa**. |

Sombra dura (`0 4px 4px rgba(0,0,0,.5)`) é proibida. Y sempre maior que blur/2, alpha sempre baixo.

---

## Movimento

Personalidade: **séria e calma**. Entrada e mudança de estado; nada de bounce, nada de spring, nada
de overshoot.

- `--ease-smooth: cubic-bezier(.4,0,.2,1)` é o padrão.
- `--dur-fast: 160ms` (foco, cor de link) · `--dur-base: 240ms` (hover) · `--dur-slow: 420ms` (painel).
  240ms em vez dos 150ms de produto: a marca não tem pressa.
- **Hover muda no máximo duas propriedades** — cor de borda e sombra, e ponto.
- `prefers-reduced-motion: reduce` está no `tokens.css` e é obrigatório em qualquer artefato.

---

## Componentes e estados

### Botão

| Variante | Repouso | Hover | Pressionado | Foco | Desabilitado |
|---|---|---|---|---|---|
| **Primário** | fundo `500`, texto branco, `shadow-sm` | fundo `600`, `shadow-md` | fundo `700`, sem sombra | `--ring` (anel sálvia .28) | fundo `300`, sem sombra |
| **Secundário** | branco, borda `--border`, texto `600` | borda `400`, texto `700` | fundo `--primary-wash` | `--ring` | texto e borda apagados |
| **Sutil** | só texto `600` | fundo `--primary-a08` | fundo `--primary-a16` | `--ring` | texto `--fg-subtle` |
| **Perigo** | fundo `--destructive`, texto branco | `#7C2E38` | mais escuro, sem sombra | anel vermelho .30 | rosa apagado |

**Uma ação principal por tela.** Se aparecer um segundo botão primário, um dos dois vira secundário.

### Campo

- Repouso: fundo branco, borda `--border`, raio 14px.
- Hover: borda `--primary-300`.
- **Foco: borda `--primary-500` + `--halo`** (anel de sálvia a 8%, sem blur). O halo é a elevação
  afetiva da marca — lê como colo, não como alerta.
- Erro: `aria-invalid="true"` pinta a borda de `--destructive`; a mensagem vem abaixo, em 12px,
  escrita como instrução ("Falta a parte depois do arroba"), nunca como acusação ("E-mail inválido").
- Desabilitado: fundo `--bg-card`, texto `--fg-subtle`, cursor `not-allowed`.

Foco visível **nunca** é removido. `outline: none` sem substituto é o bug de acessibilidade mais
comum que existe.

### Card

Fundo `--bg-card`, borda `--border-muted`, raio 20px, respiro 32px, `--shadow-sm`.
Hover: borda `--primary-a28` + `--shadow-md`. **Sem lift, sem escala.**

### Badge

Pílula, 12px, peso 600, com um ponto de 7px em `currentColor` antes do texto. Fundo é sempre o tint
da semântica, texto sempre a cor cheia.

---

## As assinaturas da marca

Três detalhes reproduzíveis. Sem eles, trocar nome e cor transformaria a Amparo em qualquer outra.

### 1. O orbe — card de informação com ícone em círculo tint

O componente característico da direção, e o que identifica a marca a três metros.

**Receita:** círculo **sólido** de 56px em `--primary-wash`, `border-radius: 9999px`, ícone de linha
de 24px em `--primary-500` centralizado. Título de 22px peso 500 abaixo, texto de apoio em
`--fg-muted`. Gap de 20px entre orbe e texto.

**Nunca:** borda no orbe, gradiente no orbe, quadrado arredondado no lugar do círculo, ícone
preenchido, orbe menor que 40px (`--icon-orb-sm`) ou maior que 56px.

Variantes: `--mist-200` para categoria, tint semântico para estado. A variante padrão é sálvia.

### 2. O arco — wordmark

Arco aberto para cima (um colo) com um ponto suspenso acima, seguido de `amparo` em caixa baixa,
peso 500, tracking `-0.015em`.

**Receita:** `path M4 11 C4 20 20 20 20 11` num viewBox 24, traço 2,2px, ponta arredondada, mais um
círculo de raio 2,4 em (12; 6,2) preenchido. Largura do arco = 1,15em do tipo. Cor `--primary-500`
no positivo, `--primary-300` no invertido.

**Nunca:** wordmark em caixa alta, em itálico, ou em peso 700 fora do favicon.

### 3. O cartão de horário

Hora em mono tabular à esquerda (22px, peso 700, `--primary-500`), dia da semana em caixa alta 12px
abaixo, filete vertical de 1px separando, e o corpo à direita. Raio 24px, fundo branco.

**É o único filete vertical do sistema** — existe porque separa duas informações de naturezas
diferentes (quando × o quê). Filete em qualquer outro lugar é acidente.

---

## Iconografia

- **Biblioteca única: Lucide** (estilo de linha). Em artefato solto, desenhe o SVG à mão seguindo o
  mesmo padrão: `stroke="currentColor"`, `stroke-width="1.6"`, `stroke-linecap="round"`,
  `stroke-linejoin="round"`, viewBox 24.
- **Tamanhos:** 18px dentro de nota e botão · 24px dentro do orbe · 40px em tile de app.
- **Cor:** herda do container. Dentro do orbe é `--primary-500`; dentro de nota semântica é a cor da
  semântica; sozinho no texto é `--fg-subtle`.
- **Não usar:** ícone preenchido, ícone de duas cores, ícone de outra biblioteca na mesma tela,
  ilustração 3D, foto de banco de imagem com jaleco e sorriso.
- **Nunca emoji.** Um overline em caixa alta com tracking largo resolve hierarquia melhor.

---

## Layout

- Hero em duas colunas assimétricas (`1.15fr / 0.85fr`), texto à esquerda.
- Do hero para baixo, **tudo alinhado à esquerda**. Página inteira centralizada não tem hierarquia.
- Grade de cards: 3 colunas em desktop, 2 em tablet, 1 em celular.
- Cabeçalho fixo de 72px com `backdrop-filter: blur(12px)` sobre `rgba(240,244,243,.88)`.
- Tabela larga vive dentro de um container com `overflow-x: auto` — o corpo da página **nunca**
  rola na horizontal.

---

## Antipadrões proibidos nesta marca

- Fundo bege ou creme. O off-white da Amparo é **frio**, com viés azul-esverdeado. Papel quente ao
  lado de sálvia deixa a marca com aparência encardida.
- Peso 700 ou 800 em título.
- Sálvia como cor de sucesso.
- Barra de acento colorida na lateral de card arredondado (a barra reta briga com o canto e sobra um
  degrau visível). O card diferencia por superfície e por orbe.
- Numeração 01/02/03 como decoração onde não existe sequência real.
- Gradiente ocupando área grande. `--gradient-wash` existe só para painel de destaque, e é wash de
  sálvia para névoa — nunca roxo-para-azul.
- Emoji, exclamação, tudo centralizado, `border-radius: 8px` em absolutamente tudo.

---

## Ressalvas e substituições

1. **Avenir Next não está em toda máquina.** No Windows a pilha cai em Segoe UI; no Linux, em
   `system-ui`. As três são humanistas o suficiente para o sistema não se descaracterizar. **Foi
   decisão, não descuido:** webfont em clínica significa página que pisca no 4G da sala de espera.
   Se um dia a marca quiser uma face licenciada, troque **só** `--font-sans` e mantenha a pilha nativa
   como fallback final.
2. **Não há tema escuro.** Escuro em saúde lê como clínica de emergência. Se um painel interno
   precisar de escuro, ele é outro produto e pede outro conjunto de superfícies — não a inversão
   destes tokens.
3. **Sem assets binários.** O wordmark, o favicon e todos os ícones são SVG inline, escritos no
   `showcase.html`. Copie de lá; não gere um PNG.
4. **Contraste conferido** com fórmula WCAG 2.1 sobre `--bg-base` e `--bg-card`. Todo texto passa
   4.5:1; branco sobre `--primary-500` dá 5,9:1.
