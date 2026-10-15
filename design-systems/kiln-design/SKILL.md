---
name: kiln-design
description: Use esta skill para construir qualquer interface de produto técnico com a identidade Kiln — dashboard de API, painel de observabilidade, plataforma de automação, console interno ou admin de infraestrutura — em produção, protótipo, mock ou slide.
user-invocable: true
type: design-system
ds-tokens: tokens.css
ds-brand: Kiln
ds-signature: "#F08519"
---

Leia o `README.md` desta pasta antes de escrever qualquer linha de código: ele traz a paleta com os
papéis de cada cor, as regras de tipografia, o contrato de cada componente e a seção de VOZ (a tabela
"falar / não falar" e as regras de escrita da marca).

Depois leia o `tokens.css`. Ele é a fonte de verdade: variáveis CSS + classes utilitárias com prefixo
`.kl-`. Nunca invente um valor de cor, espaço, raio ou duração — se o token não existe, o sistema não
tem aquele valor. Para instalar num projeto: copie o arquivo, faça `<link rel="stylesheet"
href="tokens.css">` e coloque `class="kl"` no `<body>`. Sem build, sem webfont, sem CDN.

O `showcase.html` é a referência visual montada: abra no navegador para ver marca, paleta, escala de
tipo, componentes em todos os estados, raios, elevação e regras de uso. Use-o como gabarito quando
precisar montar uma tela nova.

Se a pessoa invocar esta skill sem dizer o que quer, pergunte que tela ela vai construir e quais dados
aparecem nela — no Kiln o dado define o layout, não o contrário.

## Quick reference

- **Assinatura:** âmbar de forja `#F08519` (`--kl-ember-500`) contra neutros azulados frios
  (`#0B0E14` base, `#11151D` card). O contraste de temperatura é a ideia inteira: nenhum segundo tom
  quente entra no sistema.
- **Duas faces com papéis fixos:** mono é estrutural (rótulo, número, metadado, navegação, tabela,
  botão, badge), sans é só texto corrido. **Se é dado, é mono.** Ambas são stacks nativas do SO.
- **Densidade:** UI opera em 13px, controle tem 32px de altura, gutter e padding de card são 24px,
  hairline de 1px, todo número com `tabular-nums` e alinhado à direita.
- **Cantos:** máximo 6px. Padrão 4px. Badge é retângulo, indicador de status é quadrado de 6px,
  avatar é quadrado. **Nada de pílula.**
- **Regra de componente:** um preenchimento âmbar por vista (o botão primário); hover só onde há
  destino; `:focus-visible` sempre com o anel âmbar `--kl-ring`; desabilitado é `opacity .42`,
  carregando é `opacity .72` com o rótulo intacto.
- **Cor de estado nunca vem sozinha:** quadrado de 6px + palavra (`operacional`, `degradado`, `caído`).
  Âmbar marca ação, nunca estado.
- **Assinaturas visuais:** cursor de bloco âmbar no wordmark `kiln▮` · label mono maiúsculo com
  tracking 0.08em seguido de hairline atravessando a largura · quadrado de status · colunas de número
  tabular.
- **Nunca:** gradiente decorativo, glow, sombra colorida, emoji, ponto de exclamação, número em sans,
  animação em conteúdo de dado, Title Case em português, adjetivo no lugar de número.
