---
name: prompt-ctc
description: "Transforma uma ideia solta ('quero um negócio pra organizar meus clientes', 'quero uma landing page', 'queria automatizar isso aqui') em um prompt de entrega completo pelo método CTC — Contexto, Tarefa e Critério de aceite. Começa com uma rodada de descoberta pra identificar se é uma peça única, um sistema, uma automação ou um ambiente, e que integrações estão envolvidas. Quando é sistema, gera também um PRD versionado dentro do projeto (docs/PRD.md), que serve pra conferir os critérios de aceite depois de pronto e pra evoluir junto com o projeto. Use quando o usuário disser /prompt-ctc, pedir ajuda pra 'montar um prompt', 'estruturar meu pedido', 'escrever um PRD', ou quando descrever de forma vaga algo que quer construir. Dentro de um projeto no Claude Code, pergunta na primeira invocação da sessão se deve executar o CTC ali mesmo ou só gerar o prompt, e sempre explica o que gerou."
---

# /prompt-ctc — de ideia solta a prompt (e a PRD, quando o caso pede)

Você **não começa construindo o produto**. Primeiro você constrói o **prompt** que constrói o produto —
e, quando for um sistema, a **documentação viva** que sustenta ele ao longo do tempo.
Depois, ou entrega esse prompt, ou executa ele você mesmo: quem decide é a pessoa, uma vez por
sessão (veja **Modo de saída**).

## O método, em uma linha

| Camada | Pergunta que responde | O que dá errado sem ela |
|---|---|---|
| **Contexto** | Onde eu estou pisando? | A IA inventa o cenário: troca a stack, reescreve o que já funcionava. |
| **Tarefa** | O que exatamente é pra fazer? | Escopo explode, vem "melhoria" que ninguém pediu. |
| **Critério** | Como eu sei que acabou e ficou bom? | Volta "pronto!" e você vira o QA. |

---

## MODO DE SAÍDA — executar ou só gerar (pergunte uma vez por sessão)

O CTC serve pra duas coisas diferentes, e quem invocou a skill precisa saber qual vai receber:

- **Roteiro pra executar:** as decisões, os fatos e os critérios que você mesmo usa pra construir e conferir, ali no projeto.
- **Prompt pra levar:** um bloco pronto pra colar numa sessão nova, em outra ferramenta, ou mandar pra alguém.

**Quando perguntar.** Só quando você está no Claude Code (ou em outro agente com acesso a arquivos e
terminal) trabalhando num projeto: existe diretório de trabalho com código, ou a conversa já vinha
mexendo nele. Fora disso (chat sem acesso a arquivos), o modo é **só gerar** e não se pergunta nada,
porque não há onde executar.

**Na primeira invocação da sessão**, pergunte junto com a primeira rodada. Conta como uma das 4 perguntas:

> **Quando o CTC ficar pronto, o que eu faço com ele?**
> - **Executar aqui (Recomendado)** — eu uso o CTC como roteiro, implemento neste projeto e confiro cada critério antes de dizer que acabou. Você não precisa colar nada.
> - **Só gerar o prompt** — eu entrego o bloco pronto pra você guardar, colar em outra sessão ou mandar pra alguém. Não implemento nada.
>
> Se você não disser, eu executo aqui.

**Nas invocações seguintes, não pergunte de novo.** Antes de perguntar, procure nesta conversa
(inclusive no resumo, se ela foi compactada) a resposta dada antes. Achou: use o mesmo modo. Não
achou, ou ficou em dúvida: pergunte. Também não pergunte quando a pessoa já disse na própria
invocação ("monta e roda", "só quero o prompt"). E troque de modo sempre que ela pedir ("agora só
gera", "pode executar").

| | Executar aqui | Só gerar |
|---|---|---|
| **Rodadas** | As mesmas. O que o projeto já responde vira fato, não pergunta. | As mesmas. |
| **Entrega do CTC** | Explica em 2 linhas o que gerou e mostra o CTC como plano. Começa a implementar em seguida, sem perguntar "rodo agora?". | Explica em 2 a 3 linhas o que gerou e pra que serve, e entrega o bloco pronto pra colar. |
| **Final** | Relatório critério por critério: passou, ou falhou com a evidência. Critério que falhou vira trabalho, não ressalva. | Oferece: salvar em arquivo · ajustar · executar aqui, se mudar de ideia. |
| **Rota B** | Escreve `docs/PRD.md` e executa a fase 1. | Escreve `docs/PRD.md` e entrega o prompt da fase 1. |

**A explicação do que gerou vale nos dois modos.** Sem ela, a pessoa recebe um bloco de texto e não
sabe se é pra colar, guardar ou esperar. Diga o que o CTC guarda (as decisões que ela tomou nas
rodadas, os fatos, com fonte quando houver, e como conferir que ficou pronto) e o que acontece com
ele agora.

---

## Regras de condução (leia antes de perguntar qualquer coisa)

1. **A ordem é: Descoberta → Contexto → Tarefa → Critério.** Nunca pule pro código no meio.
2. **Máximo 4 perguntas por rodada.** Questionário de 20 itens faz a pessoa desistir. Pergunte o que muda o resultado; o resto você assume.
3. **Use `AskUserQuestion`** com opções prontas sempre que possível — escolher é mais fácil que redigir. Sem ela, faça perguntas numeradas em texto.
4. **Toda pergunta vem com um default explícito**: *"Se você não souber, eu assumo X."* A pessoa pode responder "sei lá" e o fluxo continua.
5. **Nunca pergunte o que dá pra descobrir sozinho.** Se existe pasta, repositório ou arquivo, leia antes e traga como fato ("vi que seu projeto usa Next.js — confirma?").
6. **Se disserem "vai logo" / "faz você mesmo"**, pare de perguntar: preencha com defaults, marque cada suposição com `[SUPOSIÇÃO]` e entregue. No modo **executar aqui**, entregar é implementar.
7. **Nunca devolva a pergunta que a pessoa não sabe responder.** Se ela não sabe o que quer, não pergunte "o que você quer?" de novo — ofereça duas ou três hipóteses concretas e deixe ela apontar. Reconhecer é sempre mais fácil que lembrar.

---

## RODADA 0 — DESCOBERTA (quando a pessoa só tem uma ideia na cabeça)

Comece **sempre** por aqui, mesmo que o pedido pareça claro. É o que separa uma landing page
de um sistema disfarçado de landing page.

> Não pergunte a solução. Pergunte a **situação**. Quem não sabe o que quer construir sabe muito bem
> o que dói.

**As 4 perguntas de descoberta:**

1. **Me conta o que acontece hoje que te incomoda** — como é feito agora, na mão ou em outro lugar?
   *(se a pessoa travar: "me descreve a última vez que isso deu trabalho")*
2. **Quem mais mexe nisso além de você?** → `só eu` · `minha equipe` · `meus clientes` · `qualquer pessoa da internet`
3. **Isso precisa guardar informação pra consultar depois?** → `sim, e cresce todo dia` · `sim, mas é pouco` · `não, é só mostrar/fazer na hora`
4. **Precisa conversar com alguma ferramenta que você já usa?** → `WhatsApp` · `planilha/Sheets` · `pagamento` · `e-mail` · `CRM/agenda` · `nenhuma` *(múltipla escolha)*

**Devolva a leitura antes de seguir.** Uma frase, para a pessoa confirmar ou corrigir:

> Então, deixa eu ver se entendi: você quer **[coisa]** pra **[quem]**, que guarda **[o quê]** e fala com **[ferramenta]**.
> Isso é **[tipo]**. É isso mesmo?

### Classificação — o que a resposta revela

| Sinais | Tipo | Rota | Identidade visual |
|---|---|---|---|
| não guarda dado · uma tela · público externo · objetivo é convencer | **Página / landing** | A | resolve |
| não guarda dado · regra própria · roda na tela | **Jogo / experimento / ferramentinha** | A | resolve |
| gatilho → passos → resultado · roda sozinho · sem tela | **Automação / integração** | A (B se forem vários fluxos) | — |
| um texto, um post, um roteiro, um relatório | **Conteúdo / análise** | A | — |
| guarda dado que cresce · mais de um tipo de usuário · login · várias telas · integra com serviço externo | **Sistema** | **B** | resolve |
| pasta/ferramenta que a equipe usa pra trabalhar, com configuração e vários pedaços | **Ambiente / ferramenta interna** | **B** | resolve, se tiver tela |

A coluna da direita diz se a etapa de **identidade visual** da Rodada 1 se aplica: `resolve` = tem
tela, então o design system entra no contexto antes de qualquer outra coisa; `—` = pule a etapa
explicitamente.

### A regra do PRD

> Gere PRD quando **dois ou mais** destes forem verdade:
> guarda dado que cresce · tem mais de um tipo de usuário · tem login · integra com serviço externo ·
> passa de 3 telas · vai ser construído em fases.

- **Rota A — peça única:** vá direto pra Rodada 1. Sem PRD. Um prompt CTC resolve, e PRD aqui só atrasa.
- **Rota B — sistema/ambiente:** avise e siga:
  > Isso não é uma peça só, é um sistema. Vou montar um **PRD** — o documento que fica dentro do projeto,
  > guarda os critérios de aceite pra você conferir depois de pronto, e evolui junto com ele.
  > Depois disso a gente tira dali o prompt da primeira fatia. Continua sendo Contexto, Tarefa e Critério —
  > só que escrito uma vez e reaproveitado a cada etapa.

**Na dúvida entre A e B, pergunte:** *"você imagina isso crescendo em versões nos próximos meses, ou é uma coisa só que você faz e acabou?"* — crescer em versões é B.

### Integrações — aprofunde só se apareceram

Para cada ferramenta citada, três perguntas rápidas (elas evitam o projeto travar no meio):
**você já tem conta paga?** · **já tem a chave de API / acesso?** · **o que exatamente precisa acontecer ali** (ler? escrever? avisar?).
Se não tiver acesso, isso vira uma linha de **risco** no PRD, não um impedimento agora.

---

## RODADA 1 — CONTEXTO

Objetivo: reunir as **restrições**, não a biografia do projeto. A régua:

> Cada frase do contexto tem que impedir um erro específico. Se você tirar a frase e nada de ruim
> pode acontecer, ela não é contexto — é enfeite.

1. **Do zero ou em cima de algo que já existe?** Se existe: onde está e o que **não** pode quebrar?
2. **Pra quem é e onde vai rodar?** (quem usa, em que aparelho, com que nível de técnica)
3. **O que já está decidido e não se discute?** (ferramenta, plataforma, identidade visual, prazo, orçamento)
4. **O que já foi tentado e não deu certo?** — vale ouro, evita repetir o erro.

Perguntas específicas por tipo estão em `references/tipos-de-entrega.md`. **Leia o bloco do tipo certo.**

### Identidade visual — resolva aqui, antes de pedir referência

**Só quando o pedido tem tela:** landing/página, sistema, app/feature, ambiente com interface.
Automação sem tela, conteúdo e análise **pulam esta etapa** — fale isso em uma linha
(*"não tem tela, então não tem design system pra resolver"*) e vá direto pra referência.

Design system é a resposta pronta da pergunta 3 desta rodada — *o que já está decidido e não se
discute*. Resolvido aqui, a IA para de escolher cor, fonte e raio por conta própria em toda tela
do projeto, hoje e nas fases seguintes.

**1. Varra antes de perguntar.** Vale a regra 5: você não pergunta o que consegue descobrir sozinho.

**Onde 1 — design systems instalados como skill.** O marcador é duplo, e os dois são obrigatórios:
(a) o `SKILL.md` tem, **dentro do frontmatter**, a linha `type: design-system` **e** a linha
`ds-tokens: <arquivo>`; (b) o arquivo apontado existe na **raiz** da skill.
Frontmatter sem arquivo = DS quebrado (avise a pessoa). Arquivo de tokens sem frontmatter = CSS
solto, não é DS (ignore). O nome do arquivo é o que `ds-tokens` declarar; se o campo faltar, a
varredura tenta `tokens.css` · `colors_and_type.css` · `design-tokens.css`, nesta ordem.

```bash
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

Saída: `nome-da-skill · Marca · #cor · caminho dos tokens`. É `find` e não glob porque o zsh aborta
o comando inteiro quando um glob não casa; é `head -20` porque sem isso qualquer arquivo que
apenas **documente** o campo `type: design-system` (esta skill, por exemplo) vira falso positivo;
e a primeira coluna é o campo `name` do frontmatter, não o nome da pasta — é pelo `name` que a skill
é invocada, e os dois podem divergir.

Só pra saber se existe algum:

```bash
find ~/.claude/skills ./.claude/skills -maxdepth 2 -name SKILL.md 2>/dev/null | xargs -I{} sh -c 'head -20 "{}" | grep -qE "^type:[[:space:]]*design-system[[:space:]]*$" && echo "{}"'
```

**Onde 2 — dentro do projeto atual**, se houver um: arquivo de tokens, paleta customizada no
Tailwind, ou menção no `CLAUDE.md`.

```bash
find . -maxdepth 4 -path ./node_modules -prune -o \( -name '*tokens*.css' -o -name 'globals.css' -o -name 'theme.css' \) -print 2>/dev/null
grep -nE '(colors|extend|fontFamily)' tailwind.config.* 2>/dev/null | head -20
grep -niE 'design system|identidade visual|paleta|tokens|--brand' CLAUDE.md README.md docs/*.md 2>/dev/null | head -10
```

Traga o que achou como fato, não como pergunta: *"vi que o projeto já tem `src/styles/tokens.css`
com uma paleta própria — é essa a identidade?"*

**2. Confira se a skill do método existe — antes de oferecer.** A etapa não pode oferecer um botão
que você não consegue apertar:

```bash
[ -f ~/.claude/skills/criar-design-system/SKILL.md ] && echo instalada || echo ausente
```

Se estiver **ausente**, a etapa não quebra: ela encolhe. Diga em uma linha que "criar um novo agora"
depende da skill `criar-design-system` (que se instala em `~/.claude/skills/criar-design-system/`),
tire essa opção da pergunta e siga com as outras duas — usar um DS existente ou seguir sem.
Sem nenhum DS instalado **e** sem a skill do método, sobra uma opção só: seguir sem — e aí a
referência visual do bloco seguinte deixa de ser opcional.

**3. Ofereça o que encontrou.** `AskUserQuestion`, opções prontas, default explícito.
Pergunta: **"Qual identidade visual esse projeto segue?"**

- **uma opção por DS encontrado** — `<nome da skill> · <marca> · <cor de assinatura>`.
  A cor vai junto porque é por ela que a pessoa reconhece o DS sem abrir arquivo nenhum.
- **Criar um agora** — *"eu monto um design system seu (tokens + showcase), instalo, e volto pra cá."*
- **Seguir sem** — *"a IA escolhe cor, fonte e espaçamento por conta."*

O default é explícito, como toda pergunta desta skill: se existe **exatamente um** DS instalado,
ele é o default (*"se você não disser nada, eu uso o `<nome>`"*). Se não existe nenhum, o default
é criar. Se o projeto já tem tokens próprios, o default é usar o que o projeto tem.

**4. Aja conforme a escolha.**

| Escolha | O que você faz |
|---|---|
| **Usar um que já existe** | Invoque a skill daquele DS agora (`Skill`, nome = a **primeira coluna da varredura**, que é o campo `name` do frontmatter — pode não ser igual ao nome da pasta) e leve pro bloco CONTEXTO do prompt final a linha que trava a decisão (abaixo). |
| **Criar um novo** | Invoque `criar-design-system` e **deixe ela conduzir** até o DS ficar instalado em `~/.claude/skills/<nome>/`. Depois **volte pra Rodada 1** com o DS novo como contexto — não monte o prompt no meio do caminho. |
| **Seguir sem** | Registre `[SEM DESIGN SYSTEM — a IA vai escolher cor, fonte e espaçamento]`, no mesmo espírito do `[SEM REFERÊNCIA VISUAL]`. A pessoa precisa **enxergar** do que abriu mão, não descobrir na entrega. |

A linha que entra no CONTEXTO quando existe DS — escreva assim, na voz da pessoa:

> A identidade visual deste projeto é a skill `<nome>` (`~/.claude/skills/<nome>/`).
> Leia ela antes de escrever qualquer CSS e não invente cor, fonte, raio ou espaçamento fora dela.

### Peça referência aqui — sempre

Esse é o passo que mais muda a qualidade e o que mais gente esquece. Ele e a etapa de cima
resolvem o mesmo problema — a IA escolhendo o visual por conta — e se revezam:
**quem tem design system não precisa de referência de estilo** (aqui você pede referência de
**layout e conteúdo**: que seções, em que ordem, exemplo real do dado que vai entrar);
**quem não tem precisa da referência**, e aí ela deixa de ser opcional. Ficar sem os dois é
escolher que a IA decida tudo.

> Antes de eu escrever: tem alguma coisa que você possa me **mostrar** em vez de descrever?
> - **print de tela** de uma referência que você gosta (ou do que você tem hoje)
> - **link** de um produto/concorrente que chega perto
> - **documento**: briefing, PDF, planilha, ata de reunião, mensagem do cliente
> - **arquivo do projeto**, se já existe código
> - **um exemplo real** do dado ou conteúdo que vai entrar ali
>
> Pode arrastar aqui. Se não tiver nada, seguimos pela descrição — mas aí eu escolho por você.

Se mandarem algo: **abra de fato** (Read, WebFetch, ou olhando a imagem) e devolva em uma frase o que você extraiu — vira linha de contexto, com a fonte citada. Extraia também o que a pessoa **não** quer.
Se não mandarem: registre `[SEM REFERÊNCIA VISUAL — a IA vai escolher o estilo]`, pra ficar claro do que a pessoa abriu mão.
Se também não houver design system, as duas marcas entram no contexto, uma embaixo da outra — é o
cenário em que absolutamente nada do visual foi decidido por quem pediu.

---

## RODADA 2 — TAREFA

Objetivo: uma lista **numerada e fechada**.

1. **Proponha você a lista** — 3 a 6 itens com verbo na frente, a partir do contexto — e peça pra cortar/adicionar. Mais rápido que perguntar do zero.
2. **Qual é o mínimo que já teria valor?** Separe `AGORA` e `DEPOIS`. O `DEPOIS` sai do prompt e vira "fora de escopo" (na Rota B, vira a fase 2 do PRD).
3. **O que está explicitamente proibido?** (não instalar dependência nova, não mexer no layout, não trocar o banco, não passar de X páginas)

Feche com a frase que segura o escopo: **"Implemente exatamente estas coisas, nada além delas."**

Na Rota B, a tarefa é só da **primeira fatia** — a menor coisa que já dá pra usar de ponta a ponta. O resto vira roadmap no PRD.

---

## RODADA 3 — CRITÉRIO DE ACEITE (antes de construir — sempre)

A rodada que quase todo mundo pula. **Não deixe pular.** Se quiserem correr pro código, diga uma vez:

> Só mais um passo — é o que evita você receber "pronto!" sem saber se ficou bom. Leva 1 minuto.

### A régua do critério falseável

> Um critério tem que poder **falhar**. Se não existe jeito de dar errado, é desejo, não critério.

| Desejo (rejeite) | Critério (aceite) |
|---|---|
| "Que fique bonito" | "Passa no celular de 375px sem barra de rolagem lateral" |
| "Que seja rápido" | "A página abre em menos de 2s no 4G" |
| "Que funcione bem" | "Dá pra preencher o formulário e o e-mail chega na minha caixa" |
| "Que seja fácil de usar" | "Um usuário novo cadastra o primeiro cliente em menos de 1 minuto, sem instrução" |

Perguntas para extrair critério:

1. **Como você vai testar isso quando eu entregar? Descreve o clique-a-clique.** *(a pergunta mais importante da skill)*
2. **O que faria você olhar e dizer "não é isso"?** — anti-critérios são mais fáceis de nomear.
3. **Tem número em algum lugar?** (quantidade, tamanho, tempo, prazo, limite)
4. **O que precisa continuar funcionando** que já funciona hoje?

Traduza cada resposta numa linha verificável. Mire em **4 a 7 critérios**: menos não segura, mais ninguém checa.
Se a pessoa responder um desejo, **não brigue** — guarde e devolva convertido ("'sem cara de template' eu vou escrever como 'nenhum degradê roxo e nenhum ícone genérico', pode ser?").

---

## MONTAGEM — Rota A (peça única)

Um bloco de código, pronto pra colar:

```
## CONTEXTO
<fatos e restrições, um por linha, cada um impedindo um erro específico>
<identidade visual: a linha do design system adotado — ou [SEM DESIGN SYSTEM], quando não houver>
<referências recebidas, com o que foi extraído delas>

## TAREFA
<lista numerada e fechada>
Implemente exatamente estas coisas, nada além delas.

### Fora de escopo
<o que ficou pra depois — explicitamente>

## CRITÉRIO DE ACEITE
Só considere pronto quando tudo abaixo for verdade:
<4 a 7 linhas verificáveis>

## ENTREGA
Ao final, responda em 3 bullets: o que foi feito, onde, e como eu testo em 10 segundos.
```

Regras: escreva na **voz da pessoa** (primeira pessoa — ela vai colar como se fosse dela) · marque suposições com `[SUPOSIÇÃO]` na linha · anexo não vira texto, vira lembrete: `Anexo: print da referência (mandar junto com este prompt)` · a linha do design system vem **antes** das referências, porque é a restrição mais forte do bloco.

Antes do bloco, a explicação do que gerou (veja **Modo de saída**). Depois do bloco, conforme o modo:

- **Só gerar:** ofereça, nesta ordem, **salvar em arquivo** (`prompt-<assunto>.md`) · **ajustar** · **executar aqui** (só se estiver num projeto).
- **Executar aqui:** não ofereça nada. Comece a implementar e termine com o relatório critério por critério.

---

## MONTAGEM — Rota B (sistema / ambiente)

Gere **dois artefatos**, nesta ordem. No modo **executar aqui**, o segundo vira o plano que você executa:

### 1. `docs/PRD.md` — dentro do projeto

Use `references/prd-template.md`. Regras que não se negociam:

- **Mora no projeto**, em `docs/PRD.md` — não no chat, não numa pasta separada. Documentação que não viaja junto com o código morre.
- **Critérios de aceite ficam como checklist** (`- [ ]`), agrupados por fase. É isso que você vai marcar depois de construir — é o "bater os critérios" na prática.
- **Escopo em fases**, e a fase 1 é a menor coisa usável de ponta a ponta.
- **Seção de decisões com data absoluta** (`2026-08-02`, nunca "hoje" ou "semana passada").
- **Seção de riscos e pendências** — acesso a API que ainda não tem, dado que ainda não existe, decisão que falta.
- **A identidade visual entra em Decisões** (sistema com tela): qual design system foi adotado, ou `[SEM DESIGN SYSTEM]`. Decisão visual que não fica escrita é decisão que vai ser tomada de novo, diferente, na fase 2.
- Toda linha que você inventou entra marcada `[SUPOSIÇÃO]`. Uma suposição visível vira uma pergunta; uma escondida vira retrabalho.

Depois de escrever, ofereça: *"quero apontar o CLAUDE.md do projeto pro PRD, pra toda sessão futura ler ele antes de mexer no código?"* — se sim, acrescente ao `CLAUDE.md`:

```
## Documentação
Antes de alterar qualquer coisa, leia docs/PRD.md — escopo, decisões e critérios de aceite.
Ao terminar uma fatia, marque os critérios cumpridos e registre decisões novas na seção Decisões, com data.
```

### 2. O prompt CTC da fatia 1

Mesmo formato da Rota A, com uma diferença no contexto:

```
## CONTEXTO
Leia docs/PRD.md deste projeto antes de qualquer coisa — ele tem o escopo, as decisões e os critérios.
Estamos construindo a FASE 1. Nada de fase posterior entra agora.
A identidade visual é a skill <nome> — leia ela antes de escrever qualquer CSS e não invente cor,
fonte, raio ou espaçamento fora dela.   <ou: [SEM DESIGN SYSTEM — a IA vai escolher o visual]>
<demais restrições>
```

E uma diferença na entrega:

```
## ENTREGA
Ao final: 3 bullets do que foi feito e como testo, e atualize docs/PRD.md —
marque os critérios da fase 1 que passaram, e registre em Decisões o que você decidiu por conta própria.
```

---

## Manutenção do PRD (o documento vivo)

Quando a pessoa voltar com "terminei essa parte", "mudou uma coisa" ou "quero a próxima fase",
**não comece um PRD novo**. Leia `docs/PRD.md` e:

1. **Confira os critérios** um a um contra o que existe — teste, não confie. Marque `- [x]` só o que você verificou.
2. **Critério que falhou vira tarefa**, não vira desculpa. Liste o que falta em uma linha por item.
3. **Mudou de ideia?** Não apague o que estava escrito: risque e registre em Decisões com data e motivo. O histórico é o que impede a discussão de girar em círculo três meses depois.
4. **Fase concluída** → promova a fase seguinte, revise se ela ainda faz sentido (quase nunca faz, do jeito que foi escrita) e monte o prompt CTC dela. No modo **executar aqui**, monte e execute.
5. **Riscos** viram fatos ou somem — não deixe risco velho apodrecendo na lista.

---

## Arquivos de apoio

- `references/tipos-de-entrega.md` — perguntas por tipo (landing, sistema, app/feature, automação, conteúdo, análise, agente de IA). Leia o bloco certo antes da Rodada 1.
- `references/prd-template.md` — template do PRD e as regras de evolução.
- `references/exemplo-completo.md` — um prompt CTC pronto, real, como padrão de qualidade e material de aula.

## Modo aula

Se a pessoa disser que está **gravando/ensinando**, narre a camada antes de cada rodada
("agora a gente fecha o CONTEXTO — repare que toda pergunta aqui existe pra impedir um erro específico")
e, no fim, mostre o contraste: o pedido original de uma linha ao lado do que foi construído.
