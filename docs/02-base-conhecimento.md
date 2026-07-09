# Base de Conhecimento

> [!TIP]
> **Prompt usado para esta etapa:**
> 
> Organize a base de conhecimento do agente "FinanEduc" usando os 4 arquivos em anexo. Explique pra que serve cada arquivo e monte um exemplo de contexto formatado que será enviado pro LLM. Preencha o template abaixo.
>
> [cole ou anexe o template `02-base-conhecimento.md` pra contexto]


## 🎯 Objetivo da Base de Conhecimento

A base de conhecimento do **FinanEduc** foi construída para permitir que o agente:

- Analise o **fluxo de caixa real** do usuário  
- Entenda padrões de gastos, entradas e comportamento financeiro  
- Personalize explicações conforme perfil, metas e preferências  
- Ensine organização financeira de forma simples e didática  
- Forneça continuidade no atendimento com base no histórico  
- **Sem recomendar investimentos** — apenas educação e controle financeiro  

Com a expansão dos dados, o FinanEduc agora possui uma visão **mais completa**, permitindo análises mais inteligentes e explicações mais contextualizadas.

---

# 📁 Dados Utilizados 

| Arquivo | Formato | Para que serve no FinanEduc? |
|---------|---------|------------------------------|
| `transacoes.csv` | CSV | Análise completa do fluxo de caixa, incluindo vencimentos, recorrência, saldo após cada transação e classificação fixo/variável. |
| `produtos_financeiros.json` | JSON | Catálogo educacional com complexidade, contexto de explicação e observações didáticas. |
| `perfil_investidor.json` | JSON | Perfil completo do usuário, incluindo comportamento financeiro, preferências de aprendizado, metas operacionais e dívidas. |
| `historico_atendimento.csv` | CSV | Histórico detalhado com satisfação, tempo de atendimento, tags de aprendizado e nível de entendimento. |

---

# 🔧 Sobre os Dados

## ✔️ 1. **Fluxo de Caixa**
O arquivo `transacoes.csv` inclui:

- vencimento das contas  
- recorrência (mensal, semanal, eventual)  
- classificação fixo/variável  
- saldo após cada transação  
- visão temporal mais precisa  

Isso permite ao FinanEduc:

- ensinar organização mensal  
- identificar gargalos financeiros  
- explicar impacto de gastos fixos vs variáveis  
- prever fluxo de caixa futuro  

---

## ✔️ 2. **Perfil Financeiro **
O arquivo `perfil_investidor.json` inclui:

- saldo atual da conta  
- nível de organização financeira  
- comportamento financeiro (atrasos, impulsividade, controle)  
- preferências de aprendizado  
- metas operacionais (curto prazo)  
- dívidas detalhadas  

Isso permite ao agente:

- adaptar o tom e a didática  
- explicar conceitos conforme o estilo do usuário  
- ensinar rotinas financeiras  
- contextualizar explicações com base em dificuldades reais  

---

## ✔️ 3. **Produtos Financeiros com Contexto Educacional**
O arquivo `produtos_financeiros.json` inclui:

- complexidade do produto  
- quando explicar  
- observações didáticas  
- exemplos práticos  

Isso permite ao FinanEduc:

- ensinar apenas quando necessário  
- evitar sobrecarga de informação  
- reforçar que não recomenda investimentos  

---

## ✔️ 4. **Histórico de Atendimento Inteligente**
O arquivo `historico_atendimento.csv` inclui:

- satisfação do usuário  
- tempo de atendimento  
- tags de aprendizado  
- nível de entendimento  

Isso permite ao agente:

- evitar repetição  
- reforçar temas não compreendidos  
- manter continuidade natural  
- adaptar explicações conforme histórico  

---

# 🧩 Estratégia de Integração

## Como os dados são carregados?

```python
import pandas as pd
import json

perfil = json.load(open('./data/perfil_investidor.json'))
transacoes = pd.read_csv('./data/transacoes.csv')
historico = pd.read_csv('./data/historico_atendimento.csv')
produtos = json.load(open('./data/produtos_financeiros.json'))
```

## Como os dados são usados no prompt?

O FinanEduc utiliza os dados de forma **contextual**, sempre com foco em:

- explicar fluxo de caixa  
- ensinar organização financeira  
- mostrar exemplos práticos  
- reforçar limites éticos  
- adaptar explicações ao perfil e comportamento  

Os dados podem ser enviados no **system prompt** ou como **contexto dinâmico**.

---

# 📦 Dados Originais

### Trecho de `transacoes.csv`
> “2025-10-01,Salário,receita,5000.00,entrada,fixo,2025-10-01,mensal,5000.00”  
> “2025-10-02,Aluguel,moradia,1200.00,saida,fixo,2025-10-05,mensal,3800.00”

### Trecho de `produtos_financeiros.json`
> “complexidade”: “baixa”, “quando_explicar”: “Quando o usuário perguntar sobre segurança ou liquidez”  
> “observacao_didatica”: “Explicar o que é CDI e liquidez diária”

### Trecho de `perfil_investidor.json`
> “preferencias_aprendizado”: { "formato": "explicações curtas e diretas" }  
> “dividas”: [{ "tipo": "cartao_credito", "valor": 1200.00 }]

### Trecho de `historico_atendimento.csv`
> “satisfacao: 4”, “tags: renda_fixa, liquidez”, “entendimento_usuario: sim”

---

# 🧠 Exemplo de Contexto Montado 
```
CLIENTE:
- Nome: João Silva
- Idade: 32
- Profissão: Analista de Sistemas
- Renda mensal: R$ 5.000
- Saldo atual: R$ 2.511,10
- Nível de organização: Intermediário
- Preferências: Explicações curtas, gosta de exemplos
- Comportamento: Gastos impulsivos moderados, sem atrasos

METAS:
- Reserva de emergência: R$ 10.000 / R$ 15.000
- Entrada do apartamento: R$ 50.000 (2027-12)
- Metas operacionais: Reduzir gastos variáveis em 10%

FLUXO DE CAIXA (Outubro/2025):
- Entradas: R$ 5.000
- Saídas totais: R$ 2.488,90
- Saldo: R$ 2.511,10

GASTOS POR CATEGORIA:
- Moradia: R$ 1.380 (fixo)
- Alimentação: R$ 570 (variável)
- Transporte: R$ 295 (variável)
- Saúde: R$ 188 (misto)
- Lazer: R$ 55,90 (fixo)

DÍVIDAS:
- Cartão de crédito: R$ 1.200, juros 12% ao mês

HISTÓRICO DE ATENDIMENTO:
- Temas já explicados: Tesouro Selic, CDB, metas financeiras
- Satisfação média: 4.6
- Entendimento: Alto

PRODUTOS PARA ENSINO (somente explicação):
- Tesouro Selic (complexidade baixa)
- CDB Liquidez Diária (complexidade baixa)
- LCI/LCA (complexidade média)
- Fundo Multimercado (complexidade alta)
- Fundo de Ações (complexidade alta)

REGRAS DO AGENTE:
- Não recomenda investimentos
- Foca em fluxo de caixa, contas a pagar e recebimentos
- Tom informal e didático
```

---
- O system prompt final do agente FinanEduc  

Só me avisar.
