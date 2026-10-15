---
name: personalizar-design-system
description: "Parte de um design system que já existe e o adapta a uma marca — troca nome, wordmark, cor de assinatura e exemplos, preservando a estrutura de tokens, as escalas e as regras que já funcionam. Entrega os 4 arquivos numa pasta nova, verificados por screenshot, e instala como skill. Use quando alguém disser /personalizar-design-system, 'quero esse design system mas com a minha marca', 'adapta esse exemplo pro meu negócio', 'personalizar/customizar um design system pronto', 'partir de um sistema que já existe', 'já tenho logo e quero um sistema em cima dele', ou quando a pessoa apontar um DS de exemplo e disser que reconheceu a marca dela ali."
user-invocable: true
---

# /personalizar-design-system — pegue um sistema pronto e vista a sua marca

Esta é a **irmã mais rápida** da `criar-design-system`. Lá se constrói uma identidade do zero, com uma
rodada inteira dedicada a propor direções visuais e deixar a pessoa escolher. Aqui não se decide
direção nenhuma: ela **já foi decidida** por quem escreveu a base. O trabalho é outro — descobrir a
marca, extrair a cor real dela e **transplantar**.

| Artefato | Para quem | Onde vive |
|---|---|---|
| `tokens.css` | máquinas | raiz da pasta nova |
| `showcase.html` | humanos | raiz da pasta nova — abre com duplo clique |
| `SKILL.md` + `README.md` | agentes de IA | a pasta de skills pessoais desta máquina |

Se ao final existir uma pasta com o nome novo e o texto velho por dentro, a skill falhou.

---

## Quando NÃO usar esta skill

Use `criar-design-system` — não esta — em qualquer um destes casos:

| Sinal | Por quê |
|---|---|
| **A marca não se parece com nenhuma das bases.** A pessoa olhou as opções e nenhuma deu o clique. | Personalizar a "menos pior" entrega um sistema que ninguém defende. Direção errada não se conserta com hex novo. |
| **A pessoa quer explorar direções.** "Será que fica melhor claro ou escuro?" | Isso é a Rodada 1 da irmã: 2 ou 3 direções propostas lado a lado. Aqui não existe essa rodada — a direção veio pronta. |
| **A base escolhida é de um arquétipo oposto ao negócio.** Clínica infantil sobre a base de fintech densa; consultoria de governança sobre a base de comida de rua. | Estrutura carrega significado. Densidade alta e mono tabular dizem "operação", por mais sálvia que se pinte por cima. |
| **A pessoa já tem manual de marca completo** (grid, aplicações, malha de proporção). | Aí não é personalizar exemplo, é implementar manual. Vale ler o PDF e construir com `criar-design-system` usando o manual como fonte. |

> **A régua:** a base certa é aquela em que a pessoa reconhece o **negócio dela**, não a cor favorita
> dela. Cor a gente troca em cinco minutos. Densidade, temperatura e papel da cor, não.

Se a dúvida aparecer no meio do caminho, diga em uma linha e ofereça a troca — mudar de base na
Rodada 2 custa barato; descobrir na Rodada 5 que a base estava errada custa a rodada inteira.

---

## O que se preserva e o que se troca

Esta tabela é o método inteiro. Leia antes de tocar em qualquer arquivo.

| Camada | O que é | Decisão |
|---|---|---|
| Inventário de tokens (quais grupos existem e como se chamam) | estrutura | **PRESERVA** |
| Escala tipográfica (os degraus e as proporções entre eles) | estrutura | **PRESERVA** |
| Escala de espaço (a base de 4px e os múltiplos) | estrutura | **PRESERVA** |
| Escala de raio (a **proporção** entre chip, botão, card e bloco) | estrutura | **PRESERVA** — dá pra reescalar tudo junto, nunca item a item |
| Modelo de elevação (sombra difusa, borda, ou glow — escolha um) | estrutura | **PRESERVA** |
| Regras de componente e de estado (foco visível, disabled, hover, erro com texto) | estrutura | **PRESERVA** |
| Regras de acessibilidade e os pisos de contraste | estrutura | **PRESERVA** |
| A seção de voz | estrutura | **PRESERVA a tabela falar / não falar; TROCA os pares** pelos do negócio |
| Nome, wordmark, título dos arquivos, **prefixo de classe** | identidade | **TROCA** |
| Cor de assinatura e a rampa de 5 tons derivada dela | identidade | **TROCA** |
| Neutros e superfícies | identidade | **RECALIBRA** — a temperatura do neutro acompanha a da assinatura |
| Exemplos de conteúdo (produtos, métricas, nomes, textos do showcase) | identidade | **TROCA** — é o que faz o sistema parecer do negócio |
| As assinaturas visuais (o disco no "O", o fio-prumo, o orbe) | identidade | **TROCA ou readapta** — a receita fica, o motivo muda |
| Faces tipográficas | fronteira | Só troca se houver **motivo de marca**. Trocar por gosto quebra a escala junto. |

> **A armadilha:** trocar só as cores. Fica um sistema com a cara certa e o texto errado — preço de
> hambúrguer numa clínica, "fechamento contábil" numa marca de estética. Exemplo é identidade,
> não enfeite: se o showcase mostra o negócio de outra pessoa, ninguém acredita que o sistema é seu.

---

## Regras de condução

1. **Máximo 4 perguntas por rodada.** Questionário longo faz a pessoa desistir na terceira.
2. **Use `AskUserQuestion` com opções prontas.** Escolher é mais fácil que redigir. Sem a ferramenta,
   faça perguntas numeradas com alternativas em texto.
3. **Toda pergunta vem com default explícito:** *"se você não souber, eu assumo X."*
4. **"Não sei" nunca trava o fluxo.** Registre `[SUPOSIÇÃO]`, assuma o default e siga. No fim da
   Rodada 2 mostre a tabela do que foi assumido, para corrigir em uma mensagem só.
5. **Nunca pergunte o que você consegue descobrir sozinho.** Se existe logo, site, Instagram, PDF ou
   print, abra antes e traga como fato: *"o roxo do seu logo é `#6D28D9` — é essa a cor da marca?"*
6. **Nunca pergunte "o que você quer mudar?"** Quem sabe responder isso não precisa desta skill.
   Você **propõe** o plano de mudança e a pessoa aprova, ajusta ou recusa item a item.
7. **Quem roda comando é você.** Extração de cor, screenshot, grep, instalação — tudo do seu lado.
   A pessoa manda arquivo e aprova resultado; ela não abre terminal.
8. **Escreva em pt-BR.** Nomes de token em inglês (`--bg-card`, `--fg-muted`); documentação e conversa
   em português.

---

## RODADA 0 — QUAL BASE

**Varra antes de perguntar.** É o mesmo comando de detecção documentado na `criar-design-system`
(seção *A convenção de detecção*) — mesma convenção de sinal duplo, mesmas três cautelas
(`find` em vez de glob, `head -20` para não dar falso positivo em arquivo que só **documenta** o
campo, e `name` do frontmatter em vez do nome da pasta). A única diferença é acrescentar **a pasta
aberta agora** aos caminhos, porque as bases de exemplo costumam estar ali — dentro do material que a
pessoa acabou de baixar — antes de qualquer instalação. Nunca presuma onde o material foi
descompactado: cada máquina põe num lugar. Procure onde a pessoa está.

```bash
find ~/.claude/skills ./.claude/skills . -maxdepth 3 -name SKILL.md 2>/dev/null | while read -r f; do
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

### Apresente as bases encontradas

Uma opção por base, com **nome · cor de assinatura · uma linha de personalidade**. A cor vai junto
porque é por ela que a pessoa reconhece o sistema sem abrir arquivo nenhum. As cinco do kit:

| Base | Assinatura | Personalidade em uma linha | Prefixo | Serve a |
|---|---|---|---|---|
| `kiln-design` | `#F08519` âmbar de forja | Escuro, frio e denso: mono é estrutura, cantos de 4px, nada de pílula. | `.kl-` | produto técnico, painel, console, dev tool |
| `nogueira-prumo-design` | `#6B2436` vinho | Claro e editorial: serifada de alto contraste, fio de 1px como hierarquia, muito respiro. | `.np-` | consultoria, advocacia, contabilidade, gestão |
| `fervo-design` | `#D92D0B` tomate | A cor é estrutura: blocos inteiros pintados, condensada em caixa alta, preço como elemento gráfico. | `.fv-` | varejo, delivery, comida, loja de esquina |
| `amparo-design` | `#406D5D` verde-sálvia | Claro e calmo: tudo em pílula, sombra tingida, peso 500 no título, exclamação não existe. | `.amp-` | clínica, terapia, nutrição, cuidado |
| `cotejo-design` | `#2E6DA4` azul-aço | Denso e bitemático: número sempre mono e tabular, raio ≤6px, cor é ação e nunca resultado. | `.ctj-` | dados, finanças, relatório, operação |

Ofereça sempre uma saída extra: **"nenhuma dessas se parece com o meu negócio"** — e aí a resposta
certa é `criar-design-system`, não forçar a menos pior. Diga isso sem rodeio.

**Se a pessoa já disser a base no primeiro pedido** ("quero o Amparo com a minha marca"), pule a
pergunta e confirme em uma linha o que ela vai herdar: *"o Amparo é claro, arredondado e calmo, e o
número dele nunca grita. Cabe no seu negócio?"*

### Se a varredura não achar nada

Não invente uma base. Diga onde conseguir, em duas linhas:

- o kit de exemplos do curso vive em `09-kit-design-systems/` — se a pasta existir na máquina, basta
  apontá-la; se não existir, a pessoa precisa baixar o kit;
- qualquer design system que siga a convenção (`type: design-system` + `ds-tokens` no frontmatter,
  arquivo de tokens na raiz) serve como base, inclusive um DS que ela já tenha de outro projeto.

Sem base nenhuma, ofereça o caminho da irmã: **`criar-design-system` constrói do zero, propondo as
direções visuais em vez de perguntar por elas.** Não tente virar a irmã aqui dentro.

---

## RODADA 1 — A MARCA

Duas coisas nesta rodada: **quem é a marca** e **o material visual dela**. As duas em uma tacada só,
respeitando o teto de 4 perguntas.

### As 4 perguntas (`AskUserQuestion`, todas com default)

**1. Qual é o nome, e como ele se escreve?**
Peça a grafia exata: caixa, acento, espaço, ponto. `Fervo`, `FERVO`, `fervo.` são três marcas
diferentes na tela.
→ Default: caixa de título, como a pessoa digitou.

**2. O que o negócio faz e vende — em uma frase?**
A frase, não a categoria. *"Clínica"* não serve; *"clínica de nutrição e psicologia que atende
adulto que já tentou de tudo"* serve. É daqui que saem os exemplos do showcase.
→ Default se travar: ofereça 3 leituras a partir do nome e do material, e deixe apontar.

**3. O que a marca NÃO é?** (múltipla escolha + campo livre)
`não é barata` · `não é corporativa/engravatada` · `não é infantil` · `não é hypada/startupeira` ·
`não é artesanal/fofa` · `não é técnica demais` · `não é agressiva/vendedora`
→ Default: `não é corporativa` + `não é hypada`.
> Anti-posicionamento é mais fácil de nomear que posicionamento e recorta o ajuste de tom com muito
> mais precisão. Cada "não é" vira restrição na Rodada 2 — inclusive sobre a cor extraída.

**4. Me mostra a marca** — a pergunta que mais muda a qualidade. Detalhada abaixo.

### O pedido de material — o logo vem primeiro

O logo não é enfeite: é **a fonte mais confiável da cor real da marca**. Site tem CSS de tema, print
tem compressão, memória tem viés. O arquivo do logo tem o valor que o designer escolheu.

Peça exatamente assim, nesta ordem:

> Me manda a marca, na melhor coisa que você tiver à mão — **basta arrastar o arquivo aqui pra dentro
> da conversa**:
>
> 1. **O logo** — PNG, JPG ou, melhor de todos, **SVG** (no SVG a cor é exata, não estimada).
> 2. **PDF do manual de marca**, se existir — normalmente já traz os hexes e as fontes escritos.
>    Se você tiver esse, é o único que eu preciso.
> 3. **Print do site ou do Instagram** — serve bem, e mostra a marca aplicada.
> 4. **Foto do cartão, da fachada, da embalagem, do uniforme** — foto de celular resolve.
> 5. **O endereço do site** — eu abro e leio a paleta declarada no CSS.
>
> Se não tiver nada, eu sigo pela descrição — mas aí a cor sou eu que escolho, e marco como suposição.

**Se vier PDF de manual, ele manda no resto.** Diga isso na hora: *"com o manual em mãos eu não vou
adivinhar nada — vou usar o que está escrito nele."*

Sem material nenhum, registre `[SEM MATERIAL VISUAL — cor escolhida pela IA a partir da base]` e siga.

### Se a pessoa responder "não sei" em tudo

O fluxo não trava. Ele encolhe:

1. **Nome** é o único item sem default possível — se faltar, pergunte só ele, sozinho.
2. **O que faz** vem do material, se houver; do contrário, dos arquétipos que a base atende.
3. **O que não é** vira o default (`não é corporativa` + `não é hypada`).
4. **Cor** vem do material; sem material, mantenha a **rampa da base** e diga isso com todas as
   letras: *"sem logo, a cor continua a do exemplo — quando você tiver o arquivo, eu troco em cinco
   minutos."* Inventar um roxo aleatório é pior que herdar uma cor que ao menos está calibrada.

Marque **cada** item assumido com `[SUPOSIÇÃO]` e mostre todos juntos na tabela do fim da Rodada 2.
Suposição visível vira pergunta; suposição escondida vira retrabalho.

---

## RODADA 2 — EXTRAÇÃO E PROPOSTA

### 2.1 Extraia de verdade — não olhe por cima

Cada tipo de material tem um caminho próprio. Use o da linha certa; olho não acerta hex.

| Material | Caminho | Confiabilidade |
|---|---|---|
| **PDF de manual de marca** | Leia o PDF com o `Read` (parâmetro `pages`). Procure "cores", "paleta", "aplicação", "tipografia" — os hexes e as fontes costumam estar escritos. | **Máxima.** Se vier um, ele manda no resto. |
| **SVG** | Leia o arquivo **como texto** e colete os valores de `fill` e `stroke`. Nada de estimar. | **Exata.** |
| **Logo ou print (PNG/JPG)** | `Read` na imagem para julgar a identidade **e** extração por código para os hexes (abaixo). Os dois — a leitura sem o código erra o valor; o código sem a leitura não sabe qual cor é a marca. | Alta. |
| **Site** | Busque a paleta declarada no CSS: variáveis, `theme`, `tailwind.config`. | Alta, com ressalva: tema de site nem sempre é a marca. |
| **Foto de fachada/cartão/embalagem** | Mesma extração da imagem, com um alerta: iluminação desloca o tom. Trate o resultado como **aproximação** e confirme. | Média. |

**SVG — o caminho exato:**

```bash
grep -oiE '(fill|stroke)[:=]"?#[0-9a-f]{3,8}' logo.svg | grep -oiE '#[0-9a-f]{3,8}' | sort | uniq -c | sort -rn
```

**Imagem — extração por código.** Um script curto que reduz a imagem, agrupa tons quase iguais
(antialias e JPEG criam centenas de variações do mesmo vermelho), descarta branco, preto,
transparência e cinza puro, e devolve o hex **exato** mais frequente de cada grupo:

```python
# cores.py — uso: uv run --with pillow python3 cores.py <imagem> [quantas]
import sys, colorsys
from collections import Counter
from PIL import Image

caminho = sys.argv[1]
quantas = int(sys.argv[2]) if len(sys.argv) > 2 else 6

im = Image.open(caminho).convert("RGBA")
im.thumbnail((240, 240))                    # baixa o custo e funde ruído de compressão

exatas, grupos = Counter(), Counter()
for n, (r, g, b, a) in im.getcolors(maxcolors=10**6):
    if a < 128:                             # transparente não é cor da marca
        continue
    h, l, s = colorsys.rgb_to_hls(r/255, g/255, b/255)
    if l > .93 or l < .07 or s < .12:       # branco, preto e cinza puro: não são assinatura
        continue
    chave = (r//10, g//10, b//10)           # agrupa tons quase iguais (antialias, JPEG)
    grupos[chave] += n
    exatas[(chave, (r, g, b))] += n

total = sum(grupos.values()) or 1
for chave, n in grupos.most_common(quantas):
    r, g, b = max(((c, q) for (k, c), q in exatas.items() if k == chave), key=lambda t: t[1])[0]
    h, l, s = colorsys.rgb_to_hls(r/255, g/255, b/255)
    print(f"#{r:02x}{g:02x}{b:02x}  {n/total*100:5.1f}% da área colorida | "
          f"matiz {h*360:5.1f}° · saturação {s*100:3.0f}% · luminância {l*100:3.0f}%")
```

**Como rodar, em ordem de preferência** — o objetivo é não instalar nada permanente na máquina:

```bash
uv run --with pillow --quiet python3 cores.py logo.png 6     # 1ª opção: ambiente efêmero, não suja nada
python3 -m pip install --user pillow && python3 cores.py logo.png 6   # 2ª: se não houver uv
magick logo.png -resize 240x240 -colors 8 -format %c histogram:info: | sort -rn | head -8   # 3ª: ImageMagick
```

> **Ressalva das duas últimas:** o `pip install` deixa pacote instalado — avise antes. O ImageMagick
> **não** filtra branco, preto nem cinza: descarte na mão as linhas quase-brancas e quase-pretas antes
> de olhar o resultado, e trate o hex como aproximado (a quantização desloca em 1 ou 2 pontos).

Nenhum dos três disponível: leia a imagem com o `Read`, proponha o hex mais próximo que você
reconhecer, **diga que foi estimado a olho** e peça confirmação. Não apresente estimativa como medida.

### 2.2 Mostre as cores — não liste

Devolver `#7C3AED · #F59E0B · #10B981` em texto obriga a pessoa a imaginar. Gere um HTML de uma tela
com as amostras, tire screenshot e **mostre a imagem**:

```bash
cat > /tmp/cores.html <<'HTML'
<!DOCTYPE html><html><head><meta charset="utf-8"><style>
body{margin:0;font:14px -apple-system,system-ui,sans-serif;background:#fff;color:#111}
.linha{display:flex} .col{flex:1} .amostra{height:110px}
.rot{padding:10px 12px;font-family:ui-monospace,Menlo,monospace;font-size:13px}
.par{display:flex;margin-top:2px} .par div{flex:1;padding:14px 12px;font-weight:600}
</style></head><body>
<div class="linha">
  <div class="col"><div class="amostra" style="background:#COR1"></div><div class="rot">#COR1 · 70% · extraída do logo</div></div>
  <div class="col"><div class="amostra" style="background:#COR2"></div><div class="rot">#COR2 · ajustada p/ texto</div></div>
</div>
<div class="par">
  <div style="background:#COR1;color:#fff">Texto branco sobre a cor — X:1</div>
  <div style="background:#FUNDO;color:#COR2">Texto da cor sobre o fundo — Y:1</div>
</div>
</body></html>
HTML
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --hide-scrollbars --screenshot="/tmp/cores.png" --window-size=900,220 "file:///tmp/cores.html"
```

Depois **leia o PNG** e mostre. Ao lado da imagem, uma linha por cor: hex · de onde veio · quanto
ocupa. E então a pergunta fechada: **"qual dessas é a cor de assinatura?"** — com as candidatas como
opções prontas e a mais frequente como default.

### 2.3 Cor extraída nem sempre é cor de interface

Uma cor pode ser ótima em vinil e péssima em tela. Quando isso acontecer, **proponha o ajuste,
explique em uma linha por quê, e mostre a original ao lado da ajustada** — nunca troque em silêncio.

| Defeito | Como se manifesta | Ajuste |
|---|---|---|
| Saturada demais | Vibra na borda, cansa em bloco grande, "estoura" ao lado do branco | Baixe 10–20% de saturação; mantenha o matiz |
| Clara demais | Some no fundo claro, não passa contraste em texto nem em botão | Escureça 2 passos e crie `--primary-on-light` |
| Escura demais | Vira quase-preto no tema escuro e some do sistema | Clareie para o tema escuro; a assinatura precisa existir nos dois |
| Matiz colidindo com estado | O vermelho da marca é o mesmo do erro; o verde é o mesmo do sucesso | Afaste o estado em ~30° de matiz e **sempre** acompanhe cor de ícone e texto |
| Sem contraste com os neutros da base | A cor "some" nos cards | Recalibre os neutros (temperatura), não a assinatura |

### 2.4 Contraste é checagem obrigatória

Ao trocar a assinatura, **verifique os dois sentidos**: o texto continua legível **sobre** ela, e ela
continua legível **sobre** os fundos do sistema. Calcule, não estime — as bases já vêm calibradas e é
justamente a troca de cor que quebra a calibragem.

**Mínimos aceitáveis (WCAG AA):** `4.5:1` texto normal · `3:1` texto ≥24px ou negrito ≥18.66px ·
`3:1` borda, ícone e anel de foco.

```python
# contraste.py — uso: python3 contraste.py "#fff/#d92d0b" "#b32209/#fff6f1"   (sem dependência)
import sys
def lin(c):
    c /= 255
    return c/12.92 if c <= .03928 else ((c+.055)/1.055)**2.4
def L(h):
    h = h.lstrip('#')
    if len(h) == 3: h = ''.join(c*2 for c in h)
    r, g, b = (int(h[i:i+2], 16) for i in (0, 2, 4))
    return .2126*lin(r) + .7152*lin(g) + .0722*lin(b)
for par in sys.argv[1:]:
    fg, bg = par.split('/')
    a, b = L(fg), L(bg)
    r = (max(a, b)+.05) / (min(a, b)+.05)
    print(f"{fg} sobre {bg} = {r:.2f}:1  ["
          f"texto normal {'PASSA' if r>=4.5 else 'REPROVA'} · "
          f"texto grande {'PASSA' if r>=3 else 'REPROVA'} · "
          f"borda/ícone {'PASSA' if r>=3 else 'REPROVA'}]")
```

**Os pares que você é obrigado a testar**, no mínimo: texto sobre a assinatura · assinatura sobre a
base clara · assinatura sobre a base escura · texto muted sobre card · anel de foco sobre a base ·
cada semântica sobre a lavagem dela.

Se quebrar: **ajuste o tom e avise o que fez**, em uma linha — *"o `#22C55E` do seu logo dá 1,9:1 em
texto sobre branco, então em texto eu uso `#15803D` (5,1:1) e mantenho o original para fundo."*
O truque padrão é o token dedicado `--primary-on-light`, que as bases já têm — preserve o mecanismo e
troque só o valor.

### 2.5 Proponha o plano de mudança

Nunca pergunte "o que você quer mudar?". **Apresente o plano** — o que troca, o que preserva, e por
quê — e deixe a pessoa aprovar item a item com `AskUserQuestion`.

Formato: uma tabela curta, com o item, o valor de origem, o valor proposto e a justificativa em uma
frase.

| # | Item | Da base | Proposto | Por quê |
|---|---|---|---|---|
| 1 | Nome e wordmark | Fervo / `FERV`+disco | Bocas / `BOCAS` com o "O" em disco | O motivo gráfico serve ao nome novo sem inventar outro |
| 2 | Assinatura | `#D92D0B` tomate | `#C2410C` telha | Extraída do logo; 10% menos saturada para não vibrar em bloco |
| 3 | Neutros | papel quente `#FFF6F1` | mantém, ajustado ao novo matiz | Temperatura tem que acompanhar a assinatura |
| 4 | Exemplos | hambúrguer, porção | café, grão, assinatura mensal | Showcase com o produto de outro negócio não convence |
| 5 | Voz | "Fome não espera carregar" | reescrita nos mesmos moldes | A tabela falar/não falar fica; os pares mudam |
| — | **Preservado** | escalas, raios, elevação, estados, acessibilidade | — | É o que já está calibrado — mexer aqui é refazer, não personalizar |

Ofereça três saídas por item: **aprovar · ajustar · não fazer**. Agrupe os itens óbvios numa pergunta
só e reserve as perguntas individuais para os que têm risco (cor de assinatura, troca de face,
mudança de assinatura visual).

**Feche a rodada com a tabela de suposições** — todo `[SUPOSIÇÃO]` da Rodada 1 e 2 junto, em quatro
linhas, com o convite: *"corrige o que estiver errado numa mensagem só; o resto eu já aplico."*

---

## RODADA 3 — APLICAR E VERIFICAR

Sem perguntas. Você já tem tudo. Aplique e mostre.

### 3.1 Copie a base para a pasta nova — e trabalhe já lá dentro

Nada de gerar em pasta temporária para mover depois: duas cópias divergem e a instalada é sempre a
velha. Descubra a pasta de skills desta máquina (Rodada 4 explica por que não se fixa o caminho) e
copie para dentro dela.

```bash
SKILLS=<pasta de skills desta máquina>          # ver Rodada 4
BASE=<caminho da base escolhida>
DS="$SKILLS/<marca-slug>-design"

mkdir -p "$DS" && cp -R "$BASE"/. "$DS"/
rm -rf "$DS/assets"                              # o logo da base NÃO vai junto
ls -la "$DS"
```

> **`assets/` é o resquício que passa despercebido.** O wordmark, o símbolo e o favicon da base são
> a marca de outro negócio. Apague a pasta e recrie só o que existir da marca nova; se não existir
> nada, não recrie — o wordmark tipográfico do showcase resolve.

### 3.2 A ordem de substituição

1. **Rampa de cor** — os 5 tons a partir da assinatura nova, mais `--primary-on-light` e os alfas
   nomeados. Mesmos nomes de token, valores novos.
2. **Neutros e superfícies** — recalibre a temperatura para acompanhar a assinatura. Cinza neutro ao
   lado de cor quente deixa a marca suja.
3. **Nome e wordmark** em todos os arquivos, inclusive comentário de cabeçalho e `<title>`.
4. **Prefixo de classe** — em todos os arquivos, de uma vez (comando abaixo).
5. **Frontmatter** — `name`, `description`, `ds-brand`, `ds-signature`.
6. **Exemplos do showcase e do README** — produtos, métricas, nomes, textos.
7. **Tabela falar / não falar** — mesma estrutura, pares do negócio novo. Mínimo 5.
8. **Assinaturas visuais** — readapte a receita ao nome novo, ou substitua se não couber.

**Renomeação portátil** (`perl -pi` funciona igual em macOS, Linux e git-bash; `sed -i` muda de
sintaxe entre eles e é onde a etapa costuma quebrar):

```bash
cd "$DS"
perl -pi -e 's/\bfv-/bc-/g'      tokens.css showcase.html README.md SKILL.md
perl -pi -e 's/\bFervo\b/Bocas/g; s/\bFERVO\b/BOCAS/g; s/\bFERV\b/BOCAS/g; s/\bfervo\b/bocas/g' \
                                 tokens.css showcase.html README.md SKILL.md
```

> **Quatro substituições, não uma.** O nome aparece em quatro caixas diferentes: título (`Fervo`),
> letreiro (`FERVO`), **wordmark quebrado** (`FERV` + disco) e slug do frontmatter (`fervo-design`).
> Uma substituição só resolve uma delas e deixa as outras três — é o defeito mais comum desta skill.

### 3.3 O grep final — zero resquício

Rode **antes** de mostrar qualquer coisa. Saída vazia é a única saída aceitável.

```bash
RADICAL='ferv'                                    # o RADICAL, não o nome inteiro (pega FERV, Fervo, fervo-design)
PFX='fv-'
HEXES='d92d0b|b32209|8a1907|ff5c33|ff8a66'        # a rampa inteira da base, sem o "#"

grep -rinE "$RADICAL|$PFX|$HEXES" "$DS" | head -40
echo "--- acima precisa estar vazio ---"
```

E a conferência do avesso — a marca nova tem que estar nos quatro arquivos:

```bash
grep -ric '<marca>' "$DS"/tokens.css "$DS"/showcase.html "$DS"/README.md "$DS"/SKILL.md
# nenhum arquivo pode voltar 0
```

Achou resquício, **corrija e rode de novo**. Não passe adiante com "só sobrou um".

### 3.4 Verifique por screenshot — não negociável

Mesma regra e mesmo método da `criar-design-system` (Rodada 3): você tira o screenshot, **você** olha
primeiro, conserta o que reprovar, e só então mostra.

```bash
# desktop — 1440
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --hide-scrollbars --screenshot="/tmp/ds-1440.png" --window-size=1440,3000 "file://$DS/showcase.html"

# mobile — 375 por iframe (o headless tem largura mínima e RECORTA em vez de rediagramar:
# pedir --window-size=375 dá falso positivo de "estourou". A moldura cinza é a prova.)
cat > /tmp/mob.html <<HTML
<!DOCTYPE html><html><head><meta charset="utf-8">
<style>html,body{margin:0;background:#888}
iframe{width:375px;height:2400px;border:0;display:block;margin:0 auto}</style></head>
<body><iframe src="file://$DS/showcase.html"></iframe></body></html>
HTML
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --hide-scrollbars --screenshot="/tmp/ds-375.png" --window-size=520,2400 "file:///tmp/mob.html"
```

Depois **leia os dois PNGs com o `Read`** e passe a régua — a de sempre, mais as três linhas que só
existem quando se personaliza:

| Checagem | Reprova se |
|---|---|
| Token faltando | Bloco preto, branco ou transparente onde deveria ter cor |
| Fonte não carregou | O display renderizou igual ao texto (caiu no fallback) |
| Dominância da assinatura | A cor nova ocupa mais que ~10% da tela |
| Contraste real | Texto muted sobre card fica ilegível na imagem |
| Mobile 375 | Rolagem lateral, tabela ou paleta estourando |
| Tema claro e escuro | Um dos dois ficou sujo, ou o toggle quebrou |
| **Resquício visual** | **Aparece o nome, o wordmark ou uma cor da base em algum canto** |
| **Exemplo órfão** | **O showcase ainda fala do negócio da base** |
| **Cor vibrando** | **A assinatura nova briga com o neutro herdado — recalibre a temperatura** |
| Antipadrão | Bate em qualquer item de `criar-design-system/references/antipadroes.md` |

Reprovou: conserte e tire outro screenshot. Só então mostre.

---

## RODADA 4 — INSTALAR

### Onde ficam as skills pessoais nesta máquina

**Não fixe o caminho literal.** Em macOS e Linux é `~/.claude/skills/`; no Windows a documentação
oficial é ambígua e a instalação varia. **Descubra em vez de assumir** — e o jeito mais confiável é
olhar onde as skills existentes já moram:

```bash
for p in "$CLAUDE_CONFIG_DIR/skills" "$HOME/.claude/skills" "$USERPROFILE/.claude/skills" \
         "$APPDATA/claude/skills"; do
  [ -n "$p" ] && [ -d "$p" ] && { echo "pasta de skills: $p"; break; }
done
```

Se nenhuma existir, a referência é a pasta desta própria skill (`personalizar-design-system/`): a
pasta que a contém **é** a pasta de skills. Se ainda assim não der para determinar, **pergunte** —
uma pergunta é melhor que instalar no lugar errado.

**Ao final, reporte o caminho usado**, literalmente, na última mensagem. É informação de manutenção
e é como quem estiver acompanhando descobre onde a coisa foi parar.

### O frontmatter de convenção — obrigatório

Sem estes campos o DS fica invisível para a varredura e nenhuma outra skill o encontra. O detalhe de
cada campo está em `criar-design-system/references/template-skill.md`.

```yaml
---
name: <marca-slug>-design
description: "Use esta skill para gerar qualquer interface ou artefato da marca <Marca> (<posicionamento curto>) — ..."
user-invocable: true
type: design-system            # marcador da convenção (obrigatório)
ds-tokens: tokens.css          # arquivo de tokens na raiz da skill (obrigatório)
ds-brand: <Marca>
ds-signature: "#RRGGBB"        # entre aspas: # inicia comentário em YAML
---
```

### Confirme que instalou de verdade

```bash
ls -la "$DS"                       # os 4 arquivos
head -10 "$DS/SKILL.md"            # frontmatter com type e ds-tokens
```

E **rode a varredura da Rodada 0 de novo**: se a marca nova não aparecer na lista, ela não está
instalada — não importa que os arquivos existam. Arquivo presente com frontmatter errado é o modo de
falha silencioso desta rodada.

### Aponte o `CLAUDE.md` do projeto

É o passo que faz o DS sobreviver à terceira semana. Acrescente ao `CLAUDE.md` do projeto:

```markdown
## Design system
Este projeto usa o design system **<Marca>** (skill `<marca-slug>-design`).
Antes de escrever qualquer CSS, componente ou tela, leia o `README.md` dessa skill e use
`tokens.css` como fonte da verdade.
Proibido: hex solto no componente, fonte fora das declaradas, cor de destaque que não seja a de
assinatura. Na dúvida sobre um valor, use o token mais próximo — nunca invente um.
```

Se a pessoa quiser o DS versionado junto com o código, instale também em `<projeto>/.claude/skills/`
— mesma estrutura, mesma convenção.

---

## RODADA 5 — APROVAÇÃO VISUAL

A verificação da Rodada 3 é sua: ela pega **defeito**. Esta é da pessoa: ela pega **discordância**.
São coisas diferentes, e é por isso que esta rodada existe e vem **depois** de instalar.

### 1. Abra o showcase no navegador — de verdade

Não mostre o caminho pedindo que ela abra. Quem roda comando é você; ela só aprova. Detecte o sistema
antes:

```bash
case "$(uname -s)" in
  Darwin)      open "$DS/showcase.html" ;;
  Linux)       xdg-open "$DS/showcase.html" >/dev/null 2>&1 & ;;
  MINGW*|MSYS*|CYGWIN*) start "" "$DS/showcase.html" ;;
  *)           cmd.exe /c start "" "$DS/showcase.html" 2>/dev/null || xdg-open "$DS/showcase.html" ;;
esac
```

### 2. Diga o que ela está olhando — três ou quatro linhas

Sem isso a pessoa encara a página inteira sem saber onde reparar. Diga, nesta ordem:

> - **A cor de assinatura é `#C2410C`** — saiu do seu logo (era `#E24A0B`, baixei a saturação para
>   não vibrar em bloco grande).
> - **Mudou:** nome e wordmark, a rampa de cor inteira, os neutros (que agora acompanham a
>   temperatura da sua cor) e todos os exemplos, que agora falam de café e assinatura mensal.
> - **Foi preservado de propósito:** as escalas de tipo e de espaço, os raios, o modelo de sombra e
>   as regras de estado. É a parte que já está calibrada — é o que você está herdando.
> - **Repare especialmente em:** o bloco de cor do topo e o card de produto. É onde a marca aparece.

### 3. Pergunte se tem ajuste — com opções prontas

`AskUserQuestion`. Nunca "o que você achou?": pergunta aberta devolve "ficou legal" e a discordância
só aparece três dias depois. Ofereça as saídas mais prováveis:

`está aprovado` · `a cor não é bem essa` · `a tipografia não combina` · `está pesado / apertado demais` ·
`quero ver no celular` · `outra coisa (me conta o quê)`

A opção **"quero ver no celular"** vale sempre que houver dúvida de leitura: mande o PNG de 375px que
você já tem da Rodada 3, ou tire outro.

### 4. Se houver ajuste, é um laço — não uma pergunta única

Para cada volta: **aplique só o que ela apontou** → reverifique por screenshot (Rodada 3.4) → reabra
no navegador → pergunte de novo. Não redesenhe o resto por conta própria: ajuste pedido é ajuste
pedido, e "aproveitei e melhorei aqui também" é como se perde a confiança de quem já tinha aprovado
o resto.

Só se sai do laço com a aprovação explícita.

> **A régua dos três laços.** Um ajuste que a pessoa **pede** é ajuste. Uma direção nova que ela
> **descobre que queria** é outra skill. Se no terceiro laço ainda não houve aprovação, pare e diga
> isso a ela: provavelmente a base escolhida estava errada desde o começo, e o caminho é trocar de
> base (Rodada 0) ou construir do zero com `criar-design-system`. Continuar iterando cor por cor
> gasta a paciência dela e não conserta uma direção que não era a dela.

### 5. Aprovou: propague para os arquivos instalados

**É aqui que mais dá errado.** A pessoa aprova a versão que está na pasta de trabalho enquanto a skill
instalada continua com a versão anterior — e o DS que todo projeto futuro vai ler é a versão errada.

Depois do "aprovado": reinstale ou sincronize, e **confirme** que os quatro arquivos instalados batem
com os aprovados.

```bash
# se trabalhou fora da pasta instalada, sincronize e confira
cp -R <pasta de trabalho>/. "$DS"/
for f in SKILL.md README.md tokens.css showcase.html; do
  cmp -s "<pasta de trabalho>/$f" "$DS/$f" && echo "ok   $f" || echo "DIVERGE  $f"
done
```

Trabalhou direto na pasta instalada (o recomendado, Rodada 3.1)? Ainda assim confirme os quatro
arquivos e rode a varredura uma última vez. Conferência barata evita a descoberta cara.

### 6. Feche dizendo o que ela tem agora

Três linhas, sem rodeio:

> - **Skill instalada:** `<marca-slug>-design`
> - **Caminho:** `<caminho absoluto>`
> - **Como usar em outro projeto:** peça "usa o design system `<marca-slug>-design`" no começo da
>   conversa, ou cole o bloco de `CLAUDE.md` da Rodada 4 no projeto — aí toda sessão futura já nasce
>   com a identidade certa.

E o antes e depois: o pedido de uma linha que ela escreveu, ao lado da árvore dos quatro arquivos.

---

## Modo aula

Se a pessoa disser que está **gravando, ensinando ou fazendo demo**, mude a condução:

1. **Abra pela comparação com a irmã.** *"A `criar-design-system` leva 40 minutos porque a gente
   decide a direção junto. Aqui a direção já veio pronta — o trabalho é outro: descobrir a marca e
   transplantar. Dá pra fazer em 15."*
2. **Mostre a tabela preserva/troca antes de qualquer arquivo.** É a aula inteira em uma tela. A
   pergunta que ela responde — *o que numa marca é estrutura e o que é identidade?* — é o conceito
   que a pessoa leva pra vida, mesmo sem nunca mais abrir a skill.
3. **Faça a extração de cor ao vivo, e erre de propósito primeiro.** Olhe o logo, chute o hex, rode o
   script e mostre a diferença. *"Eu disse `#D63A1F`; a medida é `#C2410C`. Olho não acerta hex — e
   um hex errado contamina a rampa inteira."*
4. **Mostre o grep final falhando.** Rode com uma substituição só, deixe aparecer `FERV` do wordmark,
   e nomeie: *"quatro caixas, quatro substituições."* Um defeito visto vale dez avisos.
5. **Abra o showcase na tela.** O momento em que o sistema aparece com a marca certa é o clímax —
   não pule para a descrição em texto.
6. **Encene a Rodada 5.** Peça um ajuste de mentira ("essa cor tá clara demais"), aplique, reverifique
   e reabra. É o que ensina que verificação de agente e aprovação de pessoa são coisas distintas.
7. **Lição de casa:** *"escolhe a base que mais parece o seu negócio, roda a skill e me manda o
   showcase"* — entregável visual corrige turma inteira em um scroll.

**Ritmo para ~20min:** Rodada 0 (2min) · Rodada 1 (4min) · Rodada 2 (7min, com o erro proposital na
extração) · Rodada 3 (4min, incluindo o grep) · Rodadas 4 e 5 (3min).

---

## Régua de pronto — só está entregue quando

- [ ] A base foi **escolhida pelo negócio**, não pela cor favorita.
- [ ] A cor de assinatura veio de **material real** — ou está marcada `[SUPOSIÇÃO]`, explicitamente.
- [ ] Os hexes extraídos foram **mostrados** (amostra visual), não só listados.
- [ ] Todo par texto/fundo declarado passa AA (4,5:1 texto normal; 3:1 texto grande, borda e foco).
- [ ] O plano de mudança foi **proposto e aprovado item a item** — nunca "o que você quer mudar?".
- [ ] O grep de resquício volta **vazio**: nome (pelo radical), prefixo de classe e rampa da base.
- [ ] `assets/` da base foi apagada; nada do wordmark antigo sobrou.
- [ ] Os exemplos do showcase e do README falam do **negócio novo**.
- [ ] A tabela falar / não falar tem pelo menos 5 pares, do negócio novo.
- [ ] O showcase foi **verificado por screenshot** em 1440 e 375, e os defeitos corrigidos antes de mostrar.
- [ ] A skill está instalada com `type: design-system` e `ds-tokens`, e **aparece na varredura**.
- [ ] A pessoa **viu no navegador e aprovou** (Rodada 5), e os arquivos instalados são os aprovados.
- [ ] O caminho de instalação usado foi **reportado** na mensagem final.

---

## Arquivos de apoio

Esta skill **não duplica** o material da irmã — ela aponta. Leia direto de
`~/.claude/skills/criar-design-system/`:

| Arquivo da irmã | Quando ler aqui |
|---|---|
| `SKILL.md` → *A convenção de detecção* | Rodada 0 — o comando de varredura e as três cautelas dele |
| `SKILL.md` → *Rodada 3* | Rodada 3.4 — o método de screenshot e a armadilha medida dos 375px |
| `SKILL.md` → *Adotar o DS num projeto que já existe* | Depois da Rodada 5, se houver código rodando para converter |
| `references/anatomia-de-tokens.md` | Rodada 3.2 — o que cada grupo de token faz antes de mexer no valor |
| `references/antipadroes.md` | Fim da Rodada 3 — a cor nova pode ter empurrado o sistema para um clichê |
| `references/template-skill.md` | Rodada 4 — os campos de convenção do frontmatter, um a um |
| `references/direcoes-visuais.md` | Rodada 0 — se houver dúvida sobre qual base combina com o arquétipo do negócio |

**Se a irmã não estiver instalada**, esta skill ainda funciona: as tabelas e comandos essenciais estão
aqui. Mas avise em uma linha que a `criar-design-system` é onde vivem os antipadrões e a anatomia
completa dos tokens — e que sem ela a checagem de clichê fica por sua conta.
