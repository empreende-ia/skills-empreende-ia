# Bancos de pergunta por tipo de entrega

Leia só o bloco do tipo que o usuário pediu. Cada bloco traz: o que perguntar no **contexto**,
que **referência** pedir, e os critérios que quase sempre se aplicam (use como sugestão pronta,
não como imposição).

A primeira linha de cada bloco diz se a etapa de **identidade visual** da Rodada 1 se aplica —
tipo com tela resolve o design system antes de qualquer outra pergunta; tipo sem tela pula, e
avisa que pulou.

---

## Landing page / site

> **Identidade visual: resolve.** É o tipo em que o design system mais economiza discussão —
> com DS, a referência que você pede é de estrutura e copy, não de cor.

**Contexto:** o que a página vende e por quanto · quem cai nela e vindo de onde (anúncio, e-mail, bio do Instagram) · já existe marca definida (cor, fonte, logo)? · onde vai ser publicada (Lovable, Vercel, WordPress, Framer) · o lead cai onde (e-mail, WhatsApp, CRM)?

**Peça:** print de 1 a 3 landings que ele gosta ("e me diz o que especificamente você gosta em cada uma") · logo e cores · o texto de vendas se já existir · print da página atual, se houver.

**Critérios típicos:** abre no celular de 375px sem rolagem lateral · tem exatamente N seções, nesta ordem · o botão principal aparece sem rolar a tela · o formulário envia de verdade e o dado chega em [destino] · carrega em menos de 2s · nenhum texto placeholder tipo "lorem ipsum" ou "seu texto aqui" sobrou.

---

## Sistema do zero (rota B — gera PRD)

> **Identidade visual: resolve.** O DS escolhido aqui vale pras fases seguintes também —
> registre em Decisões no PRD, senão a fase 2 nasce com outra cara.

**Contexto:** quem são os tipos de usuário e o que cada um pode fazer · precisa de login? · que informação o sistema guarda e quem pode ver · quais ferramentas externas entram (e se ele já tem conta e chave em cada uma) · quantas pessoas usam e com que frequência · tem prazo ou data-marco · quem vai manter isso depois de pronto.

**Peça:** a planilha/caderno/grupo de WhatsApp onde isso é feito hoje (é o melhor PRD que existe) · print da ferramenta atual · exemplo real de um registro preenchido · print de um sistema parecido que ele gosta.

**A pergunta que define a fase 1:** *"se eu te entregasse só uma tela funcionando na semana que vem, qual seria?"* — a resposta é a fase 1, não o que ele listou primeiro.

**Critérios típicos:** um usuário novo completa [o fluxo principal] sem instrução · o dado cadastrado continua lá depois de fechar e abrir · quem é [perfil A] não enxerga o dado de [perfil B] · exporta o mês em um clique · funciona no celular, que é onde a equipe realmente usa · nenhuma chave de API dentro do código.

---

## Ambiente / ferramenta interna da equipe (rota B — gera PRD)

> **Identidade visual: resolve, se tiver tela.** Ferramenta de linha de comando pula a etapa;
> painel interno não pula — interno também é visto todo dia.

**Contexto:** quem instala e quem usa no dia a dia · em que máquina roda (Mac, Windows, servidor) · o que existe hoje e vai ser substituído · quem mantém quando quebrar · precisa funcionar sem internet?

**Peça:** o processo escrito, se existir · print do que a equipe usa hoje · a lista de passos que a pessoa faz na mão.

**Critérios típicos:** alguém de fora instala seguindo o README sem perguntar nada · roda com um comando só · falha com mensagem que diz o que fazer, não com stack trace · não depende de nada instalado só na sua máquina.

---

## App / feature nova em algo que já existe

> **Identidade visual: resolve, começando pelo projeto.** Aqui a varredura do projeto vale mais
> que a das skills: se já existe tokens/Tailwind customizado, o DS é esse e a feature nova segue ele.

**Contexto:** onde está o código · linguagem e framework (confirme lendo o projeto, não perguntando) · roda como (browser, celular, servidor) · o que **não** pode quebrar · tem teste? tem build? · quem mais mexe nesse código.

**Peça:** o caminho da pasta/repositório · print do erro ou da tela atual · exemplo do dado real que entra.

**Critérios típicos:** roda com [comando] sem erro no console · o fluxo X continua funcionando · não instalou dependência nova · o diff é cirúrgico (sem renomear nem reordenar o que já existia) · dado antigo continua sendo lido (mesma chave/tabela/formato).

---

## Automação / integração

> **Identidade visual: não se aplica** — sem tela, sem design system. Pule a etapa dizendo isso.
> (Exceção: se a automação tiver painel de acompanhamento, aí resolve.)

**Contexto:** o gatilho (o que faz começar) · as ferramentas envolvidas e se ele já tem conta/chave em cada uma · o volume por dia · o que acontece hoje na mão · quem quebra se isso falhar.

**Peça:** print da tela da ferramenta · exemplo real de uma entrada (a mensagem, o e-mail, a linha da planilha) · a documentação ou o link da API.

**Critérios típicos:** roda de ponta a ponta com um caso real de teste · se falhar, avisa em [canal] em vez de morrer calado · não dispara duas vezes pro mesmo evento · segredo nenhum fica escrito no código · aguenta N execuções por dia.

---

## Conteúdo (post, e-mail, roteiro, copy)

> **Identidade visual: não se aplica** — o que segura o padrão aqui é a voz, não os tokens.
> (Exceção: peça que vira arte ou e-mail em HTML, aí resolve.)

**Contexto:** canal e formato · pra quem (e o que essa pessoa já sabe do assunto) · a voz (formal, direta, provocativa — peça um exemplo do que ele já escreveu) · o que essa peça precisa fazer a pessoa fazer · o que é proibido dizer.

**Peça:** 2 ou 3 peças antigas que funcionaram ("é essa a voz") · a fonte do conteúdo (PDF, aula, live, transcrição) · print da métrica se houver.

**Critérios típicos:** cabe em N caracteres · primeira linha segura sem depender de contexto · tem exatamente uma chamada pra ação · não usa [lista de palavras banidas] · dá pra ler em voz alta sem tropeçar.

---

## Análise de dados / planilha / relatório

> **Identidade visual: não se aplica.** (Exceção: se a entrega for dashboard ou relatório
> publicado com a cara da marca, aí resolve.)

**Contexto:** onde estão os dados e em que formato · o que cada coluna significa (peça o cabeçalho real) · o período · a pergunta de negócio por trás · quem lê o resultado.

**Peça:** o arquivo (ou 10 linhas de amostra, com os dados sensíveis trocados) · o relatório atual, se existir.

**Critérios típicos:** o total bate com [número que ele já conhece] · trata linha vazia e valor duplicado sem quebrar · responde a pergunta de negócio em uma frase no topo · gráfico legível impresso em preto e branco · dá pra rodar de novo mês que vem sem editar o código.

---

## Agente de IA / bot de atendimento

> **Identidade visual: só se tiver tela própria** — widget no site ou painel de conversas resolve;
> agente que só vive no WhatsApp pula.

**Contexto:** o canal (WhatsApp, site, voz) · o que ele resolve e o que ele **não** resolve · quando passa pra humano · de onde vem a informação verdadeira (base, site, planilha) · o tom.

**Peça:** conversas reais de atendimento (as boas e as ruins) · a base de conhecimento atual · a lista das 10 perguntas mais frequentes.

**Critérios típicos:** acerta as 10 perguntas mais frequentes (vira o golden set) · nunca inventa preço/prazo — se não souber, diz que não sabe e passa adiante · passa pra humano quando [condição] · resposta em até N segundos · nunca pede dado sensível.

---

## Tipo não listado

Monte as perguntas do zero com estas quatro lentes, na ordem:
**onde isso vive** · **quem depende disso** · **o que já existe e não pode quebrar** · **como a pessoa vai testar quando receber**.

A regra da identidade visual é uma só, e vale pra qualquer tipo: **alguém vai olhar isso numa
tela?** Se sim, resolve o design system na Rodada 1. Se não, pule e diga que pulou.
