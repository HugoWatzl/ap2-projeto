# 📚 Revisão AP2 — Manutenção de Software

Resumo dos capítulos 7, 8, 9 e 10 para estudar e revisar os principais conceitos da prova.

---

# CAPÍTULO 7 — DÍVIDA TÉCNICA

## 1. O que é dívida técnica?

É o custo futuro causado por decisões técnicas que priorizam uma solução rápida ou deixam problemas de qualidade no software.

**Exemplo:** você desenvolve uma funcionalidade rapidamente sem organizar bem o código. Economiza tempo agora, mas terá mais dificuldade para fazer alterações no futuro.

A metáfora foi introduzida por **Ward Cunningham** para facilitar a comunicação desses custos com gestores.

## 2. Principal inicial, juros e principal atual

Essa é uma das partes mais importantes para a dissertativa.

| Conceito | Significado |
|---|---|
| Principal inicial | Tempo economizado ao adotar um atalho |
| Juros | Tempo extra gasto em manutenções futuras |
| Principal atual | Esforço necessário agora para eliminar a dívida |

**Exemplo:**

Você economizou 2 dias fazendo um código desorganizado. Depois, toda nova funcionalidade exige 3 horas extras. Um ano depois, corrigir a estrutura inteira exige 5 dias.

- Principal inicial: 2 dias economizados.
- Juros: 3 horas extras por manutenção.
- Principal atual: 5 dias para corrigir a estrutura.

## 3. Dívida de testes x dívida de arquitetura

Existe um ciclo vicioso:

1. Poucos testes automatizados.
2. Medo de refatorar o código.
3. Arquitetura fica mais deteriorada.
4. Código fica ainda mais difícil de testar.

A falta de testes aumenta o medo de modificar o código. Sem refatorações, a arquitetura piora e torna os testes mais difíceis.

## 4. Quando pagar a dívida?

Priorize os componentes alterados com maior frequência e nos quais a dívida provoca maiores custos.

**Exemplo:** uma classe modificada toda semana merece mais atenção do que um módulo antigo que funciona e quase nunca muda.

## 5. Dívida técnica planejada e não planejada

**Planejada:** a equipe sabe que está adotando um atalho para atingir um objetivo de negócio, como lançar um MVP mais cedo.

**Não planejada:** surge por descuido, falta de conhecimento ou práticas inadequadas.

A dívida planejada pode ser estratégica quando o ganho imediato compensa os custos e existe uma intenção de corrigi-la depois.

## 6. Dívida de requisitos

Surge quando os requisitos são mal definidos, não validados ou mudam constantemente sem controle.

**Consequências:**

- Retrabalho.
- Funcionalidades inúteis.
- Problemas de usabilidade.
- Desperdício de recursos.

**Exemplo:** desenvolver um sistema de consultas sem confirmar com a clínica como ela realiza os agendamentos.

## 7. Teoria das Janelas Quebradas

Pequenos problemas ignorados transmitem a impressão de que a qualidade não importa.

Quando o desenvolvedor encontra código desorganizado, pode acabar repetindo as mesmas práticas, piorando o sistema.

**Resumo:** negligenciar pequenos problemas favorece uma deterioração maior.

## 8. Regra dos Escoteiros e refatoração oportunista

A regra diz:

> Deixe o código mais limpo do que o encontrou.

Refatoração oportunista é aproveitar uma alteração que já seria feita para melhorar pequenos trechos próximos.

**Exemplo:** ao corrigir um bug, você também remove uma duplicação e melhora o nome de uma variável.

Não é necessário parar o projeto inteiro para melhorar o código.

---

# CAPÍTULO 8 — SISTEMAS LEGADOS

## 1. O que são sistemas legados?

São sistemas existentes, muitas vezes antigos, que continuam importantes para a operação de uma organização.

Podem apresentar:

- Tecnologias antigas.
- Alto acoplamento.
- Documentação incompleta.
- Poucos testes automatizados.

**Importante:** sistema legado não significa sistema inútil. Muitos sustentam operações críticas de bancos e empresas.

## 2. Sprout x Wrapper

Essa diferença é muito importante na prova.

### Sprout

O código legado é alterado para chamar a função nova.

### Wrapper

Uma nova função envolve e chama o legado, sem alterar seu interior.

**Decore assim:**

- **Sprout:** entra no legado e adiciona uma chamada para a função nova.
- **Wrapper:** cria uma função por fora que chama o legado.

## 3. Testes em produção

Duas técnicas importantes são:

### Dark Launch

Uma funcionalidade nova é executada em produção, mas permanece invisível para o usuário final.

Serve para observar desempenho, carga e erros.

### Canary Release

Uma versão nova é disponibilizada inicialmente a um grupo pequeno de usuários.

O comportamento é observado antes de ampliar a implantação.

**A revisão cobra diretamente o Dark Launch.**

## 4. Strangler Fig x Big Bang

### Strangler Fig — migração gradual

Substitui progressivamente partes do sistema legado por serviços novos, até que o legado possa ser desativado.

### Big Bang — migração de uma vez

Substitui o sistema inteiro em uma grande transição, concentrando os riscos da mudança.

**Resumo:**

- Strangler Fig: migração gradual.
- Big Bang: substituição completa de uma vez.

Para sistemas grandes e críticos, a migração gradual costuma ser mais segura.

**Atenção:** a questão 6 do capítulo 8 apresenta uma inconsistência no gabarito original. Ela marca como verdadeira a afirmação de que Big Bang garante uma transição sem riscos, mas isso não é correto.

## 5. FanInSet e FanOutSet

São conjuntos utilizados para analisar dependências quando um serviço é extraído de um sistema legado.

- **FanOutSet:** dependências que o novo serviço ainda possui em relação ao legado.
- **FanInSet:** dependências do legado em relação ao serviço extraído.

Quanto maiores esses conjuntos, maior tende a ser o acoplamento e mais complexa pode ser a extração.

## 6. Por que sistemas legados acumulam dívida técnica?

Porque passam anos recebendo alterações, frequentemente com:

- Pouca documentação.
- Testes insuficientes.
- Pressão por entregas.
- Substituição de profissionais.

Duas consequências importantes:

1. Manutenção mais demorada.
2. Aumento dos riscos de regressão.

## 7. Pirâmide de testes invertida

A pirâmide tradicional prioriza:

1. Muitos testes unitários.
2. Testes de integração.
3. Menos testes de ponta a ponta.

Sistemas legados frequentemente têm alto acoplamento, dificultando testes unitários isolados.

Por isso, começar por testes de integração ou ponta a ponta pode ser mais viável.

**Frase da prova:**

> Uma pirâmide invertida é melhor do que nenhuma pirâmide, pois oferece alguma proteção contra regressões.

---

# CAPÍTULO 9 — PROCESSOS

## 1. Desenvolvimento e manutenção na mesma equipe

Separar completamente desenvolvimento e manutenção pode fazer os programadores perderem contato com as consequências de suas decisões.

Quando a mesma equipe desenvolve e mantém o software, ela tem mais incentivo para produzir código limpo, testável e sustentável.

Isso se relaciona ao conceito de **skin in the game**: sentir diretamente as consequências das próprias decisões.

## 2. Git-flow e Hotfix

Hotfix é uma correção urgente para um problema em produção.

No Git-flow:

1. O hotfix nasce da branch `main`.
2. A correção é realizada e testada.
3. A correção é integrada na `main`.
4. A correção também é integrada na `develop`.

**Decore:**

> Hotfix nasce da main e volta para main e develop.

## 3. Scrum e mudanças durante o sprint

Um sprint é um período de trabalho com um objetivo definido.

Mudanças podem ser consideradas, mas não devem comprometer o objetivo do sprint.

O backlog do sprint não é um espaço para inserir livremente qualquer nova solicitação.

**Para a prova:**

O Manifesto Ágil valoriza mudanças porque software é mais flexível que construções físicas.

Os sprints equilibram essa flexibilidade com períodos de foco.

## 4. Pull Requests e Code Review

O Pull Request (PR) permite propor alterações no código e solicitar revisão antes de integrá-las.

### Para autores

- Enviar alterações pequenas e fáceis de compreender.
- Não levar críticas para o lado pessoal.
- Explicar o objetivo das mudanças.

### Para revisores

- Focar em problemas técnicos relevantes.
- Justificar sugestões.
- Manter comunicação respeitosa e colaborativa.

A revisão cita PRs pequenos, idealmente de até aproximadamente 200 linhas, como referência prática, não uma regra universal.

## 5. Post mortem

É um documento elaborado após um incidente para entender o que aconteceu, suas causas e como evitar repetição.

**Não deve servir para procurar culpados.**

Cinco partes:

1. **Linha do tempo:** quando cada evento aconteceu.
2. **Impacto:** quem foi afetado e quais foram as consequências.
3. **Causa raiz:** origem do incidente.
4. **Mitigação:** ações usadas para restaurar o sistema.
5. **Lições aprendidas:** melhorias para evitar novos incidentes.

## 6. SaaS: LTV e CAC

- **LTV:** valor que um cliente gera durante seu relacionamento com a empresa.
- **CAC:** custo necessário para adquirir esse cliente.

Na revisão, a referência apresentada é:

**LTV / CAC > 3**

Isso significa que o cliente deve gerar mais de três vezes o custo de aquisição, como referência de sustentabilidade econômica do SaaS.

## 7. Congelamento de implantação

### Full Deployment Freeze

Bloqueia implantações em produção, exceto emergências críticas.

### Congelamento parcial

Impede funcionalidades novas, mas permite algumas correções controladas.

É comum em períodos críticos, como Black Friday ou Natal, para reduzir riscos operacionais.

## 8. Métricas de manutenção

| Métrica | Para que serve |
|---|---|
| Bugs em produção | Avaliar defeitos que chegaram ao usuário |
| Tempo médio de correção | Medir rapidez na resolução |
| Taxa de reabertura | Avaliar eficácia das correções |

**Exemplo:** se muitos bugs corrigidos são reabertos, pode indicar que as soluções não resolveram completamente o problema.

---

# CAPÍTULO 10 — MANUTENÇÃO USANDO IA

## 1. Naturalidade do código

A hipótese estudada é que códigos escritos por seres humanos apresentam padrões repetitivos e regularidades estatísticas.

Isso permite que modelos de linguagem aprendam padrões e façam sugestões de código.

## 2. Assistentes x agentes de código

| Assistente | Agente |
|---|---|
| Sugere código | Executa tarefas com autonomia |
| Programador dirige os passos | Planeja etapas e usa ferramentas |
| Atua muitas vezes em trechos locais | Pode modificar múltiplos arquivos |
| Ex.: autocompletar original do Copilot | Ex.: agente que modifica e testa um projeto |

**A grande diferença é a autonomia.**

## 3. Agente = Harness + LLM

O agente combina um modelo de linguagem com um sistema responsável por organizar suas ações.

- **LLM:** interpreta o pedido e produz decisões ou instruções.
- **Harness:** coordena ferramentas, histórico, permissões e execução.

**Resumo:**

- LLM = inteligência.
- Harness = estrutura operacional.

## 4. Loop agêntico

O funcionamento de um agente segue um ciclo:

1. Receber objetivo.
2. Planejar próximo passo.
3. Executar ferramentas.
4. Observar resultados.
5. Decidir continuar ou finalizar.

O loop é **stateful**, ou seja, mantém o contexto das interações anteriores.

Ele não começa do zero a cada ação.

## 5. MCP — Model Context Protocol

É um protocolo que padroniza a comunicação entre aplicações de IA e ferramentas ou fontes externas de informação.

**Exemplo:** permitir que um agente consulte registros de bugs, documentação ou arquivos de um sistema usando interfaces padronizadas.

**Importante:** MCP não é um compilador nem um modelo de linguagem.

## 6. Dívida cognitiva

Surge quando a quantidade de código gerado por agentes de IA ultrapassa a capacidade humana de revisar, compreender e manter essas alterações.

**Exemplo:**

Um agente modifica 30 arquivos rapidamente, mas a equipe não entende bem as decisões e encontra dificuldades para corrigir problemas depois.

**Diferença importante:**

- Dívida técnica: custos de decisões técnicas.
- Dívida cognitiva: dificuldade de compreender o sistema.

## 7. Segurança dos agentes

Os mecanismos citados no documento são:

### Sandbox

Ambiente isolado que limita impactos de ações perigosas.

### Aprovação humana

Confirmação para comandos críticos.

### Limites de execução

Limites de iterações, tokens, tempo ou custos.

Evitam loops infinitos ou consumo excessivo de recursos.

## 8. Engenharia de prompts

### Zero-Shot

Pedido sem exemplos.

**Exemplo:**

`Crie uma função que calcule a média de três notas.`

### Few-Shot

Pedido acompanhado de exemplos que orientam o resultado.

**Exemplo:**

`Entrada: 2, 4 → saída: 3.`

`Entrada: 6, 8 → saída: 7.`

`Agora calcule 10, 20.`

### Chain-of-Thought (CoT)

Técnica de prompting que incentiva o modelo a decompor um problema em etapas de raciocínio.

### Prompts para modificação de código

A revisão também aborda dois elementos importantes:

**1. Contexto**

Descrever:

- O problema.
- Mensagens de erro.
- Arquivos envolvidos.
- Exemplos do comportamento incorreto.

**2. Critérios de verificação**

Estabelecer como confirmar que a correção funcionou.

**Exemplo:**

1. Criar um teste que reproduza o bug.
2. Executar o teste e verificar que ele falha.
3. Corrigir o código com base no contexto fornecido.
4. Executar novamente o teste.
5. Confirmar que o erro foi corrigido.

---

# 📝 SIMULADO — REVISÃO AP2

**Instruções:** responda às 15 questões antes de consultar o gabarito no final.

## Questão 1

Um defeito no código provoca comportamento incorreto durante a execução. Isso é:

A) Um crash obrigatoriamente

B) Uma falha

C) Uma refatoração

D) Uma sanitização

## Questão 2

Uma race condition está relacionada a:

A) Falta de documentação

B) Acesso concorrente não sincronizado a dados compartilhados

C) Compilação lenta

D) Problemas exclusivamente visuais

## Questão 3

Qual recurso previne SQL Injection ao separar valores de comandos SQL?

A) Git-flow

B) Prepared Statements

C) Dark Launch

D) Post mortem

## Questão 4

O que representam os juros da dívida técnica?

A) Custo de licença

B) Tempo economizado inicialmente

C) Esforço extra nas futuras manutenções

D) Valor da assinatura

## Questão 5

Qual componente deve ser priorizado para pagar dívida técnica?

A) O menos utilizado

B) O mais antigo obrigatoriamente

C) O modificado frequentemente e com alto custo de manutenção

D) Qualquer um ao acaso

## Questão 6

A Regra dos Escoteiros propõe:

A) Refatorações apenas anuais

B) Melhorar o código oportunamente

C) Eliminar todos os testes

D) Reescrever a aplicação inteira

## Questão 7

Qual afirmação sobre Sprout está correta?

A) Envolve o legado sem alterá-lo

B) Altera o legado para chamar nova função

C) Exige substituir todo o sistema

D) É uma técnica de banco de dados

## Questão 8

O Dark Launch permite:

A) Desligar a aplicação à noite

B) Testar funcionalidade em produção sem exibi-la ao usuário

C) Substituir todo o legado imediatamente

D) Ignorar logs

## Questão 9

O Strangler Fig faz:

A) Migração completa de uma vez

B) Migração progressiva dos serviços

C) Congelamento permanente

D) Remoção dos testes

## Questão 10

No Git-flow, um hotfix nasce de:

A) develop

B) feature

C) main

D) uma branch aleatória

## Questão 11

O post mortem deve priorizar:

A) Encontrar culpados

B) Punir o desenvolvedor

C) Identificar causas e prevenir reincidências

D) Eliminar todos os sprints

## Questão 12

A relação LTV/CAC recomendada no texto é:

A) Menor que 1

B) Maior que 3

C) Igual a zero

D) Sempre 100

## Questão 13

A principal diferença de um agente de código é:

A) Não usar ferramentas

B) Ter maior autonomia para executar tarefas

C) Não utilizar LLMs

D) Apenas completar linhas

## Questão 14

O harness é responsável por:

A) Apenas armazenar pesos da IA

B) Coordenar ferramentas, histórico e permissões

C) Substituir a linguagem de programação

D) Criar o banco de dados sempre

## Questão 15

Qual técnica de prompting utiliza exemplos?

A) Zero-Shot

B) Few-Shot

C) Sandboxing

D) Hotfix

---

# ✅ GABARITO — SIMULADO

**Confira somente depois de responder às 15 questões.**

| Questão | Resposta |
|---|---|
| 1 | B |
| 2 | B |
| 3 | B |
| 4 | C |
| 5 | C |
| 6 | B |
| 7 | B |
| 8 | B |
| 9 | B |
| 10 | C |
| 11 | C |
| 12 | B |
| 13 | B |
| 14 | B |
| 15 | B |

## Gabarito comentado

**1. B — Uma falha**

A falha é o comportamento incorreto observado durante a execução do software.

**2. B — Acesso concorrente não sincronizado**

Uma race condition ocorre quando o resultado depende da ordem ou do momento em que operações concorrentes acessam dados compartilhados.

**3. B — Prepared Statements**

Separam os comandos SQL dos valores fornecidos pelo usuário, ajudando a prevenir SQL Injection.

**4. C — Esforço extra nas futuras manutenções**

Os juros da dívida técnica representam os custos adicionais causados pela dívida ao longo do tempo.

**5. C — Modificado frequentemente e com alto custo**

Componentes alterados frequentemente e que geram custos elevados devem receber maior prioridade.

**6. B — Melhorar o código oportunamente**

A Regra dos Escoteiros recomenda deixar o código mais limpo do que foi encontrado.

**7. B — Altera o legado para chamar nova função**

No Sprout, o código legado recebe uma chamada para a nova implementação.

**8. B — Testar em produção sem exibir ao usuário**

O Dark Launch permite executar e observar uma funcionalidade nova sem disponibilizá-la visualmente ao usuário.

**9. B — Migração progressiva dos serviços**

O Strangler Fig substitui gradualmente componentes legados por implementações novas.

**10. C — main**

No Git-flow, o hotfix é criado a partir da branch main para corrigir problemas críticos em produção.

**11. C — Identificar causas e prevenir reincidências**

O post mortem analisa incidentes para aprender com eles, sem procurar culpados.

**12. B — Maior que 3**

A relação LTV/CAC maior que 3 é a referência de sustentabilidade econômica apresentada na revisão.

**13. B — Maior autonomia para executar tarefas**

Agentes de código podem planejar, utilizar ferramentas, modificar arquivos e verificar resultados.

**14. B — Coordenar ferramentas, histórico e permissões**

O harness oferece a estrutura operacional necessária para o funcionamento do agente.

**15. B — Few-Shot**

Few-Shot utiliza exemplos no prompt para orientar as respostas do modelo.

---

# 📊 RESULTADO DO SIMULADO

| Acertos | Desempenho |
|---|---|
| 15/15 | Excelente |
| 12 a 14 | Muito bom |
| 9 a 11 | Bom, mas precisa revisar |
| 6 a 8 | Revisar os conceitos principais |
| 0 a 5 | Reestudar os capítulos |

---

# 🎯 REVISÃO FINAL — O QUE DECORAR

| Conceito | Palavra-chave |
|---|---|
| Dívida técnica | Custo futuro |
| Principal inicial | Tempo economizado |
| Juros | Manutenção extra |
| Principal atual | Custo para corrigir agora |
| Regra dos Escoteiros | Código mais limpo |
| Sprout | Chamada dentro do legado |
| Wrapper | Nova camada por fora |
| Dark Launch | Invisível ao usuário |
| Canary Release | Pequeno grupo |
| Strangler Fig | Migração gradual |
| Big Bang | Migração de uma vez |
| Hotfix | Nasce da main |
| Post mortem | Aprendizado sem culpados |
| LTV | Valor gerado pelo cliente |
| CAC | Custo de aquisição |
| Agente de código | Autonomia |
| LLM | Inteligência |
| Harness | Coordenação |
| MCP | Integração padronizada |
| Dívida cognitiva | Dificuldade de compreensão |
| Sandbox | Isolamento |
| Zero-Shot | Sem exemplos |
| Few-Shot | Com exemplos |
| Chain-of-Thought | Raciocínio em etapas |
| Contexto do prompt | Informações do problema |
| Critério de verificação | Confirmar a correção |

**Bons estudos!**
