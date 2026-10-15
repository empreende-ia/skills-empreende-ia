# Template de PRD — `docs/PRD.md`

Documento vivo. Nasce curto, cresce com o projeto. **Uma página no começo é melhor que dez páginas
que ninguém lê.** Corte qualquer seção que não se aplique.

Datas sempre absolutas (`2026-08-02`), nunca "hoje" ou "semana passada" — quem lê daqui a 3 meses
não sabe quando você escreveu.

---

```markdown
# PRD — <nome do projeto>

**Status:** fase 1 em construção · **Criado:** <AAAA-MM-DD> · **Última revisão:** <AAAA-MM-DD>

## 1. O problema
<O que acontece hoje que não deveria. Como é feito agora — na mão, na planilha, no WhatsApp.
Duas ou três frases, na língua de quem sofre o problema, não na língua de quem programa.>

## 2. O resultado esperado
<Como fica quando estiver funcionando. Uma frase. Se der pra medir, meça:
"o atendente para de digitar o mesmo dado duas vezes" vale mais que "otimizar o processo".>

## 3. Quem usa
| Quem | O que faz no sistema | Quantos |
|---|---|---|
| <ex: atendente> | cadastra pedido, consulta cliente | <ex: 4 pessoas> |
| <ex: dono> | vê o resumo do mês | 1 |
| <ex: cliente final> | acompanha o pedido por link | <ex: ~200/mês> |

## 4. Fluxos principais
<O caminho que a pessoa percorre, em passos. Um bloco por fluxo, só os principais.>

**Fluxo 1 — <nome>:** entra em X → preenche Y → o sistema faz Z → recebe W.

## 5. Dados que o sistema guarda
| Coisa | Campos principais | Observação |
|---|---|---|
| <ex: Cliente> | nome, telefone, e-mail | telefone é o identificador único |
| <ex: Pedido> | cliente, itens, valor, status | status: novo → pago → entregue |

## 6. Integrações
| Ferramenta | Pra quê | Acesso | Risco |
|---|---|---|---|
| <ex: WhatsApp Cloud API> | avisar o cliente | tem conta, falta o token | bloqueia a fase 2 |
| <ex: Google Sheets> | exportar o fechamento | ok | — |

## 7. Escopo por fase

### Fase 1 — <nome> (a menor coisa usável de ponta a ponta)
1. <item>
2. <item>
3. <item>

### Fase 2 — <nome>
- <item>

### Fase 3 — <nome>
- <item>

### Fora de escopo (por enquanto, e de propósito)
- <o que já foi cogitado e cortado — escrever aqui evita que volte por acidente>

## 8. Decisões técnicas
| Decisão | Por quê | Data |
|---|---|---|
| <ex: Supabase em vez de banco próprio> | auth pronta, o time não tem quem cuide de servidor | <AAAA-MM-DD> |
| <ex: design system: skill `henrique-gabriel-design` (#10b981)> | identidade já existe e vale pra todas as fases; ninguém escolhe cor no meio do caminho | <AAAA-MM-DD> |

<Sistema com tela registra aqui qual design system foi adotado — o nome da skill ou o arquivo de
tokens do projeto. Se ficou sem, escreva `[SEM DESIGN SYSTEM — a IA escolhe cor, fonte e
espaçamento]`: decisão visual não registrada é decisão que a fase 2 toma de novo, diferente.>

<Toda decisão que a IA tomou sozinha durante o desenvolvimento entra aqui também.>

## 9. Critérios de aceite

> Regra: cada linha tem que poder **falhar**. Se não dá pra dar errado, não é critério, é desejo.
> Marque `[x]` só o que você testou de verdade.

### Fase 1
- [ ] <critério verificável>
- [ ] <critério verificável>
- [ ] <critério verificável>

### Fase 2
- [ ] <critério verificável>

### Sempre vale (não quebrar nunca)
- [ ] <ex: dado antigo continua sendo lido depois de qualquer mudança>
- [ ] <ex: nenhuma chave de API dentro do código>
- [ ] <ex: nenhuma cor, fonte, raio ou espaçamento fora dos tokens do design system adotado>

## 10. Riscos e pendências
| O quê | Impacto | Quem resolve | Status |
|---|---|---|---|
| <ex: não temos o token do WhatsApp> | trava a fase 2 | <nome> | aberto |

## 11. Histórico
| Data | O que mudou |
|---|---|
| <AAAA-MM-DD> | PRD criado |
```

---

## Como este documento evolui

**Ao terminar uma fatia:** teste cada critério da fase, marque `[x]` só os que passaram de verdade,
liste os que falharam como tarefa da próxima rodada, atualize `Última revisão` e o Histórico.

**Quando mudar de ideia:** não apague a linha antiga — ~~risque~~ e registre em Decisões, com data e
motivo. Três meses depois, é esse histórico que impede a mesma discussão de voltar.

**Quando a IA decidir algo sozinha:** ela registra em Decisões. Suposição escondida vira retrabalho;
suposição escrita vira uma pergunta de 10 segundos.

**Quando a fase acabar:** promova a fase seguinte e **reescreva** ela antes de construir. Fase 2 quase
nunca sobrevive intacta ao aprendizado da fase 1 — e tudo bem, é pra ser assim.

## Erros comuns (o que faz um PRD morrer)

- **Nasce grande.** Dez páginas escritas antes da primeira linha de código não sobrevivem ao primeiro contato com o real.
- **Vive fora do projeto.** PRD no Notion, código no repositório: em duas semanas discordam, e ninguém sabe qual está certo.
- **Critério sem teste.** "Ser intuitivo" não pode falhar, logo não é critério.
- **Não registra decisão.** Sem histórico, toda escolha vira discussão nova.
- **Ninguém marca o checkbox.** Um PRD com tudo desmarcado depois de dois meses de trabalho é um PRD abandonado — e nesse ponto ele engana mais do que ajuda.
