# Kiln — Design System

**Produto:** plano de controle para pipelines de dados e APIs internas.
**Arquétipo:** produto técnico · dev tool · infraestrutura.
**Uma frase:** a interface não tenta impressionar, tenta informar.

---

## Quem é o Kiln e para quem serve

Kiln é um produto de infraestrutura: ingestão de eventos, execução agendada, alerta e auditoria numa
superfície só. Quem abre o Kiln às 06:03 da manhã não quer uma experiência — quer saber se a carga da
madrugada rodou, quantas linhas foram descartadas e qual passo travou.

O público é técnico e o produto respeita isso. Não existe onboarding com ilustração, não existe copy
que celebra o clique, não existe animação para "dar vida" a um número. O que existe é densidade: mais
linhas por tela, rótulos curtos, números alinhados e uma cor quente marcando o único lugar onde a
pessoa precisa agir.

**Este DS serve bem para:** painel de observabilidade, dashboard de API, plataforma de automação,
console interno, ferramenta de dados, admin de infraestrutura, CLI com interface web.
**Serve mal para:** e-commerce, produto de consumo, landing page de captação, app de bem-estar.
Se o objetivo é encantar, este não é o sistema.

### A ideia central: contraste de temperatura

Tudo no Kiln é aço azulado frio, e uma única cor é quente. O âmbar de forja só funciona porque nada
em volta dele é quente — é a mesma lógica de um LED aceso dentro de um rack. Se você adicionar um
segundo tom quente ao sistema, a assinatura morre. O nome do produto vem daí: um forno de queima é um
instrumento calibrado, cheio de calor por dentro e frio por fora, e alguém está sempre olhando o
mostrador.

---

## Arquivos

| Arquivo | O que é |
|---|---|
| `tokens.css` | Fonte de verdade. Variáveis CSS + classes utilitárias com prefixo `.kl-`. É o único arquivo que você precisa levar para o projeto. |
| `showcase.html` | Página autocontida com marca, paleta clicável, escala de tipo, componentes em todos os estados, raios, elevação e regras de uso. Abra no navegador; não tem dependência nenhuma. |
| `README.md` | Este manual: contexto, paleta, tipografia, componentes, estados e voz. |
| `SKILL.md` | Frontmatter para instalar a pasta como skill do Claude Code. |

**Instalação:** copie `tokens.css` para o projeto, dê `<link rel="stylesheet" href="tokens.css">` e
coloque `class="kl"` no `<body>`. Não precisa de build, de PostCSS nem de fonte remota.

---

## Paleta

### Assinatura — âmbar de forja

Cinco passos de uma cor só. Ela marca **ação e foco**, nunca estado.

| Token | Hex | Contraste sobre a base | Onde usar |
|---|---|---|---|
| `--kl-ember-100` | `#FFE2BE` | 15,5:1 | Texto sobre preenchimento âmbar escuro (estado pressed do botão primário). |
| `--kl-ember-300` | `#FFB25C` | 10,8:1 | Texto e ícone de acento sobre fundo escuro. É o âmbar que você usa quando o âmbar precisa ser lido. |
| `--kl-ember-500` | `#F08519` | 7,4:1 | **A assinatura.** Preenchimento do botão primário, anel de foco, cursor do wordmark, barra de meter, marcador de item ativo. |
| `--kl-ember-700` | `#A85310` | 3,6:1 | Borda do botão primário e estado pressed. **Nunca em texto** — não passa AA. |
| `--kl-ember-900` | `#3A2008` | — | Fundo tingido de chip e faixa de destaque. |

Alfas derivadas: `--kl-ember-a08` (hover de linha, fundo de chip), `--kl-ember-a16` (borda de chip),
`--kl-ember-a55` (anel de foco).

**Orçamento de âmbar:** no máximo dois elementos âmbar por tela cheia. Se aparecer um terceiro,
o problema é de hierarquia, não de cor.

### Neutros — aço frio

Cinco superfícies e três hairlines. A hierarquia é feita por valor de fundo + 1px de borda.

| Token | Hex | Onde usar |
|---|---|---|
| `--kl-sunken` | `#070910` | Poço: bloco de código, saída de terminal, input, rodapé de card. |
| `--kl-base` | `#0B0E14` | Página. |
| `--kl-surface` | `#11151D` | Card, painel, cabeçalho de tabela. |
| `--kl-raised` | `#171D27` | Botão secundário, linha em hover, aba ativa. |
| `--kl-overlay` | `#1D2531` | Popover, menu, toast. É o único plano que carrega sombra. |
| `--kl-line-soft` | `#171E29` | Divisória entre linhas de tabela. |
| `--kl-line` | `#212A38` | Borda padrão de card, input e botão. |
| `--kl-line-loud` | `#334053` | Borda em hover e destaque que não é âmbar. |

### Texto — três níveis, e só três

| Token | Hex | Contraste | Onde usar |
|---|---|---|---|
| `--kl-text` | `#E7EBF3` | 16,2:1 | O dado: valor, título, conteúdo da célula. |
| `--kl-text-2` | `#9BA6BA` | 7,9:1 | A explicação: parágrafo, descrição, texto de ajuda. |
| `--kl-text-3` | `#828DA0` | 5,8:1 | O rótulo: label mono, metadado, unidade, timestamp. |
| `--kl-text-on-ember` | `#1A1206` | 7,1:1 sobre âmbar | Texto sobre preenchimento âmbar. |

Um quarto nível de texto é sinal de que a tela tem informação demais. Corte conteúdo, não contraste.

### Semânticas — estado do sistema

| Token | Hex | Contraste | Significa |
|---|---|---|---|
| `--kl-ok` | `#46B67F` | 7,6:1 | Operacional, 2xx, deploy concluído. |
| `--kl-warn` | `#E0B341` | 9,8:1 | Degradado, perto do limite, retry em curso. |
| `--kl-err` | `#E8564E` | 5,4:1 | Caído, 5xx, job falhou, validação inválida. |
| `--kl-info` | `#5B8DEF` | 6,0:1 | Informativo, em fila, nota do sistema. |

Cada uma tem um fundo tingido a 12% (`--kl-ok-bg` e companhia) para badge e faixa.

**O risco conhecido deste sistema:** `--kl-warn` (amarelo) e `--kl-ember-500` (laranja) são vizinhos de
temperatura. Eles não se confundem porque **âmbar nunca aparece como estado e amarelo nunca aparece como
ação** — e porque estado sempre vem acompanhado de palavra. Se você quebrar uma dessas duas regras, o
sistema fica ambíguo na hora. Não há terceira proteção.

**Cor nunca carrega significado sozinha.** Todo estado aparece como quadrado de 6px + palavra. O painel
tem que continuar legível impresso em preto e branco e para quem não distingue vermelho de verde.

---

## Tipografia

Duas faces, papéis que não se misturam, zero webfont. As duas stacks são nativas do sistema
operacional: a página abre sem rede, sem FOUT e sem requisição de terceiro.

```css
--kl-font-mono: ui-monospace, "SF Mono", SFMono-Regular, Menlo, Consolas,
                "Liberation Mono", "DejaVu Sans Mono", monospace;
--kl-font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI Variable Text",
                "Segoe UI", Roboto, "Helvetica Neue", "Noto Sans", Arial, sans-serif;
```

### A regra que decide tudo

> **Se o conteúdo é um dado, ele é mono. Se é uma frase que a pessoa lê em sequência, é sans.**

**Mono (estrutural):** rótulo, número, unidade, metadado, ID, hash, timestamp, caminho de rota,
método HTTP, cabeçalho de tabela, célula de tabela, badge, botão, item de navegação, wordmark.

**Sans (leitura):** parágrafo, descrição de card, texto de ajuda, estado vazio, mensagem longa,
documentação.

Número em sans é bug de implementação. Não existe exceção — nem em KPI grande, nem em gráfico.

### Escala

| Token | px | Uso |
|---|---|---|
| `--kl-fs-3xl` | 44 | Display. Só na abertura de página de marketing interno. |
| `--kl-fs-2xl` | 34 | Título de página, KPI grande. |
| `--kl-fs-xl` | 26 | Título de seção. |
| `--kl-fs-lg` | 20 | Título de card. |
| `--kl-fs-md` | 16 | Texto corrido em sans. **Único tamanho de leitura.** |
| `--kl-fs-base` | 14 | Corpo denso, item de lista. |
| `--kl-fs-sm` | 13 | **Padrão da UI**: botão, input, tabela larga, navegação. |
| `--kl-fs-mini` | 12 | Célula de tabela, metadado, badge. |
| `--kl-fs-micro` | 11 | Label mono maiúsculo, unidade, legenda de eixo. |

A UI opera em 13px, não em 16px. Isso é deliberado: densidade é posicionamento.

### Regras de composição

- **Label mono é sempre maiúsculo com `letter-spacing: 0.08em`.** Sem esse tracking, maiúscula em mono
  vira um bloco ilegível. O tracking não é estilo, é legibilidade.
- **Todo número usa `font-variant-numeric: tabular-nums`.** Coluna de número é uma régua vertical:
  se os dígitos não alinham, a leitura por varredura morre. Use a classe `.kl-num`.
- **Número em tabela alinha à direita.** Texto alinha à esquerda. Não existe centralização em tabela.
- **Unidade vem separada por espaço e em texto terciário**, com metade do tamanho do número:
  `96 ms`, `48,2 M`, `0,31 %`. Use `.kl-num__unit`.
- **Pesos:** 400 / 500 / 600 / 700. Nada de 200 ou 800 — a face mono do sistema não tem esses cortes
  e falsear peso quebra a métrica do monoespaçado.
- **Títulos usam tracking `-0.015em`.** Discreto. Este sistema não é de manchete.
- **Ligaduras desligadas** (`font-variant-ligatures: none`). `=>` tem que aparecer como `=>`.
- **Números em pt-BR:** vírgula decimal, ponto de milhar. `1.902 ms`, `11,60%`, `48,2 M`.

---

## Espaço, raio, elevação e movimento

**Espaço** — base 4 com meio-passo em 2 e 6, de `--kl-s-1` (2px) a `--kl-s-11` (64px).
Gutter de página: 24px. Padding de card: 24px. Altura de controle: 32px (`--kl-ctrl`).
A régua é mais curta que o padrão de mercado de propósito.

**Raio** — máximo 6px, em qualquer elemento.
`--kl-r-0` (0) faixa e tabela colada · `--kl-r-1` (2px) quadrado de status e tag ·
`--kl-r-2` (4px) **padrão**: botão, input, badge, chip · `--kl-r-3` (6px) card, painel, popover.
**Não existe raio total.** Badge é retângulo, indicador é quadrado, avatar é quadrado de 4px.

**Elevação** — três níveis, e os dois primeiros são a regra.
`--kl-e-0` sem sombra (card, painel) · `--kl-e-1` 1px de apoio (botão, input) ·
`--kl-e-2` camada que flutua de verdade (popover, menu, toast).
**Sombra colorida é proibida em todos os níveis.** O que separa um plano do outro é 1px de borda e um
degrau de fundo: `#070910 → #0B0E14 → #11151D → #171D27 → #1D2531`.

**Movimento** — 90ms para cor, 140ms para estado de controle, 220ms para camada que aparece.
Easing `cubic-bezier(0.2, 0, 0, 1)`. Sem bounce, sem elástico, sem entrada animada em conteúdo de dado.
Um número que entra deslizando faz a pessoa duvidar do número. `prefers-reduced-motion` está tratado
dentro do `tokens.css` — não desative.

---

## Componentes e estados

| Componente | Classe | Quando usar |
|---|---|---|
| Botão | `.kl-btn` + `--primary` / `--ghost` / `--danger`, `--sm` / `--lg` | Ação. Primário é preenchimento âmbar; **um por vista**. |
| Card | `.kl-card` + `__head` / `__body` / `__foot` | Agrupar. `--link` só quando o card inteiro navega. |
| Campo | `.kl-field`, `.kl-input`, `.kl-select`, `.kl-textarea`, `.kl-input-group` | Entrada. Input usa fundo `sunken` — mais fundo que o card, porque recebe. |
| Badge | `.kl-badge` + `--ok` / `--warn` / `--err` / `--info` / `--ember` | Classificar. 20px de altura para caber na linha da tabela. |
| Status | `.kl-status` + `.kl-dot` | Estado. Quadrado de 6px + palavra, sempre juntos. |
| Tabela | `.kl-table` dentro de `.kl-table-wrap` | Dado tabular. O scroll horizontal pertence à tabela, nunca ao body. |
| Chave-valor | `.kl-kv` | Metadado de recurso: id, timestamps, destino. |
| Meter | `.kl-meter` | Proporção: cota, progresso de job. 4px de altura. |
| Navegação | `.kl-nav` + `.kl-nav__item[aria-current="page"]` | Item ativo = fundo `raised` + quadrado âmbar. Sem preenchimento âmbar. |
| Toast | `.kl-toast[data-open]` | Confirmação curta. Único componente que usa `--kl-e-2` + `data-attribute`. |
| Régua de seção | `.kl-rule` | Abrir bloco: label mono + hairline atravessando a largura. |
| Código | `.kl-code` (inline), `.kl-pre` (bloco), `.kl-kbd` (tecla) | Comando, payload, saída de terminal. |

### Regras de estado

- **Foco é sagrado.** Todo controle tem `:focus-visible` com `--kl-ring` (anel âmbar de 3px com 1px de
  respiro). Se você remover `outline`, devolva o anel na mesma linha de código.
- **Hover só existe onde há destino.** Card estático não reage. Reagir sem levar a lugar nenhum é ruído.
- **Hover muda fundo e borda, nunca tamanho.** Nada de `transform: scale`. O único deslocamento
  permitido é `translateY(1px)` no `:active` de botão — o feedback de "afundou".
- **Desabilitado é `opacity: 0.42` + `cursor: not-allowed`.** Não invente uma cor de desabilitado.
- **Carregando é `opacity: 0.72` e o rótulo permanece.** O sistema não esconde o que está fazendo, e
  trocar a cor do texto aqui quebraria o contraste do botão primário.
- **Erro de campo mostra o valor observado.** "Token com 11 caracteres; o formato exige 40", nunca
  "Token inválido". O erro fica em mono, 11px, com o quadrado vermelho antes.
- **Linha selecionada em tabela** usa `--kl-ember-a08` de fundo. Sem borda, sem check colorido.

---

## A marca

**Wordmark:** `kiln` em caixa baixa, na face mono, peso 700, com um **cursor de bloco âmbar** colado à
direita. O cursor é a marca — é a única forma âmbar autorizada a aparecer sozinha, sem rótulo.

**Aplicações:** sobre a base, sobre superfície, invertido sobre âmbar (o cursor vira quase-preto),
ícone de app em três tamanhos (24 / 32 / 44), lockup horizontal com barra de 1px separando marca e
descritor, lockup empilhado para o seletor de organização.

**A piscada** (`.kl-wordmark--blink`) só no cabeçalho do produto. Em documento, apresentação, favicon
ou qualquer lugar impresso, o cursor fica parado.

**Nunca:** wordmark em sans · em caixa alta · com contorno · com sombra · em outra cor que não
`--kl-text` ou `--kl-text-on-ember` · com o cursor destacado do texto · dentro de forma redonda.

**Assinaturas visuais que tornam o Kiln reconhecível:**
1. O cursor de bloco âmbar.
2. Label mono maiúsculo seguido de hairline atravessando a largura (`.kl-rule`).
3. Quadrado de 6px como indicador de estado — nunca círculo.
4. Colunas de número tabular alinhadas à direita.
5. Elevação desenhada com 1px de borda, sem nenhuma sombra difusa.

---

## VOZ

O Kiln escreve como um colega sênior escrevendo no canal de incidente: direto, específico, sem drama.
A meta é que a pessoa leia a frase uma vez e saiba o que fazer.

### Falar / não falar

| Falar | Não falar |
|---|---|
| "3 execuções falharam às 14:02" | "Ops! Algo deu errado" |
| "Token com 11 caracteres; o formato exige 40" | "Token inválido" |
| "p95 de 96 ms nas últimas 24 h" | "Performance excelente" |
| "Nenhuma execução ainda — a primeira roda às 06:00" | "Nada por aqui ainda" |
| "Apagar pipeline — não tem volta" | "Tem certeza? Essa ação é irreversível!" |

O padrão das cinco linhas é o mesmo: **fato observado, com número e horário, em vez de adjetivo ou
emoção**. Quando o Kiln não sabe, ele diz o que sabe ("último heartbeat há 4 min"), não pede desculpa.

### Regras de escrita

- **Pessoa.** O produto nunca diz "eu" nem "nós". Ação é imperativo curto (`reexecutar`, `exportar csv`,
  `pausar`). Estado é impessoal (`concluída em 4,2 s`). "Você" só aparece quando a frase precisa
  atribuir responsabilidade: "reexecutar produz o mesmo erro, se o erro estiver no seu código".
- **Rótulo de UI é caixa baixa e sem ponto final** — `nova pipeline`, `ver logs`. Label de seção é
  maiúsculo com tracking. Prosa é sentence case e termina com ponto.
- **Título em português não usa Title Case.** É "Latência por rota", não "Latência Por Rota".
- **Sem ponto de exclamação. Em lugar nenhum.** Nem em sucesso, nem em erro, nem em toast.
- **Erro tem três partes:** o que aconteceu, o valor observado, o que fazer. Nessa ordem.
- **Estado vazio explica a causa e o próximo evento**, nunca só a ausência.
- **Número sempre com unidade e formato pt-BR:** `1.902 ms`, `12.480 req/min`, `0,31%`, `48,2 M`.
  Percentual com uma casa decimal quando abaixo de 10.
- **Horário absoluto quando o momento importa** (`14:02`), relativo quando a recência importa
  (`há 12 s`). Nunca os dois na mesma frase.
- **Termos técnicos ficam em inglês** quando é assim que a pessoa vai buscar no Google: `retry`,
  `payload`, `webhook`, `schema`, `deploy`, `p95`. Não traduza para parecer mais acessível.
- **Travessão (—) para atar cláusulas**, `·` para separar metadados numa linha. Nunca `>` nem `>>`.

### O que nunca aparece

Emoji · ponto de exclamação · "Ops" · "simplesmente", "apenas", "é só" · "incrível", "poderoso",
"revolucionário", "mágico" · "clique aqui" · "vamos estar verificando" · Title Case em português ·
adjetivo no lugar de número · pedido de desculpa da máquina.

---

## Checklist antes de dar merge

- [ ] Todo número está em mono e tabular?
- [ ] Existe no máximo um preenchimento âmbar na tela?
- [ ] Todo estado colorido tem uma palavra ao lado?
- [ ] Todo controle interativo mostra o anel de foco no `Tab`?
- [ ] Algum canto passou de 6px? Alguma forma virou pílula?
- [ ] Alguma sombra ficou colorida ou maior que `--kl-e-2`?
- [ ] A tabela rola dentro do próprio contêiner, sem empurrar o `body`?
- [ ] Algum texto usa cor fora dos três níveis?
- [ ] As mensagens de erro mostram o valor observado?
- [ ] Sobrou algum ponto de exclamação?
