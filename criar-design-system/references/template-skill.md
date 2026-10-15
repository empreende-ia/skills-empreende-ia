# Template do `SKILL.md` gerado (Rodada 4)

Este é o esqueleto do `SKILL.md` que vai para `~/.claude/skills/<marca>-design/`.
Substitua todo `{{PLACEHOLDER}}`. **Não remova os campos de convenção** — sem eles o DS fica
invisível para a varredura e nenhuma outra skill acha ele.

---

## O arquivo

````markdown
---
name: {{marca-slug}}-design
description: "Use esta skill para gerar qualquer interface ou artefato da marca {{Marca}} ({{posicionamento curto}}) — produção, protótipo, slide, mock, template de social, e-mail. Contém tokens de cor, tipo, espaço, raio, elevação e motion, as regras de voz (falar / não falar) e as assinaturas visuais da marca. Use sempre que o pedido envolver {{Marca}}, ou quando um projeto deste dono precisar de identidade visual."
user-invocable: true
type: design-system
ds-tokens: tokens.css
ds-brand: {{Marca}}
ds-signature: "{{#HEXDAASSINATURA}}"
---

# {{Marca}} — Design System

Leia o `README.md` desta skill antes de escrever qualquer linha de CSS ou componente.
`tokens.css` é a **fonte da verdade** — nenhum valor visual nasce fora dele.
`showcase.html` mostra o sistema aplicado; abra quando precisar decidir "como isso deveria parecer".

## Referência rápida

- **Assinatura:** `{{#HEX}}` ({{nome do tom}}). Base {{clara|escura}} `{{#HEX}}`, card `{{#HEX}}`.
- **Faces:** {{Font Display}} no display · {{Font Sans}} no texto · {{Font Mono}} em número e código.
- **Tracking:** {{-0.04em}} no display, 0 no corpo, {{0.15em}} no overline em caixa-alta.
- **Elevação:** {{sombra difusa | glow colorido | borda}} — {{valor}}.
- **Raio:** botão {{12px}} · card {{16px}} · container {{24px}} · pill full.
- **Voz:** {{pt-BR}}, {{primeira pessoa}}, {{regra de caixa}}. Emoji: {{sim|não}}.
- **Assinaturas da marca:** {{1}} · {{2}} · {{3}}.

## Como usar

**Em produção:** importe `tokens.css` no entrypoint e aponte o Tailwind/CSS para as variáveis.
Nunca escreva hex direto no componente.

**Em artefato descartável** (slide, mock, protótipo, post): copie o bloco `:root` do `tokens.css`
para dentro do HTML e use as classes `.{{pfx}}-*`. Arquivo único, abre com duplo clique.

**Se o usuário invocar sem contexto:** pergunte o que vai construir, no máximo 4 perguntas com
opções prontas, e entregue como especialista da marca — HTML pronto ou código de produção,
conforme o caso.

## Proibido

- Hex, rgb ou nome de cor solto em componente — só `var(--token)`.
- Fonte fora das declaradas.
- Cor de destaque que não seja a assinatura.
- {{antipadrão específico desta marca — ex.: "gradiente em área grande", "emoji", "tudo centralizado"}}.
- Inventar valor de espaço/raio fora da escala.

## Arquivos

| Arquivo | O que é |
|---|---|
| `README.md` | O manual: marca, voz, fundamentos visuais, iconografia, ressalvas |
| `tokens.css` | Fonte da verdade — variáveis e classes semânticas |
| `showcase.html` | A prova visual, standalone |
| `assets/` | Wordmark, símbolo, favicon |
````

---

## Os campos de convenção — o que cada um faz

| Campo | Obrigatório | Papel |
|---|---|---|
| `type: design-system` | **sim** | O marcador. É por ele que a varredura filtra. |
| `ds-tokens: tokens.css` | **sim** | Aponta o arquivo de tokens na **raiz** da skill. O arquivo precisa existir de verdade — é o segundo sinal. |
| `ds-brand: {{Marca}}` | recomendado | Nome legível da marca, pra listar sem abrir o arquivo. |
| `ds-signature: "#RRGGBB"` | recomendado | A cor de assinatura, pra identificar de relance. Sempre entre aspas (`#` inicia comentário em YAML). |

`name`, `description` e `user-invocable` continuam sendo o que já eram — a convenção **acrescenta**,
não substitui.

**Detecção = sinal duplo.** Frontmatter marcado **e** arquivo de tokens presente. Frontmatter sem
arquivo é DS quebrado (avise); arquivo sem frontmatter é CSS solto (ignore).
O comando de varredura está no `SKILL.md` da `criar-design-system`.

---

## Apêndice — esqueleto do `README.md`

```markdown
# {{Marca}} — Design System

**Posicionamento:** {{uma frase}}
**Para quem:** {{público}}
**O que NÃO é:** {{anti-posicionamento}}
**Links:** {{site}} · {{social}}

## Fundamentos de conteúdo
Idioma · pessoa verbal · caixa e pontuação · uso de emoji · símbolos permitidos.

### Falar / não falar
| Falar | Não falar |
|---|---|
| ... | ... |   ← mínimo 5 pares, obrigatório

### Padrões retóricos
{{as estruturas de frase que a marca usa: par de contraste, frase curta de fecho, etc.}}

## Fundamentos visuais
Paleta (papel de cada cor) · tipografia (incl. tracking) · espaço · fundos · animação ·
hover e press · bordas e elevação · raios · o componente-assinatura · layout · imagens.

## Iconografia
Biblioteca · espessura · tamanhos · cor · o que não usar.

## As assinaturas da marca
{{2 ou 3, cada uma escrita como RECEITA reproduzível — não como adjetivo}}

## Ressalvas e substituições
{{fonte paga substituída, cor do site divergindo do spec, ativo que falta}}
```
