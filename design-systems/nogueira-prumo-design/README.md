# Nogueira Prumo — Design System

**Posicionamento:** consultoria de estratégia e governança para empresas familiares em transição.
**Tagline:** "Parecer que sustenta decisão."
**Sede:** São Paulo · fundada em 2009
**Arquivos:** `tokens.css` (fonte de verdade) · `showcase.html` (mostruário navegável) · `SKILL.md` (instalação como skill)

---

## Quem é a marca

A Nogueira Prumo entra quando uma companhia cresceu antes de ter estrutura de decisão:
a segunda geração assumiu, a terceira chegou ao capital e ninguém escreveu quem decide o
quê. O produto da firma não é software nem processo — é **julgamento**. O cliente não
compra velocidade, compra a segurança de levar um parecer ao conselho e ele se sustentar.

Por isso o sistema visual não parece um aplicativo. Parece um **relatório caro e uma
revista de negócios**: papel branco, tinta quase preta, uma serif de alto contraste
carregando os títulos, muito espaço e um vinho que aparece pouco. Nada aqui pisca,
brilha, flutua ou pede atenção — a autoridade vem do rigor da composição.

**Para quem serve este kit:** qualquer marca que vende reputação e julgamento —
consultoria, advocacia, contabilidade, arquitetura, gestão patrimonial, boutique de M&A,
casa de análise. Se o seu cliente assina um contrato depois de ler um documento, é aqui.

**Para quem não serve:** produto de consumo, app com onboarding lúdico, marca jovem de
tecnologia, e-commerce. O sistema é frio de propósito.

---

## Paleta

O vinho é a única cor de marca. Tudo o mais é papel, fio e tinta. Regra de dosagem: **o
vinho nunca ocupa mais que ~5% da área visível da tela**.

### Vinho — assinatura

| Papel | Hex | Onde usar |
|---|---|---|
| `--vinho-100` | `#F4EAEC` | Fundo de badge de marca, marca-texto, linha destacada |
| `--vinho-300` | `#D7B3BB` | Fio tinto, sublinha de link em repouso |
| `--vinho-500` | `#8C3549` | Aplicação da marca sobre fundo escuro (o 700 some no preto) |
| `--vinho-700` | `#6B2436` | **Assinatura.** Fio-prumo, marcador de seção, botão de ação única, foco |
| `--vinho-900` | `#431722` | Estado pressionado, texto sobre fundo lavado |

### Papel e fio

| Papel | Hex | Onde usar |
|---|---|---|
| `--papel` | `#FFFFFF` | Fundo da página e do card. O padrão |
| `--superficie` | `#FAF9F8` | Seção alternada, linha de tabela em hover |
| `--elevado` | `#F2F0EE` | Campo desabilitado, bloco de código, amostra neutra |
| `--tinta-fundo` | `#17120F` | Rodapé, capa de parecer, aplicação invertida da marca |
| `--fio` | `#E5E1DE` | Divisória padrão de 1px entre itens de uma mesma lista |
| `--fio-forte` | `#C9C3BF` | Borda de campo e de botão de contorno |

### Tinta (texto)

| Papel | Hex | Onde usar |
|---|---|---|
| `--texto` | `#17120F` | Títulos e corpo · contraste 18,3:1 no branco |
| `--texto-medio` | `#4A4340` | Texto de apoio, célula de tabela, legenda longa · 9,7:1 |
| `--texto-fraco` | `#7A716C` | Rótulo, crédito, placeholder · 4,8:1 (só a partir de 13px) |
| `--texto-invertido` | `#FAF9F8` | Sobre `--tinta-fundo` |

### Semânticas

| Papel | Hex | Onde usar |
|---|---|---|
| `--sucesso` | `#1F5D45` | Favorável, aprovado, concluído (par lavado `#E8F0EC`) |
| `--atencao` | `#8A6116` | Ressalva, pendente, prazo curto (par lavado `#F6F0E4`) |
| `--erro` | `#A32323` | Impedimento, dado inválido, bloqueio (par lavado `#F7E9E9`) |

**Vinho é marca; vermelho é estado.** Nunca deixe um alerta de erro dividir espaço com um
botão vinho: troque o botão para tinta.

---

## Tipografia

Duas famílias, e a tensão entre elas é o sistema inteiro. Ambas as pilhas são **nativas** —
nenhum `@import`, nenhuma fonte remota, nada quebra offline.

| Papel | Pilha | Regra |
|---|---|---|
| Títulos (didone) | `Didot → Bodoni 72 → Bodoni MT → Iowan Old Style → Palatino → Georgia` | Alto contraste. É a personalidade da página |
| Corpo (grotesca) | `Helvetica Neue → system-ui → Segoe UI → Roboto → Arial` | Neutra e discreta. Existe pra não ser notada |

### Regras duras

1. **A serif nunca desce abaixo de 19px.** O filete fino some e o texto vira mancha. Abaixo
   disso é sempre sans.
2. **A serif nunca vira interface.** Rótulo, botão, badge, cabeçalho de tabela, campo de
   formulário: tudo sans. Serif só em título, citação e número de destaque.
3. **Medida de leitura travada em 65 caracteres** (`--medida`). Coluna de apoio em 46ch.
   Linha mais longa que isso é erro, não escolha.
4. **Entrelinha generosa:** 1,65 no corpo, 1,12 nos títulos. O ar entre as linhas é metade
   da sensação de "documento caro".
5. **Rótulos em versalete:** 11px, caixa-alta, tracking 0,18em, peso 600, sempre em sans.
   É o único momento de caixa-alta do sistema.
6. **Nada de itálico decorativo.** O itálico da serif marca ênfase real (uma palavra na
   manchete, um termo estrangeiro) e a citação.
7. **Números sempre tabulares** (`font-variant-numeric: tabular-nums`), alinhados à direita
   em tabela. Um número de destaque ganha a serif e um único fio vinho embaixo.

### Escala

| Token | px | Uso |
|---|---|---|
| `--ts-display` | 68 | Capa, manchete de abertura |
| `--ts-1` | 48 | Título de página |
| `--ts-2` | 34 | Título de seção |
| `--ts-3` | 24 | Título de bloco, pull-quote |
| `--ts-4` | 19 | Menor tamanho permitido para a serif |
| `--ts-lead` | 20 | Linha de abertura (sans) |
| `--ts-corpo` | 17 | Corpo padrão |
| `--ts-peq` | 15 | Apoio, tabela densa |
| `--ts-legenda` | 13 | Legenda, nota de rodapé |
| `--ts-micro` | 11 | Versalete, rótulo |

---

## Composição

- **Fio de 1px é a estrutura.** Antes de criar uma caixa, uma sombra ou um fundo colorido
  pra separar dois conteúdos, tente um fio ou mais espaço. Quase sempre resolve.
- **Grade de duas colunas:** rótulo fixo à esquerda (190px, versalete + uma frase),
  conteúdo à direita. É o layout de nota lateral de relatório — e é o que dá o ar editorial
  sem imitar jornal.
- **Alinhamento à esquerda em tudo**, inclusive títulos. Números à direita. Nada
  centralizado, nada justificado.
- **Respiro entre seções: 96px** (`--e-16`). Entre blocos internos: 48px.
- **Cantos:** 0 é o padrão; 1px em campo; 2px é o máximo do sistema (botão, card, badge).
- **Elevação:** nível 0 em tudo que é estático. Sombra só no que realmente flutua —
  toast, menu, diálogo.
- **Sem ícones decorativos, sem ilustração, sem emoji.** O sistema não tem essa camada. O
  único desenho da marca é o símbolo do prumo.

### A assinatura visual: o fio-prumo

Um fio vertical de 1px em vinho com um losango de 5px no pé. Ele é o eixo do wordmark
(entre "Nogueira" e "PRUMO"), o marcador de abertura de documento e o símbolo/favicon. É o
elemento pelo qual a marca é reconhecida — use-o **uma vez por bloco**, nunca repetido em
série.

---

## Componentes e estados

### Botões — a hierarquia

| Variante | Quando | Repouso → Hover → Ativo |
|---|---|---|
| `.np-btn--tinta` | Ação principal do bloco | `#17120F` → `#2F2724` → `#000000` |
| `.np-btn--vinho` | **A única** ação de conversão da tela | `#6B2436` → `#431722` → `#35111B` |
| `.np-btn--contorno` | Ação secundária | fio forte → fundo `--superficie` + borda tinta |
| `.np-btn--texto` | Ação terciária, inline | sublinha `--vinho-300` → `--vinho-700` |

- **Dois botões vinho na mesma tela = erro.** Se aparecerem dois, um vira tinta.
- **Foco:** anel quadrado de 2px vinho com 2px de folga branca (`--anel-foco`). Nunca
  remova o foco sem colocar outro no lugar — metade dos clientes desta marca navega por
  teclado em documento longo.
- **Desabilitado:** fundo `--elevado`, texto `--texto-fraco`, `cursor: not-allowed`. O
  botão de texto desabilitado não vira caixa: só apaga.
- Botão não tem sombra, não levanta, não muda de tamanho. Só de cor.

### Card

Branco sobre branco, definido só pelo fio de 1px. No hover, um fio vinho de 2px cresce da
esquerda para a direita no topo (`transform: scaleX`) — é o único movimento do componente.
`.np-card--fixo` deixa esse fio permanente para marcar o card em destaque de uma lista.
**Nunca mais de um card fixo por lista.**

### Campo de formulário

Borda `--fio-forte`, raio 1px. No foco: borda vira tinta e uma **sublinha vinho de 2px**
aparece por dentro (`inset box-shadow`). Erro: borda `--erro` + mensagem em `--erro` abaixo,
sempre explicando o que fazer ("faltam dígitos verificadores"), nunca só "campo inválido".
Rótulo em versalete acima; texto de ajuda em 13px abaixo.

### Badge

Retângulo de 2px, versalete de 11px, borda de 1px. Cinco variantes: neutro, marca (vinho
lavado), sucesso, atenção, erro. Badge não é botão — nunca é clicável.

### Citação

Serif, no máximo duas linhas, fio vinho vertical à esquerda, atribuição em versalete. É a
voz de um sócio assumindo uma posição — se o parágrafo ao lado já disse aquilo, corte a
citação.

### Tabela

Sem borda externa e sem zebra colorida. Régua de tinta sob o cabeçalho, fio claro entre
linhas, hover em `--superficie`. Números à direita, tabulares. Cabeçalho em versalete.

---

## VOZ

A marca escreve como quem já leu o contrato inteiro. Frases curtas, verbo forte, nenhuma
promessa que não caiba num parecer. O texto respeita a inteligência de quem lê e não
tenta agradar.

### Falar / não falar

| Falar | Não falar |
|---|---|
| "Parecer" | "Insight" |
| "Critério" | "Fórmula", "receita" |
| "Ressalva" | "Pontos de melhoria" |
| "A firma" | "A gente", "o time" |
| "Não recomendamos" | "Talvez não seja o ideal" |

### Regras de escrita

- **Pessoa:** primeira do plural, sóbria — "trabalhamos", "não recomendamos", "a firma
  entende". Nunca "eu"; nunca "a gente". O cliente é tratado por **você**, sem intimidade
  forçada.
- **Frase:** curta e declarativa. Uma ideia por frase. Ponto final sempre, inclusive em
  título de seção quando ele é uma afirmação ("Herança não é plano.").
- **Travessão (—)** para encaixar a ressalva no meio da frase. É a pontuação da casa.
  Nunca hífen duplo, nunca reticências.
- **Números por extenso até dez**, algarismo daí em diante. Valores sempre com a unidade
  ("R$ 4,2 bi", "12 semanas"). Todo número relevante vem com base declarada em legenda.
- **Caixa-alta só em versalete** de rótulo. Nunca uma frase inteira em maiúsculas.
- **Nunca aparece:** emoji, exclamação, superlativo ("melhor", "líder", "referência"),
  jargão de startup ("disruptivo", "unlock", "game changer"), urgência artificial ("última
  chance"), pergunta retórica em manchete, promessa de resultado garantido.
- **CTA** é um verbo direto, sem arroba de vendas: "Solicitar proposta", "Agendar
  conversa", "Baixar parecer". Sem seta, sem "clique aqui", sem "vamos lá".

### Em um parágrafo

Escreva como se o texto fosse anexado à ata. Se uma frase não sobreviveria à leitura em
voz alta na reunião de conselho, ela não entra.

---

## Acessibilidade

- Contraste verificado: `--texto` 18,3:1 · `--texto-medio` 9,7:1 · `--texto-fraco` 4,8:1
  (só a partir de 13px) · `--vinho-700` 10,5:1 · branco sobre `--vinho-700` 10,5:1.
- Foco visível obrigatório em todo elemento interativo (`--anel-foco`).
- `prefers-reduced-motion` desliga todas as transições — já está em `tokens.css`.
- Nunca use só cor para comunicar estado: badge sempre traz a palavra ("Com ressalva"),
  campo em erro sempre traz a mensagem.

---

## Como usar

```html
<link rel="stylesheet" href="tokens.css">
<body class="np-base">
  <h1 class="np-t1">Sucessão em empresa familiar</h1>
  <p class="np-corpo">…</p>
  <button class="np-btn np-btn--tinta">Solicitar proposta</button>
</body>
```

Em React/Tailwind, mapeie as variáveis no `theme` e mantenha os nomes (`vinho-700`,
`texto-medio`, `fio`) — o vocabulário faz parte do sistema. Abra `showcase.html` no
navegador para ver tudo aplicado e clique nas amostras para copiar os hex.
