# Exemplo completo — padrão de qualidade

Use como referência do nível de detalhe esperado na saída. Não copie o conteúdo; copie a **densidade**.

---

## O pedido original do aluno

```
melhora o jogo snake 3d
```

## O prompt que a skill produziu

```
## CONTEXTO
Trabalho no arquivo snake3d.html deste diretório — um Snake 3D que construí
em uma sessão anterior. Fatos que você precisa saber antes de tocar em qualquer linha:

- É WebGL puro, sem Three.js e sem nenhuma dependência externa. Não instale nada.
- É arquivo único (HTML + CSS + JS no mesmo arquivo), ~913 linhas. Tem que continuar assim:
  vou abrir com duplo clique, sem build e sem servidor.
- Tabuleiro 17x17 (const N), loop de tick com tickInt/tickAcc, HUD com pontos/nível/recorde,
  recorde salvo em localStorage na chave 'snake3d_best', som via WebAudio, comida + bônus + partículas.
- É material didático: o código precisa continuar legível pra eu explicar na tela.
- O jogo já funciona. Não quero refatoração geral, renomeação em massa nem mudança de estilo visual.

## TAREFA
1. Pause: tecla P (e Esc) congela o jogo e mostra um overlay "PAUSADO". Apertar de novo retoma.
2. Obstáculos: a partir do nível 3, 4 blocos fixos no tabuleiro. Colidir com eles mata.
   A cada novo nível, os blocos são reposicionados.
3. Botão de mute clicável no HUD, refletindo o estado que já é salvo em localStorage.

Implemente exatamente estas coisas, nada além delas.

### Fora de escopo
Modo multiplayer, ranking online, menu de configurações, troca de skin da cobra.
Não mexa nos shaders nem no render loop além do necessário pra desenhar os obstáculos.

## CRITÉRIO DE ACEITE
Só considere pronto quando tudo abaixo for verdade:
- Abre com duplo clique e joga do início ao fim com ZERO erro no console.
- Pause: pausar 10s e retomar — a cobra NÃO pula casa (o acumulador de tick não pode estourar
  com o tempo parado).
- Obstáculo nunca nasce em cima da cobra, da comida, do bônus, nem na casa imediatamente
  à frente da cabeça, e nunca prende a cobra num beco sem saída no instante em que aparece.
- Recorde continua funcionando com a MESMA chave 'snake3d_best'.
- Continua fluido (60fps) com a cobra longa.
- Diff cirúrgico: sem renomear variável existente, sem reordenar função, arquivo único.

## ENTREGA
Ao final, responda em 3 bullets: o que mudou, em que função/linha, e como eu testo
cada uma das três features em 10 segundos.
```

---

## Por que este prompt funciona — os três pontos pra apontar em aula

1. **"É arquivo único, abro com duplo clique"** → impede que a IA quebre em módulos e monte um build.
   Contexto que não impede nada não deveria estar ali.
2. **"nada além delas" + seção Fora de escopo** → o escopo tem uma parede dos dois lados:
   o que fazer e o que explicitamente não fazer.
3. **"pausar 10s e retomar, a cobra não pula casa"** → é um critério que **pode falhar**.
   É um bug real e específico (o acumulador de tempo estoura enquanto o jogo está parado).
   Compare com "que o pause funcione bem" — esse não tem como dar errado, logo não testa nada.
