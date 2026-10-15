---
name: cotejo-design
description: "Use esta skill para gerar qualquer interface ou artefato da marca Cotejo (plataforma de fechamento contábil e financeiro) — painel, tabela de dados, relatório, e-mail, mock ou protótipo. Contém os tokens de cor, tipo, espaço, raio, elevação e motion nos temas claro e escuro, as regras de voz e os dois componentes-assinatura (tabela com coluna de variação e card de métrica com sparkline). Use sempre que o pedido envolver o Cotejo, ou quando um produto denso de dados, finanças ou operação precisar de identidade visual."
user-invocable: true
type: design-system
ds-tokens: tokens.css
ds-brand: Cotejo
ds-signature: "#2E6DA4"
---

# Cotejo — Design System

Leia o `README.md` desta skill antes de escrever qualquer linha de CSS ou componente.
`tokens.css` é a **fonte da verdade** — nenhum valor visual nasce fora dele.
`showcase.html` mostra o sistema aplicado nos dois temas; abra quando precisar decidir
"como isso deveria parecer".

## Quick reference

- **Assinatura:** azul-aço `#2E6DA4` (`--steel-500`), rampa de 5 passos. É cor de **ação**, nunca
  de resultado. Meta de ocupação: menos de 10% da tela.
- **Temas completos, os dois.** Claro `#F4F6FA` / superfície `#FFFFFF`; escuro `#0A0F1A` /
  superfície `#101827`. Ordem obrigatória: `:root` → `@media (prefers-color-scheme: dark)` →
  `:root[data-theme="dark"]` → `:root[data-theme="light"]`. Todo token do escuro existe no claro.
- **Faces:** sans e mono **nativas do sistema**. Zero webfont, zero CDN — a rede do cliente cai e o
  número precisa aparecer mesmo assim.
- **Número é cidadão de primeira classe:** sempre mono, sempre `tabular-nums`, sempre alinhado à
  direita, negativo contábil entre parênteses. Classe pronta: `.ctj-num`.
- **Alta é jade `#0E6F53` / `#3FB98A`; baixa é tijolo `#A03027` / `#E0705F`** — separadas da marca.
  Em custo, despesa e inadimplência use `.ctj-delta--inverse`: direção honesta, cor trocada.
- **Densidade alta:** linha de dado de 34px, hairline de 1px, raio entre 3 e 6px (`full` só em
  avatar). Botão de 32px. Nada de canto grande em superfície que carrega número.
- **Elevação por tema:** sombra difusa no claro; borda mais clara (+ `0 0 0 1px` branco a 3%) no
  escuro. Foco sempre visível com `--ring`.
- **Voz:** pt-BR, o produto fala de si na 3ª pessoa e trata o usuário por "você". Ponto final em
  tudo. **Sem emoji, sem exclamação, sem "ops".** Número nunca sai sem unidade e sem período.

## Como usar

**Em produção:** importe `tokens.css` no entrypoint e aponte o Tailwind ou o CSS para as
variáveis. Nunca escreva hex direto no componente.

**Em artefato descartável** (mock, slide, protótipo, e-mail): copie os blocos de variáveis do
`tokens.css` para dentro do `<style>` do HTML e use as classes `.ctj-*`. Arquivo único, abre com
duplo clique, sem rede.

**Se o usuário invocar sem contexto:** pergunte o que vai construir, no máximo quatro perguntas
com opções prontas, e entregue como especialista da marca — HTML pronto ou código de produção,
conforme o caso.

## Proibido

- Hex, `rgb()` ou nome de cor solto em componente — só `var(--token)`.
- Fonte fora das duas pilhas declaradas. Nada de `@import` de Google Fonts.
- Azul-aço significando "subiu" ou "deu certo".
- Verde em despesa que aumentou (use `.ctj-delta--inverse`).
- Número em face proporcional, em qualquer lugar, inclusive tooltip e e-mail.
- Raio acima de 6px em superfície que carrega dado.
- Emoji, gradiente decorativo, ilustração ou trilho de acento colorido na lateral de card.
- Inventar valor de espaço ou raio fora da escala.

## Arquivos

| Arquivo | O que é |
|---|---|
| `README.md` | O manual: marca, voz (falar / não falar), paleta em tabela, tipografia, componentes, assinaturas, ressalvas |
| `tokens.css` | Fonte da verdade — variáveis dos dois temas e classes `.ctj-*` |
| `showcase.html` | A prova visual, standalone, com alternador de tema funcionando |
