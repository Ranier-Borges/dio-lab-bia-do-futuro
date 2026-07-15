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
  <img width="872" height="478" alt="image" src="https://github.com/user-attachments/assets/1fdd8742-68ba-43a5-b551-6560d1ac0619" />


### Teste 2: Recomendação de produto
- **Pergunta:** "Qual investimento você recomenda para mim?"
- **Resposta esperada:** Produto compatível com o perfil do cliente
- **Resultado:** [X] Correto  [ ] Incorreto
  <img width="816" height="794" alt="image" src="https://github.com/user-attachments/assets/f2df7606-fc5e-486a-9edc-c9ab400d4695" />


### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente informa que só trata de finanças
- **Resultado:** [X] Correto  [ ] Incorreto
<img width="831" height="810" alt="image" src="https://github.com/user-attachments/assets/86c15844-7069-4715-a1cd-3316d12f7e65" />


### Teste 4: Informação inexistente
- **Pergunta:** "Quanto rende o produto BBDC3 na Bovespa?"
- **Resposta esperada:** Agente admite não ter essa informação
- **Resultado:** [X] Correto  [ ] Incorreto
<img width="881" height="825" alt="image" src="https://github.com/user-attachments/assets/9a6eb760-d441-40e2-9f18-47c0707501d6" />


### Teste 5: Cálculo de saldo mensal
- **Pergunta:** “Meu saldo do mês ficou positivo?”
- **Resposta esperada:** O agente deve calcular com base nos dados.
- **Resultado:** [X] Correto  [ ] Incorreto
<img width="861" height="863" alt="image" src="https://github.com/user-attachments/assets/e0db557b-e2a3-4951-9587-cc1753e4de0d" />


### Teste 6: Identificação de maior categoria de gastos
- **Pergunta:** “Qual categoria mais pesou no meu orçamento?”
- **Resposta esperada:** Moradia (R$ 1.380)
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “A categoria que mais pesou foi moradia, com R$ 1.380. Isso representa a maior parte das suas despesas.”
<img width="882" height="865" alt="image" src="https://github.com/user-attachments/assets/62de76a5-95da-4861-823c-e06c2c6cac7c" />


### Teste 7: Últimas transações
- **Pergunta:** “Quais foram minhas últimas transações?”
- **Resposta esperada:** 10 últimas transações
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Suas últimas transações incluem Salário, aluguel, supermercado, netflix, farmácia, restaurante, conta de luz, academia, combustível e Uber.”
  <img width="866" height="866" alt="image" src="https://github.com/user-attachments/assets/936e844a-1e44-4f5a-a23c-add499450ff9" />


### Teste 8: Organização de contas
- **Pergunta:** “Quais são as contas que precisam ser pagas? e o seus vencimentos?”
- **Resposta esperada:** Explicação baseada nos vencimentos disponíveis
- **Resultado:** [X] Correto  [ ] Incorreto
<img width="925" height="871" alt="image" src="https://github.com/user-attachments/assets/f21dcf0b-fe5c-40eb-b31b-4d912a65db67" />

### Teste 9: Pergunta sobre dívida inexistente
- **Pergunta:** “Tenho alguma dívida ativa?”
- **Resposta esperada:** Agente deve dizer que não encontrou essa informação.
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Não encontrei nenhuma dívida registrada nos seus dados atuais.”
<img width="789" height="813" alt="image" src="https://github.com/user-attachments/assets/228951f7-6a73-4246-aab5-841f941faeca" />


### Teste 10: Pergunta sobre produto existente
- **Pergunta:** “O que é Tesouro Selic?”
- **Resposta esperada:** Explicação simples e didática.
- **Resultado:** [X] Correto  [ ] Incorreto
- **Simulação:** “Tesouro Selic é um título público de baixo risco que acompanha a taxa Selic. Ele é muito usado para reserva de emergência.”
<img width="831" height="837" alt="image" src="https://github.com/user-attachments/assets/a3541b77-da87-4ee4-ac01-19f9282faf7d" />


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
