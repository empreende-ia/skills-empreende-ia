---
name: copy-hormozi
description: "Escreve copy de resposta direta no método Alex Hormozi — página de vendas, VSL, roteiro de anúncio, sequência de e-mail de lançamento, headline/gancho, bio de oferta — partindo da oferta já desenhada (o Modelo de Oferta preenchido, quando existir) ou destilando a oferta antes de escrever. Aplica a Value Equation frase a frase, a fórmula MAGIC de naming, empilhamento de valor com preço-âncora, garantia e as 4 objeções reais (dinheiro, tempo, 'não funciona pra mim', 'não confio em você'), calibrado pro mercado brasileiro (R$, parcelamento, CDC). Também AUDITA copy pronta e diz por que não converte. Use quando pedirem 'escreve a copy', 'página/carta de vendas', 'VSL', 'roteiro de anúncio', 'e-mail de lançamento', 'headline', 'gancho', 'copy estilo Hormozi', 'melhora essa copy', 'por que essa página não converte'."
---

# Copy Hormozi — da oferta à página que vende

> **Skill de escrita.** Começa quando a oferta já está desenhada: pega o documento da oferta
> e escreve a peça que vende. Conhecimento denso vive em `references/` — carregue só o arquivo do
> formato em que estiver. Os moldes de saída estão em `templates/`.
>
> **Regra que governa tudo:** copy não cria valor, copy *revela* valor. Se a oferta é fraca,
> nenhuma frase salva. Quando a oferta chegar fraca, conserte a oferta antes (Fase 0).

## Roteador

| O que pediram | Formato | Reference | Template |
|---|---|---|---|
| "página de vendas", "carta de vendas", "landing que vende", "sales letter" | Página longa | `carta-vsl.md` | `pagina-de-vendas.md` |
| "VSL", "vídeo de vendas", "roteiro do vídeo da página" | VSL 8–25 min | `carta-vsl.md` | `vsl.md` |
| "anúncio", "criativo", "ad", "roteiro de reels pra tráfego" | Ad (estático/vídeo) | `ads.md` | `anuncios.md` |
| "e-mail de lançamento", "sequência", "carrinho abrindo/fechando" | Sequência 7–12 e-mails | `emails.md` | `sequencia-email.md` |
| "headline", "gancho", "hook", "título", "nome da oferta" | Peça curta | `ganchos.md` | inline |
| "melhora essa copy", "por que não converte", "audita" | **Modo AUDITAR** | `voz.md` + o do formato | `qa-copy.md` |
| "não tenho a oferta pronta", só tema/ideia | **Fase 0 obrigatória** | — | `brief-oferta.md` |

Carregue `references/voz.md` **sempre** — é a régua de voz, vale pra todo formato.
Carregue `references/objecoes.md` sempre que a peça tiver que fechar venda (página, VSL, e-mail de fechamento).
Carregue `references/conformidade.md` antes de entregar qualquer peça com número, promessa ou prazo.

---

## Fase 0 — Origem da oferta (nunca escreva sem isso)

Três caminhos, nesta ordem de preferência:

1. **Existe documento da oferta.** Procure o Modelo de Oferta preenchido (ou outro documento de
   oferta) anexado na conversa ou na pasta do projeto atual. Se existir, leia inteiro e vá pra Fase 1. Não reinvente a oferta.
2. **Existe oferta na cabeça do usuário.** Rode o intake de `templates/brief-oferta.md` —
   9 perguntas, pergunte só o que faltar, proponha default pra tudo.
3. **Não existe oferta.** Pare de escrever. Diga: *"Isso não é problema de copy, é problema de
   oferta."* e ofereça montar a oferta primeiro (público, promessa, prova, preço, garantia).

**Veto de entrada.** Não escreva se qualquer um for verdade:

- Promessa é um tópico, não um resultado ("aprender IA", "dominar n8n").
- Público é "todo mundo" / "qualquer pessoa que queira".
- Não existe prova nenhuma — nem depoimento, nem número, nem caso, nem demonstração ao vivo.
- Pediram urgência/escassez falsa (contador que reseta, "últimas 3 vagas" inventado). **Veto duro.**

Nos três primeiros casos, escreva mesmo assim **se o usuário reafirmar** — mas abra o entregável
com um bloco `RISCO` dizendo o que vai limitar a conversão. No quarto, não. Proponha um
mecanismo real (`references/conformidade.md`).

---

## Fase 1 — Ângulo (15 min antes da primeira frase)

Preencha estes 6 campos. Eles cabem em meia página e determinam 80% do resultado.

| Campo | Regra | Exemplo ruim → bom |
|---|---|---|
| **Uma pessoa** | Nome, idade, o que faz, o que ele disse com as palavras dele | "empreendedores" → "Rafael, 34, dono de agência de tráfego com 4 clientes, disse 'eu virei funcionário do meu próprio negócio'" |
| **Estado atual doloroso** | O que dói HOJE, na segunda-feira de manhã | "falta de eficiência" → "responde orçamento no WhatsApp às 23h" |
| **Destino** | Onde ele acorda depois. Concreto, com número e prazo | "mais produtividade" → "3 automações rodando e 12h/semana de volta em 30 dias" |
| **Mecanismo nomeado** | Como se chega lá — com NOME próprio. Sem nome, vira commodity | "usando IA" → "o Método das 3 Camadas" |
| **Prova** | O que faz ele acreditar. Ranqueie: demonstração ao vivo > caso com número > depoimento de igual > sua credencial | "sou especialista" → "print do painel: 1.847 mensagens respondidas sozinho em 30 dias" |
| **Objeção #1** | A real, não a educada. Escolha uma das 4 (`objecoes.md`) e mate ela no título | — |

**Teste do ângulo:** leia o destino em voz alta pro espelho. Se você não sentiria vergonha de
prometer isso pra um amigo, o ângulo tá calibrado. Se sentiria, ou a promessa é vaga demais
(fraca) ou grande demais (mentira). Ajuste até doer na medida.

---

## Fase 2 — Escrita

Abra o template do formato e escreva no molde. Três coisas valem em todos:

**A ordem é sempre a mesma.** Atenção → problema que ele reconhece → mecanismo (por que agora
é diferente) → prova → oferta empilhada → preço ancorado → risco invertido (garantia) → razão
pra agir hoje → chamada única.

**Venda o destino, não o veículo.** *"Sell the vacation, not the flight."* Ninguém quer aprender
n8n. Querem parar de responder WhatsApp às 23h. Toda vez que a frase descrever o produto,
reescreva pra descrever a vida depois do produto.

**Cada frase paga o aluguel.** Passe frase a frase perguntando: isso aumenta o resultado
sonhado, aumenta a chance percebida, diminui o tempo ou diminui o esforço? Se não faz nenhum
dos quatro, corta. Ver `references/voz.md` → "A passagem de quatro alavancas".

---

## Fase 3 — Passagem Hormozi

Depois do primeiro rascunho, rode as quatro passadas **nesta ordem**. Uma por vez, cada uma
até o fim do documento. Misturar as quatro é o que produz copy morna.

1. **Passada da especificidade.** Todo número vago vira número exato. "Muitos alunos" → "1.847".
   "Rápido" → "em 9 dias". "Aumenta o faturamento" → "de R$8.400 pra R$21.000/mês". Se você
   não tem o número, ou vai buscar ou corta a frase — nunca invente (`conformidade.md`).
2. **Passada do corte.** Corte 20% das palavras sem perder nenhum argumento. Advérbio some,
   adjetivo duplicado some, frase de transição some. Copy longa vende; copy inchada não.
3. **Passada da objeção.** Leia como cético. Toda vez que você pensar "tá, mas...", esse "mas"
   vira um bloco novo na peça, no lugar exato onde surgiu.
4. **Passada da voz.** Rode `references/voz.md` — palavras banidas, ritmo, "a matemática",
   e o teste de leitura em voz alta.

---

## Fase 4 — Variantes e entrega

Nunca entregue uma versão só do que é testável:

- **5 headlines** (fórmulas diferentes, não sinônimos da mesma) + sua recomendação e o porquê.
- **3 aberturas/leads** de ângulos distintos (dor / prova / contrarian).
- **2 CTAs** (direto vs. redução de risco).
- **1 versão curta** da peça (para story, DM, WhatsApp) — sempre.

Feche com o **QA** de `templates/qa-copy.md`. Nenhuma peça sai com item vermelho.

**Onde salvar.** Se veio de um offer stack, ao lado dele (`.../02-copy/`). Senão, `copy/<slug>/`
no diretório atual. Um arquivo por formato + `00-angulo.md` com a Fase 1.

---

## Regras de ouro

1. **Clareza vence esperteza.** Se a pessoa precisa reler pra entender, você perdeu. Trocadilho
   em headline é vaidade de copywriter.
2. **Específico vence superlativo.** "O melhor curso de IA" não vale nada. "847 alunos, 63%
   fecharam o primeiro cliente em 30 dias" vale tudo.
3. **A objeção que você não escreve é a que mata a venda.** Escreva ela antes que ele pense.
4. **Preço nunca aparece antes do valor.** Primeiro o que vale, depois o que custa. Sempre.
5. **Prova > promessa.** Uma promessa sem prova é ruído. Prefira mostrar a afirmar.
6. **Uma chamada por peça.** Duas ofertas na mesma página = nenhuma oferta.
7. **Escreva pra uma pessoa.** "Você", singular, sempre. Nunca "vocês", "pessoal", "galera".
8. **Urgência real ou nenhuma.** Um print de contador falso circulando num grupo de WhatsApp
   acaba com a marca. Não vale o teste A/B.
9. **Frase curta puxa a próxima.** Alterne 4 palavras / 20 palavras. Parágrafo de 1 a 3 linhas.
10. **Se você não compraria pelo preço, a copy não conserta.** Volte pra oferta.

---

## Modo AUDITAR

Quando entregarem copy pronta ("melhora isso", "por que não converte"):

1. **Não reescreva primeiro.** Diagnostique. Rode `templates/qa-copy.md` inteiro e devolva o
   placar: CRÍTICO quebra a conversão / MELHORAR deixa dinheiro na mesa / OK.
2. **Ranqueie por impacto**, não por ordem de aparição. Headline e primeiro parágrafo primeiro:
   é onde 80% desiste.
3. **Reescreva só os 3 blocos de maior impacto**, lado a lado (antes → depois → por quê).
4. **Só então** ofereça reescrever a peça inteira.

Diagnóstico rápido por sintoma:

| Sintoma | Causa quase sempre | Onde mexer |
|---|---|---|
| Muito clique, nenhuma venda | Anúncio promete o que a página não entrega | Alinhar promessa ad↔página |
| Lê tudo e não compra | Falta prova ou falta inversão de risco | Prova + garantia |
| "Vou pensar" | Nenhuma razão real pra hoje | Mecanismo de urgência genuíno |
| "Tá caro" | Preço apareceu antes do valor empilhado | Ordem da página |
| Ninguém passa do título | Headline descreve tópico, não resultado | `ganchos.md` |
| Vende só pra quem já te conhece | Copy assume contexto que o frio não tem | Reescrever o lead pro nível de consciência |

---

## Escopo

**Faço:** headline, lead, página de vendas, VSL, anúncio, e-mail, story/DM/WhatsApp, bio de
oferta, nome de oferta, auditoria de copy, variantes pra teste.

**Não faço:** engenharia de oferta, design e layout da página, conteúdo de topo pra redes
sociais, mídia paga e segmentação, currículo de curso.

Quando o pedido for de outra caixa, diga qual e ofereça o handoff — não faça meio torto.
