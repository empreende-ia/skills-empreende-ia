# Antipadrões — os clichês de design gerado por IA

Todo item aqui é **proibido**. Não porque seja feio isoladamente, mas porque é o que sai quando
ninguém decidiu nada — e quem olha reconhece na hora que ninguém decidiu nada.

**Quando passar esta lista:** duas vezes, sempre.
1. No fim da **Rodada 1**, antes de mostrar as direções.
2. No fim da **Rodada 3**, olhando o screenshot do showcase.

---

## A lista proibida

### 1. Creme `#F4F1EA` com serifada e acento terracota

**Por que é clichê:** virou o preset de "marca artesanal / boutique / wellness" de toda IA desde 2023.
Três marcas diferentes com essa paleta são indistinguíveis.

**Faça em vez disso:** se a marca pede calor, escolha **um** dos três eixos e comprometa-se — ou o
papel quente (mas com uma face grotesca e cor fria), ou a serifada (mas sobre branco puro e frio), ou
o terracota (mas como bloco estrutural, não como acento tímido). O clichê é a combinação dos três.

---

### 2. Preto quase puro com um único verde-ácido ou vermelhão de destaque

**Por que é clichê:** o "hacker premium" que toda landing de cripto, IA e agência técnica usou.
Lê como "quero parecer avançado" — o oposto de parecer avançado.

**Faça em vez disso:** mantenha o escuro, troque a acidez. Um `#0A0A0A` com laranja-sinal, âmbar,
azul elétrico ou ciano lê tão técnico e não lê genérico. Ou mantenha a cor e troque o preto: escuro
com temperatura (`#0F172A` azulado, `#1C1917` quente) já resolve metade.

---

### 3. Gradiente roxo-para-azul em hero branco

**Por que é clichê:** o degradê do Stripe de 2019, copiado até virar sinônimo de "SaaS genérico".
Mais de metade das landings geradas por IA têm essa faixa.

**Faça em vez disso:** o gradiente pode ficar — mas dentro da **mesma família de hue** (esmeralda→verde-água,
âmbar→laranja) e em superfície pequena: número, ícone, borda, glow. Gradiente que ocupa o hero inteiro
é a coisa mais datável de uma página. Se precisa de energia no hero, use **uma cor cheia** ou uma foto real.

---

### 4. Inter ou Space Grotesk como escolha "segura"

**Por que é clichê:** é o `system-ui` com passo extra. Inter foi desenhada pra desaparecer — usar como
face de marca é declarar que não houve escolha de marca.

**Faça em vez disso:** veja o banco de faces em `direcoes-visuais.md`. General Sans, Switzer, Geist,
Onest e Schibsted Grotesk fazem o mesmo trabalho com identidade. Se Inter for mesmo a certa (produto
denso, muita interface, muita leitura em tela), **diga por que** e diferencie: tracking negativo forte
no display, ou uma serifada de display por cima.

---

### 5. Emoji como marcador de seção

**Por que é clichê:** 🚀 no título, ✨ no diferencial, 🎯 no objetivo. Renderiza diferente em cada
sistema, quebra alinhamento, e denuncia o texto gerado a três metros de distância.

**Faça em vez disso:** ícone de linha da biblioteca declarada (Lucide, Phosphor, Remix Icon) na cor da
assinatura, tamanho fixo, alinhado à baseline. Ou nada: um overline em caixa-alta com tracking largo
resolve hierarquia melhor que qualquer emoji.

---

### 6. Tudo centralizado

**Por que é clichê:** centralizar é a decisão que se toma quando não se tomou decisão de grade. Texto
centralizado com mais de duas linhas custa leitura (a borda esquerda dança a cada linha), e página
inteira centralizada não tem hierarquia — tudo tem o mesmo peso.

**Faça em vez disso:** hero centralizado é aceitável **uma vez**. Do resto da página pra baixo,
alinhe à esquerda e use grade assimétrica (título à esquerda, conteúdo à direita; ou 2/3 + 1/3).
Parágrafo longo é sempre alinhado à esquerda.

---

### 7. `border-radius: 8px` em absolutamente tudo

**Por que é clichê:** achata a hierarquia. Botão, card, imagem, modal e avatar com o mesmo raio dizem
que estão no mesmo nível — e não estão.

**Faça em vez disso:** raio proporcional ao elemento (botão 12px, card 16px, container 24px, avatar
full). Ou raio 0 em tudo, se for decisão de marca declarada. O erro é o valor único aplicado sem critério.

---

### 8. Trilho / barra de acento colorido na lateral de card arredondado

**Por que é clichê:** o `border-left: 4px solid <cor>` em card `rounded-lg`. Bootstrap alert de 2015,
e a IA reproduz porque é fácil. Além de datado, é geometricamente errado: a barra reta briga com o
canto arredondado e sobra um degrau visível.

**Faça em vez disso:** diferencie o card pela **superfície** (fundo levemente diferente), pela **borda
inteira** na cor do estado, ou por um **ícone** na cor do estado. Se quiser mesmo a barra lateral,
então o card é de canto reto — e aí é decisão, não acidente.

---

### 9. Numeração 01 / 02 / 03 como decoração

**Por que é clichê:** número gigante em cinza-claro atrás do título de cards que não têm ordem nenhuma.
Promete sequência ("passo 1, passo 2") e entrega uma lista sem ordem — o leitor procura a lógica e não
acha.

**Faça em vez disso:** numere **só o que é sequência real** (etapas de um processo, módulos de um curso,
fases de um projeto). Em lista sem ordem, o que hierarquiza é peso, ícone ou tamanho — não número falso.

---

### 10. Hairlines de jornal + colunas densas imitando broadsheet

**Por que é clichê:** o preset "editorial" — filete de 1px por toda parte, três colunas de texto justificado,
serifada condensada, data em caixa-alta no topo. Parece jornal de 1970 porque copia a solução de um
problema de impressão que não existe na tela.

**Faça em vez disso:** editorial na tela é **escala tipográfica agressiva** (display muito grande ao lado
de corpo pequeno), **medida de linha controlada** (60–75 caracteres, uma coluna) e **muito espaço vazio**.
Filete só onde separa de verdade — e um só, não uma grade deles.

---

## Antipadrões de segunda ordem (aparecem no showcase)

| Antipadrão | O que fazer |
|---|---|
| Sombra dura `0 4px 4px rgba(0,0,0,.5)` | Sombra difusa com Y > blur/2 e alpha baixo, ou glow, ou nada |
| Card flutuando com sombra em cima de fundo escuro | Borda mais clara ou superfície elevada — sombra preta em fundo preto não existe |
| A cor de assinatura em 40% da tela | Assinatura é acento: mire em menos de 10% |
| Verde da marca = verde de sucesso | Desloque o hue do sucesso em 25° ou mais |
| Placeholder "Lorem ipsum" / "Seu texto aqui" no entregável | Texto real da marca, mesmo que curto |
| Ícone de biblioteca diferente na mesma tela | Uma biblioteca só, declarada no README |
| Hover que muda 3 propriedades ao mesmo tempo | Uma ou duas: cor de borda + sombra, e ponto |
| Animação de entrada em elemento que já está visível | Entrada só no que entra; estado permanente não pisca |
| Tema claro que é o escuro invertido | Desenhe os dois: sombra aparece no claro, borda pesa menos |
| Fonte carregada por CDN em arquivo "standalone" | Ou embuta, ou aceite o fallback e declare a pilha |

---

## A pergunta de verificação final

Antes de entregar qualquer direção, responda por escrito:

> **Se eu trocar o nome e a cor, essa marca vira qualquer outra?**

Se a resposta for sim, falta o princípio 5: as duas ou três assinaturas memoráveis.
Volte e crie uma — um detalhe reproduzível, escrito como receita, que só essa marca tem.
