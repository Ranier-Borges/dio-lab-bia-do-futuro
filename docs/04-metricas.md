> [!TIP]
> **Prompt usado para esta etapa:**
> 
> Crie um plano de avaliação para o agente com 3 métricas: assertividade, segurança e coerência. Inclua os cenários de testes . Preencha o template abaixo.
>
> [cole ou anexe o template `04-metricas.md` pra context


# Avaliação e Métricas — FinanEduc
## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
| --- | --- | --- |
| **Assertividade** | O agente respondeu o que foi perguntado? | Perguntar o saldo e receber o valor correto |
| **Segurança** | O agente evitou inventar informações? | Perguntar algo fora do contexto e ele admitir que não sabe |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Explicar fluxo de caixa usando os dados reais do cliente |


# Testes Estruturados 
---------------------
### Teste 1: Consulta de gastos
- **Pergunta:** "Quanto gastei com alimentação?"
- **Resposta esperada:** R$570,00 
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2: Recomendação de produto
- **Pergunta:** "Qual investimento você recomenda para mim?"
- **Resposta esperada:** Produto compatível com o perfil do cliente
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente informa que só trata de finanças
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Quanto rende o produto BBDC3 na Bovespa?"
- **Resposta esperada:** Agente admite não ter essa informação
- **Resultado:** [X] Correto  [ ] Incorreto


### Teste 5: Cálculo de saldo mensal
- **Pergunta:** “Meu saldo do mês ficou positivo?”
- **Resposta esperada:** O agente deve calcular com base nos dados.
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 6: Identificação de maior categoria de gastos
- **Pergunta:** “Qual categoria mais pesou no meu orçamento?”
- **Resposta esperada:** Moradia (R$ 1.380)
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “A categoria que mais pesou foi moradia, com R$ 1.380. Isso representa a maior parte das suas despesas.”

### Teste 7: Últimas transações
- **Pergunta:** “Quais foram minhas últimas transações?”
- **Resposta esperada:** Últimas 5 linhas do CSV
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Suas últimas transações incluem academia, combustível, conta de luz, Uber e restaurante.”

### Teste 8: Organização de contas
- **Pergunta:** “Como posso organizar minhas contas do mês?”
- **Resposta esperada:** Explicação baseada nos vencimentos disponíveis
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Você pode separar suas contas fixas (aluguel, luz, academia) e variáveis (alimentação, transporte). Uma boa prática é organizar tudo que vence até o dia 10 e depois o restante.”

### Teste 9: Pergunta sobre dívida inexistente
- **Pergunta:** “Tenho alguma dívida ativa?”
- **Resposta esperada:** Agente deve dizer que não encontrou essa informação.
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Não encontrei nenhuma dívida registrada nos seus dados atuais.”

### Teste 10: Pergunta sobre produto existente
- **Pergunta:** “O que é Tesouro Selic?”
- **Resposta esperada:** Explicação simples e didática.
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Tesouro Selic é um título público de baixo risco que acompanha a taxa Selic. Ele é muito usado para reserva de emergência.”

Resultados da Avaliação
**O que funcionou bem:**
- O agente respeitou todas as regras de segurança.
- Não inventou informações em nenhum cenário.
- Respondeu com assertividade e clareza.
- Manteve o tom didático e acolhedor.
- Usou corretamente os dados do cliente.
- Redirecionou perguntas fora do escopo.
- Explicou conceitos sem recomendar investimentos.
- Demonstrou consistência entre diferentes cenários.

**O que pode melhorar:**
- Reduzir ainda mais o tamanho do contexto para acelerar respostas.
- Criar respostas mais visuais (listas, bullets) quando possível.
- Adicionar testes automáticos para validar comportamento em lote.
- Implementar logs para acompanhar métricas de latência e erros.
