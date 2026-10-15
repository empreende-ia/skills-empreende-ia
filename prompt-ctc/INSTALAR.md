# Como instalar a skill /prompt-ctc

Você recebeu uma pasta chamada `prompt-ctc`. Ela ensina o Claude Code a te entrevistar
e montar um prompt completo — Contexto, Tarefa e Critério de aceite — antes de construir qualquer coisa.

## Instalação (1 minuto, sem terminal)

Quem instala é o próprio Claude — você só pede.

1. No app do Claude, abra a aba **Code → Local** e selecione a pasta onde está a `prompt-ctc`
   (a pasta do kit, ou a pasta onde você descompactou o arquivo).
2. Numa conversa nova, cole o pedido abaixo e envie:

```
Instala a skill que está na pasta prompt-ctc deste material na pasta de skills pessoais do Claude Code deste sistema operacional, sobrescrevendo se já existir. Depois confere se o SKILL.md está lá e me responde só "instalada" ou "faltou", seguido do caminho que você usou.
```

3. Confira: digite `/prompt` na caixa de mensagem — a `/prompt-ctc` aparece na lista.
   Não apareceu? Feche o app do Claude (botão direito no ícone → Encerrar) e abra de novo.

> Quer a skill só num projeto específico, em vez de em toda a máquina?
> No pedido, troque "na pasta de skills pessoais do Claude Code" por "na pasta .claude/skills deste projeto".

## Como usar

Digite:

```
/prompt-ctc
```

E diga, do jeito mais preguiçoso possível, o que você quer construir. Pode ser bem vago:

- "quero uma landing page"
- "quero um negócio pra organizar meus clientes"
- "queria automatizar essa parte chata do meu atendimento"
- "não sei bem, tenho uma ideia na cabeça"

**Não saber ainda é normal — a skill foi feita pra isso.** Ela começa com uma rodada de
**descoberta**: pergunta o que te incomoda hoje, quem mais mexe nisso, se precisa guardar informação
e com que ferramentas precisa conversar. Só então ela decide o que você está construindo de fato.

Depois vêm as três rodadas do método — **Contexto**, **Tarefa** e **Critério de aceite** — e no meio
do caminho ela pede uma referência (print, link, PDF, arquivo). **Mande.** É o passo que mais muda o
resultado final.

No fim, a skill explica o que gerou e o que acontece com ele. Se você estiver dentro de um projeto no
Claude Code, na primeira vez da sessão ela pergunta antes: **executar ali mesmo** (ela constrói e
confere cada critério) ou **só gerar o prompt** (pra você guardar, colar em outra sessão ou mandar pra
alguém). Fora de um projeto, você recebe o prompt pronto pra colar.

### Se o que você quer for um sistema

Quando o pedido for maior — guarda dados, tem login, tem mais de um tipo de usuário, integra com
outras ferramentas — a skill não entrega só um prompt. Ela escreve um **PRD** (`docs/PRD.md`) dentro
do próprio projeto: o que é, pra quem, em quantas fases, e os critérios de aceite em forma de
checklist.

Esse documento serve pra duas coisas: **conferir** se o que foi construído bate com o que você pediu,
e **evoluir** junto com o projeto — a cada fase você marca o que passou e registra o que mudou de
ideia. Depois é só voltar e dizer "terminei a fase 1" que ela confere os critérios e monta o prompt
da fase seguinte.

## As três perguntas que você deveria saber responder sozinho

Se um dia você não tiver a skill à mão, o método cabe em três perguntas:

1. **Onde eu estou pisando?** → o que já existe e não pode quebrar
2. **O que exatamente é pra fazer?** → lista numerada e fechada
3. **Como eu vou saber que ficou bom?** → um teste que pode falhar

A terceira é a que quase todo mundo pula — e é a que separa "pronto!" de pronto.
