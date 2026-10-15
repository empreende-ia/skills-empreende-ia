---
name: nogueira-prumo-design
description: Use para gerar qualquer interface, documento ou peça da Nogueira Prumo — consultoria de estratégia e governança — e, de modo geral, para marcas de serviço profissional B2B que vendem julgamento e reputação (consultoria, advocacia, contabilidade, gestão patrimonial). Sistema claro e editorial: serif de alto contraste nos títulos, sans neutra no corpo, vinho como única cor de assinatura.
user-invocable: true
type: design-system
ds-tokens: tokens.css
ds-brand: Nogueira Prumo
ds-signature: "#6B2436"
---

Leia o `README.md` desta skill antes de escrever qualquer linha — ele traz o
posicionamento da marca, as regras de tipografia, as regras de componente e estado, e a
seção de VOZ (tabela falar/não falar e o que nunca aparece no texto).

Leia o `tokens.css` e use as variáveis e as classes `.np-*` diretamente. Nunca invente um
hex novo, um raio novo ou uma sombra nova: se algo não existe no arquivo, provavelmente
não deve existir na tela. Para ver o sistema aplicado, abra o `showcase.html`.

Se a peça for um artefato visual (mock, slide, proposta, one-pager), gere um HTML estático
com o `tokens.css` embutido no `<style>`, sem nenhuma dependência externa. Se for código de
produção, mapeie as variáveis no tema do projeto preservando os nomes em português
(`vinho-700`, `texto-medio`, `fio`) — o vocabulário faz parte do sistema.

Se a skill for invocada sem contexto, pergunte o que vai ser construído, para quem e em que
suporte (tela, PDF, apresentação) — e então produza como um design lead, não como um
gerador de layout.

## Quick reference

- **Cor de assinatura:** vinho `#6B2436`. Fundo é branco puro `#FFFFFF`; tinta é `#17120F`
  (quase-preto quente). Vinho nunca passa de ~5% da área — fios, marcadores, um número, um
  botão. Nunca fundo grande.
- **Duas famílias nativas, zero fonte remota:** títulos em `Didot → Bodoni 72 → Iowan Old
  Style → Georgia`; corpo em `Helvetica Neue → system-ui → Arial`. A tensão serif/sans é a
  ideia central.
- **A serif nunca desce de 19px** e nunca vira interface (rótulo, botão, tabela, campo são
  sempre sans).
- **Fio de 1px é a hierarquia.** Antes de criar caixa, sombra ou fundo colorido, use um fio
  ou mais espaço. Cantos de 0 a 2px; sombra só no que flutua de verdade.
- **Assinatura visual:** o fio-prumo — fio vertical de 1px em vinho com losango de 5px no
  pé. Uma vez por bloco, nunca em série.
- **Medida travada em 65 caracteres**, entrelinha 1,65, respiro de 96px entre seções, tudo
  alinhado à esquerda. Números tabulares, à direita em tabela.
- **Um único botão vinho por tela** (a ação de conversão); as demais ações são tinta,
  contorno ou texto. Foco sempre visível: anel quadrado vinho.
- **Voz:** primeira do plural, frase curta e declarativa, travessão como pontuação da casa.
  Sem emoji, sem exclamação, sem superlativo, sem jargão de startup.
