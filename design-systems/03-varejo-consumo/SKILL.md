---
name: fervo-design
description: "Use esta skill para gerar qualquer interface ou artefato da marca Fervo (comida de rua, delivery e loja de esquina) — app de pedido, cardápio, landing, embalagem, story, e-mail promocional, mock ou protótipo. Contém os tokens de cor, tipo, espaço, raio, elevação e motion, as regras de voz (falar / não falar) e as assinaturas visuais. Use sempre que o pedido envolver a Fervo, ou quando um projeto de varejo, delivery ou comida e bebida precisar herdar esta identidade."
user-invocable: true
type: design-system
ds-tokens: tokens.css
ds-brand: Fervo
ds-signature: "#D92D0B"
---

# Fervo — Design System

Leia o `README.md` desta skill antes de escrever qualquer linha de CSS ou componente —
ele tem a paleta comentada, as regras de tipografia, o comportamento de cada estado e a
seção de voz.

`tokens.css` é a **fonte da verdade**: nenhum valor visual nasce fora dele.
`showcase.html` é a prova visual (standalone, offline) — abra quando precisar decidir
"como isso deveria parecer".

## Quick reference

- **Assinatura:** tomate `#d92d0b` (`--primary-500`). É cor de **fundo**. Em texto e link
  use `#b32209` (`--primary-on-light`) — o `-500` só dá 4,4:1 sobre papel e reprova.
- **A cor é estrutura:** bloco inteiro pintado (hero, faixa, chamada de combo). Marca com
  filete colorido some da calçada. Base clara e quente `#fff6f1`; tinta quente `#241512`.
- **Faces:** display em condensada nativa (`'Arial Narrow'` → `'Liberation Sans Narrow'` →
  `'Roboto Condensed'`), caixa alta, `letter-spacing: -0.035em`, `line-height: 0.92`.
  Texto na sans nativa do sistema, caixa de frase, tracking 0, `line-height: 1.6`.
  Nunca condensada em parágrafo.
- **Preço é elemento gráfico:** `R$` a `0.34em` no topo, inteiro em condensada 900,
  centavos a `0.4em` elevados, `tabular-nums`. Preço antigo riscado **acima** do novo.
- **Componente-assinatura:** `.fv-produto` — card com `--radius-asym` (32px 8px 32px 8px),
  selo circular girado `-8deg` no canto e preço em destaque no rodapé. Hover = borda tomate
  + `--shadow-pop` (sombra tingida) + `translateY(-4px)`.
- **Raio proporcional:** chip 8 · botão/input 14 · card 22 · bloco 32 · selo e badge full.
  O canto assimétrico é raro de propósito: só card de produto e hero.
- **Um botão de comprar por tela.** Tomate cheio é exclusividade de "Adicionar" e
  "Finalizar pedido". Secundárias (mostarda, limão, uva) servem categoria e ilustração —
  nunca botão. Erro é carmim `#a11043`, nunca o tomate da marca, e sempre com texto.
- **Voz:** pt-BR, "você", frase curta com verbo na frente, ponto final sempre. Preço por
  extenso com centavos. Zero emoji, zero "imperdível", zero contagem regressiva.

## Como usar

**Em produção:** importe `tokens.css` no entrypoint e aponte o Tailwind/CSS para as
variáveis. Nunca escreva hex direto no componente.

**Em artefato descartável** (slide, mock, protótipo, post): copie o bloco `:root` do
`tokens.css` para dentro do `<style>` do HTML e use as classes `.fv-*`. Arquivo único,
abre com duplo clique, offline.

**Se o usuário invocar sem contexto:** pergunte o que vai construir — no máximo 4 perguntas
com opções prontas — e entregue como especialista da marca.

## Proibido

- Hex, `rgb()` ou nome de cor solto em componente — só `var(--token)`.
- Fonte fora das duas declaradas, e nenhuma webfont por CDN (o DS abre offline).
- Cor secundária em botão, CTA, link ou anel de foco.
- `--primary-500` em texto pequeno; `--fg-on-primary-soft` em corpo sobre tomate.
- `--radius-asym` fora de card de produto e hero.
- Contagem regressiva piscando, emoji, banco de imagem genérico, lorem ipsum.
- Valor de espaço ou raio inventado fora da escala.

## Arquivos

| Arquivo | O que é |
|---|---|
| `README.md` | O manual: marca, paleta comentada, tipografia, componentes e estados, voz, iconografia, ressalvas |
| `tokens.css` | Fonte da verdade — variáveis e classes utilitárias `.fv-*` |
| `showcase.html` | A prova visual, standalone e sem dependência externa |
