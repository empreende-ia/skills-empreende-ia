# Instalar a skill `copy-hormozi`

## O que é

Uma skill de Claude Code que escreve copy de resposta direta no método Alex Hormozi —
página de vendas, VSL, anúncio, sequência de e-mail de lançamento, headline — e também
**audita** copy pronta dizendo por que não converte.

Calibrada pro mercado brasileiro: R$, parcelamento, CDC, e as objeções que só aparecem aqui.

## Instalação

1. Descompacte o arquivo `copy-hormozi.zip`.
2. No Claude Code, selecione a pasta onde está a pasta `copy-hormozi` e mande este pedido:

> Instale a skill que está na pasta copy-hormozi deste material na pasta de skills pessoais do
> Claude Code deste sistema operacional, substituindo se já existir. Depois confira o SKILL.md e
> me responda só: instalada ou faltou, seguido do caminho que você usou.

3. Feche e abra o Claude Code. A skill aparece como `/copy-hormozi`.

## Como usar

Digite `/copy-hormozi` e diga o que precisa. Se você já preencheu o Modelo de Oferta, anexe o
documento na conversa: a skill parte dele. Exemplos:

- "escreve a página de vendas do meu curso de X"
- "monta a sequência de e-mail do carrinho"
- "5 headlines pra essa oferta"
- "audita essa página, ela não converte" *(cole o texto)*

## Como ela trabalha

**Fase 0 é obrigatória e ela não pula.** Antes de escrever qualquer frase, a skill quer saber
qual é a oferta — quem compra, o que ganha, qual a prova, qual o preço, qual a garantia. Se
você não tiver isso, ela roda um intake de 9 perguntas. Se a oferta for fraca, ela avisa em vez
de escrever bonito em cima de coisa que não vende.

Depois vem ângulo → escrita no molde → 4 passadas de revisão (especificidade, corte, objeção,
voz) → variantes pra teste + QA de 22 pontos.

**Ela tem vetos.** Não escreve urgência falsa (contador que reseta, "últimas 3 vagas" inventado)
nem número que você não consegue provar. Isso é de propósito: um print de contador falso
circulando num grupo de WhatsApp custa mais caro que qualquer ponto de conversão.

## O que tem dentro

| Arquivo | Serve pra |
|---|---|
| `SKILL.md` | O processo inteiro — roteador, 5 fases, regras de ouro, modo auditar |
| `references/voz.md` | Como o Hormozi escreve, traduzido em regras · palavras banidas |
| `references/ganchos.md` | 7 fórmulas de headline (MAGIC, contrarian, prova…) · gancho de 3s |
| `references/carta-vsl.md` | Os 13 blocos da página de vendas · os tempos da VSL |
| `references/emails.md` | Cadência de 11 e-mails · assunto · entregabilidade |
| `references/ads.md` | Gancho-retenção-recompensa · 4 ângulos · alinhamento anúncio↔página |
| `references/objecoes.md` | As 4 objeções reais · 4 tipos de garantia · A-C-A · objeções BR |
| `references/conformidade.md` | CDC, CONAR, LGPD · urgência real vs. falsa · limite da promessa |
| `templates/` | Os moldes de saída de cada formato + o QA de 22 pontos |

Nada aqui depende de projeto, conta ou ferramenta específica — é texto puro, funciona em
qualquer máquina com Claude Code.

## Escopo

**Faz:** headline, lead, página, VSL, anúncio, e-mail, story/DM/WhatsApp, nome de oferta,
auditoria de copy, variantes pra teste.

**Não faz:** engenharia de oferta, design/layout, conteúdo de topo de funil pra social, mídia
paga e segmentação. Quando o pedido for de outra caixa, ela diz qual e para.
