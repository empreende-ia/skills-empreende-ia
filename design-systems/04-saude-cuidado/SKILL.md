---
name: amparo-design
description: "Use esta skill para gerar qualquer interface ou artefato da marca Amparo (clínica integrada — nutrição, psicologia e fisioterapia) — produção, protótipo, landing, área do paciente, lembrete de consulta, laudo, ficha, slide, e-mail. Contém os tokens de cor, tipo, espaço, raio, elevação e motion, as regras de voz (falar / não falar) e as assinaturas visuais. Use sempre que o pedido envolver a Amparo, ou quando um projeto de clínica, consultório, nutrição, terapia ou coaching de saúde precisar de identidade visual acolhedora e competente."
user-invocable: true
type: design-system
ds-tokens: tokens.css
ds-brand: Amparo
ds-signature: "#406D5D"
---

# Amparo — Design System

Leia o `README.md` desta skill **antes** de escrever qualquer linha de CSS ou componente — ele traz a
voz, as regras de estado e as receitas das assinaturas.
`tokens.css` é a **fonte da verdade**: nenhum valor visual nasce fora dele.
`showcase.html` mostra o sistema aplicado; abra quando precisar decidir "como isso deveria parecer".

## Quick reference

- **Assinatura:** `#406D5D`, verde-sálvia profundo e dessaturado. Base off-white **frio** `#F0F4F3`,
  card `#F9FBFA`, elevado `#FFFFFF`. Secundária azul-névoa `#445F74`. Nunca bege, nunca creme.
- **Faces:** pilha 100% nativa, zero webfont — `"Avenir Next", Avenir, "Segoe UI", system-ui` no texto
  e no display; `ui-monospace, "SF Mono", Menlo` em horário, dose e código, sempre `tabular-nums`.
- **Peso:** título em **500**. 600 em botão e label. **700 só em número. 800 nunca** — a marca não grita.
- **Tracking:** `-0.025em` no display, `-0.012em` no heading, 0 no corpo, `+0.16em` no overline em
  caixa alta. Entrelinha do corpo em **1.7**, medida de 65 caracteres.
- **Forma:** botão é **pílula** (`--radius-full`); input 14px, card 20px, destaque 24px, painel 28px.
  Nenhum canto reto em lugar nenhum.
- **Elevação:** sombra difusa **tingida de tinta** (`rgba(31,46,41,…)`), nunca preta e nunca glow.
  Foco de campo usa `--halo` (anel de sálvia a 8%); foco de teclado usa `--ring` (a 28%).
- **Componente-assinatura:** card de informação com **orbe** — círculo sólido de 56px em
  `--primary-wash` `#E3EEEA`, ícone de linha de 24px em `--primary-500`. Sem borda, sem gradiente,
  sem quadrado arredondado. Mais o **arco** do wordmark e o **cartão de horário** com hora em mono.
- **Voz:** pt-BR, "a gente" para a clínica e "você" para o paciente. Frase termina em ponto —
  **exclamação não existe**. Emoji: não. Prazo e preço sempre em número, nunca em adjetivo.

## Como usar

**Em produção:** importe `tokens.css` no entrypoint e aponte o Tailwind/CSS para as variáveis.
Nunca escreva hex direto no componente.

**Em artefato descartável** (landing, mock, slide, e-mail): copie o bloco `:root` inteiro do
`tokens.css` para dentro do `<style>` e use as classes `.amp-*`. Arquivo único, abre com duplo clique,
funciona offline — a pilha de fontes é nativa justamente para isso.

**Se o usuário invocar sem contexto:** pergunte o que vai construir, no máximo 4 perguntas com opções
prontas, e entregue como especialista da marca — HTML pronto ou código de produção, conforme o caso.

## Proibido

- Hex, rgb ou nome de cor solto em componente — só `var(--token)`.
- Fonte fora das duas pilhas declaradas. Nenhum `@import` de Google Fonts, nenhum `<link>` de CDN.
- Peso 700 ou 800 em título.
- Sálvia como cor de sucesso — sucesso é `#2C6D31`, e é outra coisa.
- Fundo bege ou creme; gradiente em área grande; barra de acento na lateral de card arredondado;
  emoji; exclamação; página inteira centralizada; `border-radius: 8px` em tudo.
- Inventar valor de espaço, raio ou sombra fora da escala.

## Arquivos

| Arquivo | O que é |
|---|---|
| `README.md` | O manual: marca, voz, fundamentos visuais, componentes e estados, assinaturas, ressalvas |
| `tokens.css` | Fonte da verdade — variáveis e classes `.amp-*` |
| `showcase.html` | A prova visual, standalone, sem dependência externa |
