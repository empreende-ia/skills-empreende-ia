# Fervo — Design System

**Posicionamento:** comida de rua feita na hora, entregue quente.
**Tagline:** "Fome não espera carregar."
**Para quem:** quem está com fome agora — no celular, na fila, no sofá às 23h.
**O que NÃO é:** restaurante de fine dining, marca artesanal de linho e serifada, app de saúde.
**Onde a marca aparece:** app e site de delivery, cardápio impresso, embalagem, fachada, story.

---

## 1. Quem é a Fervo

A Fervo é uma rede pequena de comida de rua: hambúrguer na chapa, porções pra dividir,
bebida gelada. Vende pelo delivery, pelo balcão e pela janela da esquina. O que a marca
precisa fazer é simples e brutal: **dar vontade em menos de dois segundos e não atrapalhar
o pedido**.

Por isso o sistema inteiro é organizado em torno de três decisões:

1. **A cor é estrutura, não acabamento.** Bloco de tomate saturado carrega seção inteira.
   Marca que se lê da calçada e no story não tem filete colorido — tem área de cor.
2. **O preço é elemento gráfico.** Não é um número no fim do card: é o segundo maior
   elemento da tela, com tratamento próprio (moeda pequena, inteiro gigante, centavos
   elevados, tabular-nums).
3. **Barulho no lugar certo.** O letreiro é condensado e pesado. O texto que explica é
   uma sans neutra, corrida, sem drama. Uma marca de rua desleixada perde a venda;
   uma marca de rua tímida some.

### As assinaturas (o que torna a Fervo reconhecível de longe)

| # | Assinatura | Receita reproduzível |
|---|---|---|
| 1 | **O "O" que é um disco** | O wordmark é `FERV` + um círculo de `0.74em` em `--primary-500` com miolo de 40% do diâmetro na cor do papel. Lê como chapa quente vista de cima. É o símbolo isolado, o favicon e o avatar. |
| 2 | **Canto assimétrico** | `--radius-asym: 32px 8px 32px 8px` — só em card de produto e bloco de hero. Nunca em botão, input, badge ou lista. É assinatura porque é raro. |
| 3 | **Preço com moeda alta e centavo elevado** | `R$` a `0.34em` alinhado ao topo, inteiro a `1em` em condensada 900, centavos a `0.4em`, `font-variant-numeric: tabular-nums`. Preço antigo riscado sempre **acima** do novo, nunca ao lado. |
| 4 | **Faixa listrada de oferta** | `repeating-linear-gradient(-45deg, #d92d0b 0 22px, #c02708 22px 44px)` com texto condensado em caixa alta deslizando. Uma por página, sempre logo abaixo do hero. |

---

## 2. Paleta

### Assinatura — tomate

| Papel | Hex | Onde usar |
|---|---|---|
| `--primary-300` | `#ff8a66` | Highlight e overline **sobre** bloco tomate ou bloco tinta. Nunca sobre papel. |
| `--primary-400` | `#ff5c33` | Hover de elemento em superfície escura; ponta clara de gradiente. |
| `--primary-500` | `#d92d0b` | **A assinatura.** Bloco de seção, faixa, selo, botão de comprar, borda ativa. Cor de **fundo**. |
| `--primary-600` | `#b32209` | Estado pressionado **e** texto/link/preço em destaque sobre papel (6,6:1). |
| `--primary-700` | `#8a1907` | Texto miúdo sobre lavagem clara, borda forte, cauda de gradiente. |
| `--primary-on-light` | = `--primary-600` | Atalho de intenção. Se é **texto**, use este. Se é **fundo**, use o `-500`. |

Alfas nomeados: `--primary-alpha-06` (chip, zebra), `--primary-alpha-14` (badge soft, grifo do
preço), `--primary-alpha-32` (anel de foco), `--primary-alpha-45` (sombra tingida).
Nunca use `opacity` no elemento — ela apaga o texto filho junto.

### Neutros e superfícies

| Papel | Hex | Onde usar |
|---|---|---|
| `--bg-base` | `#fff6f1` | A página. Papel quente — a temperatura acompanha a assinatura. |
| `--bg-surface` | `#ffffff` | Card, painel, linha de cardápio, input. |
| `--bg-elevated` | `#ffe9de` | Área de mídia do produto, chip, campo desabilitado, amostra. |
| `--bg-ink` | `#241512` | Bloco escuro quente: rodapé, seção de inversão, embalagem, botão secundário. |
| `--bg-ink-soft` | `#3a221c` | Card dentro do bloco escuro, hover do botão tinta. |
| `--bg-overlay` | `rgba(36,21,18,.62)` | Fundo de modal. |

> A base não é branco puro de propósito: `#fff` ao lado de um bloco `#d92d0b` estoura e
> deixa a borda do bloco vibrando. `#fff6f1` segura a cor.

### Texto e bordas

| Papel | Hex | Onde usar |
|---|---|---|
| `--fg` | `#241512` | Título e corpo. Tinta marrom-preta, nunca `#000` (halação ao lado do tomate). |
| `--fg-muted` | `#6b4a40` | Parágrafo longo, descrição de produto. 7,4:1 sobre a base. |
| `--fg-subtle` | `#8a6553` | Label, caption, placeholder, preço antigo. 4,8:1 — é o piso. |
| `--fg-on-primary` | `#ffffff` | Todo texto sobre bloco tomate, inclusive corpo (4,8:1). |
| `--fg-on-primary-soft` | `#ffe0d4` | **Só** em ≥ 24px, ou ≥ 18,66px em negrito (4,3:1). |
| `--fg-on-ink` / `--fg-on-ink-muted` | `#fff6f1` / `#d9bdb2` | Título e parágrafo sobre bloco tinta. |
| `--border` | `#ebd5c9` | Borda padrão de card e input. |
| `--border-muted` | `#f6e5dc` | Divisória de lista de cardápio. |
| `--border-ink` | `#241512` | Régua grossa sob o título de seção, contorno de botão terciário. |

### Semânticas

| Papel | Hex | Onde usar |
|---|---|---|
| `--success` | `#0f7b3f` | Pedido confirmado, saiu para entrega. |
| `--warning` | `#b26a00` | Estoque baixo, atraso na cozinha. |
| `--danger` | `#a11043` | Erro de formulário, cancelamento, pagamento recusado. |
| `--info` | `#1b6aa8` | Horário, aviso neutro, informação de raio de entrega. |

> **A armadilha desta marca:** a assinatura já é vermelha. Se o erro fosse o mesmo vermelho,
> "pedir" e "deu ruim" ficariam indistinguíveis. Por isso o erro é carmim (`#a11043`, hue ~340°,
> ~30° longe do tomate) — e **sempre** vem com ícone e texto. Cor sozinha nunca comunica estado.

Cada semântica tem sua lavagem clara (`--success-wash`, `--warning-wash`, `--danger-wash`,
`--info-wash`) para fundo de badge e de alerta.

### Secundárias

| Papel | Hex | Onde usar |
|---|---|---|
| `--accent-mostarda` | `#e8a33d` | Categoria "porções", pão e fritura na ilustração, selo alternativo. |
| `--accent-limao` | `#7fb800` | Categoria "bebidas e leves", alface e canudo na ilustração. |
| `--accent-uva` | `#6b2d5c` | Categoria "sobremesas". |

**Regra dura:** secundária nunca aparece em botão, CTA, link ou foco. Ela existe para
categoria e ilustração. No botão, ela vira uma segunda marca disputando com a primeira.

---

## 3. Tipografia

Duas famílias, **as duas em pilha nativa do sistema**. Sem `@import`, sem CDN, sem webfont —
o design system tem que abrir com duplo clique, offline.

```css
--font-display: 'Arial Narrow', 'Helvetica Neue Condensed', 'Liberation Sans Narrow',
                'Nimbus Sans Narrow', 'Roboto Condensed', 'Franklin Gothic Medium',
                Impact, system-ui, sans-serif;
--font-sans:    -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Helvetica Neue',
                Helvetica, 'Liberation Sans', Arial, sans-serif;
```

### Regras

- **Display é letreiro, não texto.** Serve título de seção, nome de produto, preço e faixa.
  Nunca parágrafo: face estreita cansa na terceira linha.
- **Caixa alta** em `display-2xl`, `display-lg`, nome de produto, badge, selo e faixa.
  Caixa de frase em `display-md` e em tudo que explica.
- **Tracking negativo no display, positivo no overline.** `--tracking-display: -0.035em`,
  `--tracking-heading: -0.02em`, corpo em `0`, overline em `0.16em`.
  Título grande com tracking 0 parece frouxo; caixa-alta pequena com tracking 0 parece amassada.
- **Line-height do display é 0.92.** A condensada aguenta linha colada — é isso que
  transforma três linhas num letreiro em vez de três frases.
- **Corpo em 16px, sempre.** Nada abaixo de 12px em texto. A única exceção é o `__nota`
  do selo (10px), que é elemento gráfico, não conteúdo.
- **Número é tabular.** Todo preço leva `font-variant-numeric: tabular-nums`. Número que
  dança de largura destrói uma lista de cardápio.

### Escala

`display-2xl` 88 · `display-xl` 68 · `display-lg` 52 · `display-md` 40 · `heading-lg` 32 ·
`heading-md` 24 · `heading-sm` 20 · `body-lg` 18 · `body` 16 · `body-sm` 14 · `caption` 12.

Abaixo de 900px a escala encolhe (`display-2xl` vira 60px, depois 45,6px em 560px) via
redeclaração das variáveis no media query — não via classe nova.

---

## 4. Componentes e estados

### Botão — a hierarquia é rígida

| Variante | Quando | Estados |
|---|---|---|
| `.fv-btn--primary` | **Comprar.** Adicionar, finalizar pedido. **Um por tela.** | hover: `-600` + `translateY(-2px)` · pressed: `-700` + volta ao chão + sombra menor · foco: `--ring` · disabled: troca para `--bg-elevated` |
| `.fv-btn--ink` | Ação importante que não é comprar: ver cardápio, rastrear pedido. | hover: `--bg-ink-soft` + lift · pressed: `#150b09` |
| `.fv-btn--outline` | Terciário: filtro, "continuar comprando". | hover: lavagem `alpha-06` + borda tomate + texto `-600` |
| `.fv-btn--ghost-on-primary` | Dentro de bloco tomate. | hover: `rgba(255,255,255,.16)` · foco: `--ring-on-primary` |

**Regras de estado que valem para tudo:**

- **Desabilitado troca de superfície, não de opacidade.** `opacity: .5` apaga o texto junto e
  reprova contraste. O botão desabilitado vira `--bg-elevated` com texto `--fg-subtle`.
- **Foco é obrigatório e visível.** `--ring` (3px de `alpha-32`) sobre papel,
  `--ring-on-primary` (3px de branco a 72%) sobre tomate. `outline: none` sem substituto
  é o bug de acessibilidade mais comum que existe.
- **Hover muda no máximo duas propriedades.** Cor de fundo + 2px de lift, e ponto.
- **Motion é curto.** `--dur-fast: 120ms` em hover e foco, `--dur-base: 220ms` em estado.
  `--ease-pop` (overshoot leve) é permitido porque a marca é enérgica — mas nada acima de 420ms
  e nada que pisque. `prefers-reduced-motion` zera transições e para a faixa.

### Card de produto — o componente característico

```
.fv-produto
├── .fv-produto__midia      fundo --bg-elevated, ilustração ou foto sangrando
│   └── .fv-produto__selo   canto superior direito, girado -8°
└── .fv-produto__corpo
    ├── .fv-badge--soft     categoria (align-self: flex-start — badge é pill, não barra)
    ├── .fv-produto__nome   display, caixa alta, line-height 1.05
    ├── .fv-produto__desc   body-sm, --fg-muted, 2 linhas
    └── .fv-produto__rodape preço à esquerda · botão "Adicionar" à direita
```

- Raio `--radius-asym`, borda de 2px, `overflow: hidden`.
- Hover: borda vira `--primary-500`, sombra vira `--shadow-pop` (tingida de tomate),
  `translateY(-4px)`. `:focus-within` faz a mesma borda com `--ring`.
- Preço antigo riscado fica em bloco próprio **acima** do preço novo. Ao lado, os dois "R$"
  colidem e ninguém sabe qual é qual.

### Selo — a promessa curta

Círculo de 5,5rem, girado `-8deg`, com anel tracejado interno (`inset: 7px`).
Carrega no máximo duas linhas em caixa alta: `-30% / só hoje`, `NOVO / na chapa`, `FRETE / grátis`.
Variantes: `--ink` (tinta), `--mostarda` (categoria), `--estrela` (starburst por `clip-path`).

**A estrela é reservada:** uma por tela, e só quando a oferta é real. Duas estrelas na mesma
página transformam a marca em panfleto.

### Campo

Borda de 2px `--border`, raio `--radius-md`, altura confortável (padding `.875rem 1rem`).
Hover escurece a borda; foco vira tomate + `--ring`; erro vira `--danger` **com mensagem
abaixo em texto**, nunca só a borda vermelha.

### Badge

Pill em caixa alta, 12px, tracking `.06em`. `--primary` (oferta), `--soft` (categoria),
`--ink` (modalidade), + as quatro semânticas. Badge nunca estica: dentro de um flex column,
sempre `align-self: flex-start`.

### Bloco de cor — o que estrutura a página

`.fv-bloco--tomate`, `.fv-bloco--ink`, `.fv-bloco--papel`. Raio `--radius-xl` (ou `--radius-asym`
no hero). É o bloco que dá identidade à página — uma página Fervo sem bloco de cor é uma
página qualquer com um botão vermelho.

---

## 5. Forma, elevação e espaço

- **Raio proporcional ao elemento:** chip 8 · botão/input 14 · card 22 · bloco 32 · selo/badge full.
  Um valor único em tudo achata a hierarquia.
- **Assimetria é rara:** `--radius-asym` só em card de produto e hero; `--radius-asym-alt`
  no cartão que se sobrepõe ao bloco.
- **Elevação é sombra, não glow.** Fundo claro pede sombra: difusa, Y maior que blur/2,
  alpha baixo, tingida de marrom (`rgba(60,20,10,…)`) para não sujar o papel quente.
  `--shadow-pop` (tingida de tomate) é exclusiva de elemento de compra.
- **Espaço base 4px.** `--section-y: 5rem` entre blocos, containers em 44rem (texto),
  72rem (grade), 82rem (teto). Densidade média: grade de produto junta, página de produto arejada.

---

## 6. Iconografia e ilustração

- **Biblioteca única: Lucide** (stroke 2px, `stroke-linecap: round`), 16px em pill,
  20–24px em botão e lista, 28–32px em card. Cor: `--primary-on-light` sobre papel,
  `--fg-on-primary` sobre tomate. **Nunca duas bibliotecas na mesma tela.**
- **Em artefato standalone, ícone é SVG inline** copiado de lucide.dev. Nada de CDN:
  o arquivo precisa abrir offline.
- **Ilustração de produto é chapada**, com as cores da paleta (tomate, mostarda, limão,
  tinta), sem gradiente, sem sombra, sem contorno. Serve de substituta quando não há foto.
- **Foto real ganha da ilustração sempre.** Comida fotografada, sangrando até a borda da
  área de mídia. Banco de imagem genérico está proibido — vê-se de longe que não é a casa.
- **Zero emoji.** Nem no texto, nem como marcador de seção. Símbolos permitidos: `·` (separador),
  `—` (travessão), `◆` (separador da faixa de oferta), `×` (multiplicação em "2×1").

---

## 7. VOZ

A Fervo fala como quem está atrás do balcão: direto, sem cerimônia e sem enrolação.
Cordial porque é gente atendendo gente, nunca bajulador.

### Falar / não falar

| Falar | Não falar |
|---|---|
| "Feito na hora" | "Preparado com carinho e dedicação" |
| "R$ 34,90" | "A partir de R$ 34,90" |
| "Chega em 30 minutos" | "Entrega super rápida" |
| "Acabou hoje" | "Produto temporariamente indisponível" |
| "Dois de 120 g na chapa" | "Uma explosão de sabor inesquecível" |

### Regras de escrita

- **Pessoa:** segunda pessoa, "você". A casa fala de si como "a gente" — informal, nunca "nós".
  Nada de terceira pessoa institucional ("a Fervo informa que…").
- **Frase:** curta, verbo na frente, uma ideia por frase. Ponto final sempre, inclusive em
  frase de uma palavra: *"Quente."* *"Na porta."*
- **Pontuação:** travessão (`—`) para atar oração. Nunca reticências, nunca ponto de
  exclamação em texto corrido — a energia vem do bloco de cor e do tamanho do tipo,
  não do teclado.
- **Preço:** sempre por extenso e completo, com centavos. "R$ 34,90", nunca "34" nem
  "a partir de". Taxa de entrega aparece **antes** de confirmar, nunca depois.
- **Prazo é promessa.** Se o texto diz 30 minutos, o sistema tem que cumprir 30 minutos.
  Promessa de prazo que a operação não sustenta destrói a marca mais rápido que qualquer
  erro visual.
- **Caixa alta** só em letreiro, badge, selo e faixa. Frase inteira em caixa alta no corpo
  do texto é grito, e grito é desleixo.
- **O que nunca aparece:** emoji · "imperdível" · "sabor inesquecível" · "clique aqui" ·
  contagem regressiva · "últimas unidades" quando não é verdade · lorem ipsum ·
  nome de produto em inglês sem necessidade ("smash burger" pode; "our signature blend" não).

---

## 8. Ressalvas e substituições

1. **Fonte.** O sistema roda em pilha nativa de propósito (material de curso, zero
   dependência). Em produção com orçamento de fonte, a display natural é uma condensada
   real — **Archivo Expanded** não serve, procure **Oswald**, **Anton** ou uma condensada
   paga de verdade — e o texto pode virar **Switzer** ou **Onest**. Ao trocar, mantenha
   `line-height: 0.92` e o tracking negativo: é isso que faz o letreiro, não a fonte em si.
2. **`Arial Narrow` não tem peso 900 real** em todo sistema; o navegador sintetiza o bold.
   Fica correto na tela, mas em impresso confira a versão instalada antes de fechar arte.
3. **Fotografia.** Este kit entrega ilustração chapada como substituta. Assim que houver foto
   real da comida, ela ganha — e a `--produto__midia` deve receber a foto sangrando,
   sem raio próprio (o `overflow: hidden` do card já corta).
4. **`--fg-on-primary-soft` (`#ffe0d4`) reprova em texto pequeno** sobre tomate (4,3:1).
   Ele existe só para título e subtítulo grandes. Em corpo sobre tomate, use branco puro.

---

## 9. Arquivos

| Arquivo | O que é |
|---|---|
| `tokens.css` | **Fonte da verdade.** Variáveis + classes utilitárias `.fv-*`. Nenhum valor visual nasce fora daqui. |
| `showcase.html` | A prova visual, standalone e offline. Abra quando precisar decidir "como isso deveria parecer". |
| `README.md` | Este manual. |
| `SKILL.md` | Frontmatter para instalar como skill do Claude Code. |
