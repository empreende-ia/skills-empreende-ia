# Anatomia de tokens — o inventário obrigatório

Um design system é a lista abaixo, resolvida. Componente é consequência.
Grupo que você não decidir agora, alguém decide depois no meio de um componente — e aí não é mais
sistema, é remendo.

**Regra de ouro do nome:** token tem nome de **papel**, nunca de **valor**.
`--fg-muted` sobrevive a uma troca de paleta. `--cinza-claro` vira mentira no primeiro rebrand.

---

## 1. Cor

### 1.1 Assinatura — 5 tons, no mínimo

```css
--primary-300: /* highlight, ponta de gradiente, texto sobre fundo escuro */
--primary-400: /* hover, estado claro */
--primary-500: /* A ASSINATURA — CTA, ícone, foco, acento */
--primary-600: /* pressed */
--primary-700: /* cauda de gradiente, texto pequeno sobre fundo claro */
```

**Por que 5 e não 10:** você precisa de um tom pra hover, um pra pressed e um pra texto pequeno em
fundo claro. Dez tons viram dez decisões arbitrárias no componente.

### 1.2 Neutros e superfícies — os dois temas, sempre

```css
--bg-base       /* a página */
--bg-card       /* card, seção alternada */
--bg-elevated   /* input, card em hover, popover, menu */
--bg-overlay    /* fundo de modal — rgba, não hex */
```

**A regra da temperatura:** o neutro herda a temperatura da assinatura.
Assinatura fria (azul/verde/roxo) pede cinza azulado (`#0f172a`, `#f8fafc`).
Assinatura quente (âmbar/terracota/vermelho) pede cinza quente (`#1c1917`, `#fafaf9`).
Cinza neutro puro (`#808080`) ao lado de cor quente deixa a marca com aparência suja — é o erro
número 1 de DS amador e quase ninguém sabe nomear por que "ficou estranho".

**Base nunca é preto puro nem branco puro.** `#000` cria halação com texto claro; `#fff` estoura em
tela OLED e brilho alto. Use `#030712`…`#0a0a0a` no escuro e `#fafaf9`…`#f8fafc` no claro.

### 1.3 Texto — 3 níveis, não mais

```css
--fg          /* corpo e títulos */
--fg-muted    /* parágrafos longos, descrição, legenda de card */
--fg-subtle   /* label, caption, copyright, placeholder */
```

Três níveis já dão hierarquia. Um quarto vira ilegível ou vira igual ao terceiro.

### 1.4 Bordas

```css
--border         /* padrão */
--border-muted   /* separador sutil, divisória de lista */
--border-active  /* foco, seleção, card em hover */
```

### 1.5 Estados semânticos

```css
--success / --warning / --destructive / --info
```

**Armadilha grave:** se a assinatura é verde, o sucesso **não** pode ser o mesmo verde. O usuário
perde a capacidade de distinguir "ação da marca" de "deu certo". Desloque o hue do sucesso em pelo
menos 25° ou mude a saturação drasticamente. Mesma regra pra assinatura vermelha vs. destructive,
e âmbar vs. warning.

### 1.6 Secundária e acento

Existem no token, quase nunca na tela. Servem pra gráfico com mais de uma série, ilustração, tag de
categoria. **Se a secundária aparecer no botão, você tem duas marcas brigando.**
No DS de referência, indigo e âmbar estão declarados e a interface inteira é esmeralda + neutros.

### 1.7 Alfa e overlay

```css
--primary-alpha-05  /* rgba(...,0.05) — fundo de pill */
--primary-alpha-15  /* anel de foco */
--primary-alpha-30  /* borda de hover, glow */
```

Declare como `rgba()` nomeado, não como `opacity` no elemento. `opacity` apaga o filho junto —
o texto dentro do card também desbota, e ninguém entende por quê.

### 1.8 Contraste — calcule, não estime

| Caso | Mínimo AA |
|---|---|
| Texto normal (<18.66px, peso <700) | **4.5:1** |
| Texto grande (≥24px, ou ≥18.66px bold) | **3:1** |
| Borda de componente, ícone informativo, anel de foco | **3:1** |

**A armadilha da cor pequena em fundo claro:** quase nenhuma cor de assinatura vibrante passa 4.5:1
sobre branco. Emerald `#10b981` sobre `#fff` dá ~2.5:1. A saída não é abandonar a cor — é ter um
token dedicado:

```css
--primary-on-light: #047857;  /* mesma família, 2 passos mais escuro, passa 4.5:1 */
```

Use o `-500` em botão preenchido (onde a cor é o **fundo**) e o `-on-light` em texto e link.

---

## 2. Tipografia

### 2.1 Famílias

```css
--font-display  /* opcional — só se o display for diferente do texto */
--font-sans
--font-mono
```

Toda pilha termina com fallback de sistema: `..., system-ui, -apple-system, sans-serif`.
Sem isso, a página pisca em Times New Roman enquanto a webfont carrega.

**Duas faces é o teto para 95% das marcas.** Três já exige justificativa escrita.

### 2.2 Escala — 10 degraus

```css
--fs-display-xl: 4.5rem   /* 72px — hero */
--fs-display-lg: 3.5rem   /* 56px */
--fs-display-md: 2.5rem   /* 40px — título de seção */
--fs-heading-lg: 2rem     /* 32px */
--fs-heading-md: 1.5rem   /* 24px */
--fs-heading-sm: 1.25rem  /* 20px */
--fs-body-lg:  1.125rem   /* 18px — parágrafo de destaque */
--fs-body:     1rem       /* 16px — NUNCA menos no corpo */
--fs-body-sm:  0.875rem   /* 14px */
--fs-caption:  0.75rem    /* 12px — piso absoluto */
```

Nada abaixo de 12px. 16px no corpo não é preferência, é o padrão que evita zoom no celular.

### 2.3 Tracking — o token que quase todo mundo esquece

```css
--tracking-display: -0.04em  /* ≥48px */
--tracking-heading: -0.02em  /* 24–40px */
--tracking-body:     0
--tracking-overline: 0.15em  /* UPPERCASE pequeno */
```

**A regra:** quanto maior o texto, mais negativo o tracking; quanto menor e mais caixa-alta, mais
positivo. Título grande com tracking 0 parece frouxo. Caixa-alta pequena com tracking 0 parece
amassada. Esses dois ajustes sozinhos separam "feito por designer" de "feito no automático".

### 2.4 Line-height

```css
--lh-display: 1.05
--lh-heading: 1.2
--lh-body:    1.6   /* 1.6–1.7 em texto longo */
--lh-tight:   1.3
```

### 2.5 Pesos

Declare só os que você vai carregar. Cada peso extra é peso de download.

```css
--fw-light: 300  --fw-regular: 400  --fw-medium: 500
--fw-semibold: 600  --fw-bold: 700  --fw-extrabold: 800
```

> Contraste de peso é assinatura barata e forte: o wordmark do DS de referência põe 800 ao lado de
> 200 na mesma palavra. Custa zero e é reconhecível de longe.

---

## 3. Espaço

```css
--space-1: .25rem  --space-2: .5rem   --space-3: .75rem  --space-4: 1rem
--space-6: 1.5rem  --space-8: 2rem    --space-12: 3rem   --space-16: 4rem
--space-24: 6rem   --space-32: 8rem
```

Base 4px, sempre. Espaço fora da escala (`13px`, `27px`) é o que faz uma tela parecer "quase certa"
sem ninguém saber apontar.

```css
--section-y: var(--space-24)   /* respiro entre blocos — o token mais subestimado do DS */
--container-prose: 48rem       /* 768px — texto corrido */
--container-content: 72rem     /* 1152px — grade de cards */
--container-wide: 80rem        /* 1280px — teto */
```

**Espaço é o que mais comunica preço.** Denso = ferramenta, produtivo, barato. Espaçado = premium,
calmo, caro. Isso é decisão de marca, não de layout — decida na Rodada 1 e trave no token.

---

## 4. Raio

```css
--radius-sm:   .5rem    /*  8px */
--radius-md:  .75rem    /* 12px — botão, input */
--radius-lg:    1rem    /* 16px — card */
--radius-xl: 1.25rem    /* 20px — card de destaque */
--radius-2xl: 1.5rem    /* 24px — container grande */
--radius-full: 9999px   /* pill, avatar */
```

**Armadilha:** um raio só, aplicado em tudo, achata a hierarquia (é o antipadrão do "8px em tudo").
A relação certa é proporcional: elemento maior, raio maior. Um botão de 40px com raio 24px parece um
comprimido; um card de 400px com raio 8px parece uma caixa de diálogo do Windows.

**Raio 0 é uma decisão de marca válida** (brutalista, editorial, técnica) — mas então é 0 em tudo,
declarado, e o DS diz isso por escrito. Meia dúzia de cantos retos no meio de arredondados é acidente.

---

## 5. Elevação

```css
--shadow-sm / --shadow-md / --shadow-lg / --shadow-2xl
--shadow-inset       /* declare, mesmo que só pra dizer: não usar */
--glow-primary       /* a sombra colorida da marca, se houver */
```

**A decisão de marca aqui é: sombra ou luz?**
Interface escura raramente pede drop-shadow — sombra preta sobre fundo quase preto some. O que separa
plano ali é **borda mais clara** ou **glow colorido**. O DS de referência trocou drop-shadow por
`0 0 40px rgba(16,185,129,.30)` e transformou isso numa assinatura.

Interface clara funciona com sombra — desde que seja suave, com Y maior que blur/2 e alpha baixo.
`0 20px 40px -20px rgba(0,0,0,.15)` parece profundidade. `0 4px 4px rgba(0,0,0,.5)` parece 2009.

Sombra colorida (a sombra tingida da cor do elemento) é a versão moderna:
`0 12px 24px -8px rgba(var(--primary-rgb), .35)`.

---

## 6. Motion

```css
--ease-smooth: cubic-bezier(.4, 0, .2, 1)   /* padrão de UI */
--ease-out:    cubic-bezier(0, 0, .2, 1)    /* entrada */
--ease-spring: cubic-bezier(.34, 1.56, .64, 1)  /* só se a marca for lúdica */
--dur-fast: 150ms   /* hover, foco */
--dur-base: 300ms   /* mudança de estado */
--dur-slow: 500ms   /* transição de layout */
--dur-entrance: 1000ms
```

**Motion é traço de personalidade, não enfeite.** Marca séria: entrada só, sem bounce, 150–300ms.
Marca lúdica: spring, overshoot, stagger. Escolha uma e escreva no README qual é — senão cada
componente inventa a sua.

Sempre respeite:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; }
}
```

---

## 7. Assinaturas da marca

Os 2 ou 3 detalhes reconhecíveis, **como token nomeado** — não como descrição em prosa:

```css
--gradient-number: linear-gradient(135deg, #10b981, #34d399);  /* números de prova */
--glow-primary:    0 0 40px rgba(16,185,129,.30);              /* hover de card */
/* + a regra do wordmark, escrita como classe */
```

Se a assinatura não vira token ou classe, ela não é reproduzível — é lembrança.

---

## 8. Foco, z-index, breakpoints

```css
--ring:        0 0 0 3px rgba(var(--primary-rgb), .35);
--ring-offset: 2px;

--z-dropdown: 1000;  --z-sticky: 1020;  --z-overlay: 1040;
--z-modal:    1050;  --z-toast:  1070;

--bp-sm: 640px;  --bp-md: 768px;  --bp-lg: 1024px;  --bp-xl: 1280px;
```

Foco visível não é opcional: quem navega por teclado depende dele, e `outline: none` sem substituto
é o bug de acessibilidade mais comum que existe.

---

## 9. Temas — a armadilha que invalida tudo

```css
:root { /* claro: TODOS os tokens */ }
:root[data-theme="dark"], @media (prefers-color-scheme: dark) { /* escuro: os que MUDAM */ }
```

> **A armadilha:** definir um token só dentro do bloco escuro.
> No tema claro ele fica indefinido, `var()` cai no fallback (ou em nada), e o componente renderiza
> transparente ou preto. Pior: só aparece no tema que ninguém testou.
>
> **Régua:** todo token declarado em um tema tem que existir no outro. Cheque contando as linhas dos
> dois blocos — não precisam ser iguais, mas cada nome do bloco escuro precisa existir no `:root`.

Segunda armadilha: **tema claro não é o escuro invertido.** Sombra que some no escuro precisa
aparecer no claro; borda que aparecia no escuro fica pesada no claro; a cor de assinatura que era
legível no escuro precisa do `--primary-on-light`. Desenhe os dois, não calcule um do outro.

---

## 10. Checklist final dos tokens

- [ ] Assinatura com 5 tons, e o 500 é a assinatura.
- [ ] Neutros na mesma temperatura da assinatura.
- [ ] Base não é `#000` nem `#fff`.
- [ ] 3 níveis de texto, 3 de borda, 3 de superfície.
- [ ] Sucesso ≠ assinatura (quando a assinatura é verde). Mesma checagem pra vermelho e âmbar.
- [ ] `--primary-on-light` existe e passa 4.5:1.
- [ ] Escala de tipo com 10 degraus, nada abaixo de 12px, corpo em 16px.
- [ ] Tracking negativo no display, positivo no overline.
- [ ] Espaço base 4px, com `--section-y` e larguras de container.
- [ ] Raios proporcionais, não um valor único.
- [ ] Decisão explícita: sombra ou glow.
- [ ] Motion com easing + 3 durações + `prefers-reduced-motion`.
- [ ] As assinaturas da marca viraram token ou classe.
- [ ] `--ring` existe.
- [ ] Todo token do tema escuro existe no claro.
- [ ] Nenhum hex fora do `:root`.
