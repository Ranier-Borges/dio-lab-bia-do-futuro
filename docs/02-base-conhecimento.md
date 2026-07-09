# Base de Conhecimento – **FinanEduc**

> [!TIP]
> **Prompt usado para esta etapa:**
> 
> Organize a base de conhecimento do agente "Edu" usando os 4 arquivos em anexo. Explique pra que serve cada arquivo e monte um exemplo de contexto formatado que será enviado pro LLM. Preencha o template abaixo.
>
> [cole ou anexe o template `02-base-conhecimento.md` para contexto

## 🎯 Objetivo da Base de Conhecimento

A base de conhecimento do **FinanEduc** foi construída para permitir que o agente:

- Entenda o **fluxo de caixa real** do usuário  
- Analise entradas, saídas e categorias de gastos  
- Personalize explicações conforme o perfil financeiro  
- Utilize o histórico para manter continuidade no atendimento  
- Ensine conceitos de forma simples, informal e didática  
- **Sem recomendar investimentos** — apenas educação e organização financeira  

---

## 📁 Dados Utilizados

| Arquivo | Formato | Para que serve no FinanEduc? |
|---------|---------|------------------------------|
| `transacoes.csv` | CSV | Base principal para análise de fluxo de caixa: entradas, saídas, categorias e comportamento financeiro mensal. |
| `produtos_financeiros.json` | JSON | Catálogo de produtos financeiros **somente para fins educativos** — o agente explica conceitos, mas não recomenda nenhum produto. |
| `perfil_investidor.json` | JSON | Permite personalizar explicações conforme o perfil, metas e situação financeira do usuário. |
| `historico_atendimento.csv` | CSV | Ajuda o agente a manter continuidade, lembrando temas já explicados e evitando repetição desnecessária. |

---

## 🔧 Melhorias Implementadas

### ✔️ Reorganização por Função Educacional
Os dados foram agrupados por **função pedagógica**, facilitando prompts mais eficientes.

### ✔️ Criação de Blocos de Contexto
Cada arquivo foi transformado em um bloco pronto para ser injetado no LLM.

### ✔️ Padronização das Categorias
As categorias do fluxo de caixa foram padronizadas:

- moradia  
- alimentação  
- transporte  
- saúde  
- lazer  
- receita  

### ✔️ Indicadores Financeiros Derivados
O agente consegue calcular:

- total de entradas  
- total de saídas  
- saldo do mês  
- gastos por categoria  
- percentual de cada categoria  

### ✔️ Contexto Sintético
Criação de um contexto resumido e otimizado para consumo de tokens.

---

## 🧩 Estratégia de Integração

### Como os dados são carregados?

```python
import pandas as pd
import json

perfil = json.load(open('./data/perfil_investidor.json'))
transacoes = pd.read_csv('./data/transacoes.csv')
historico = pd.read_csv('./data/historico_atendimento.csv')
produtos = json.load(open('./data/produtos_financeiros.json'))
```

### Como os dados são usados no prompt?

O FinanEduc utiliza os dados de forma **contextual**, sempre com foco em:

- explicar fluxo de caixa  
- ensinar organização financeira  
- mostrar exemplos práticos  
- reforçar limites éticos  

Os dados podem ser enviados no **system prompt** ou como **contexto dinâmico**.

---

## 📦 Dados Originais (com citações obrigatórias)

### Trecho de `transacoes.csv`
> “2025-10-01,Salário,receita,5000.00,entrada”  
> “2025-10-02,Aluguel,moradia,1200.00,saida”

### Trecho de `produtos_financeiros.json`
> “Tesouro Selic”, “categoria”: “renda_fixa”, “risco”: “baixo”  
> “CDB Liquidez Diária”, “rentabilidade”: “102% do CDI”

### Trecho de `perfil_investidor.json`
> “nome”: “João Silva”, “renda_mensal”: 5000.00  
> “objetivo_principal”: “Construir reserva de emergência”

### Trecho de `historico_atendimento.csv`
> “2025-10-01,chat,Tesouro Selic,Cliente pediu explicação…”  
> “2025-10-12,chat,Metas financeiras,Cliente acompanhou…”

---

## 🧠 Exemplo de Contexto Montado

```
CLIENTE:
- Nome: João Silva
- Idade: 32
- Profissão: Analista de Sistemas
- Renda mensal: R$ 5.000
- Objetivo principal: Construir reserva de emergência
- Reserva atual: R$ 10.000 (meta: R$ 15.000)
- Aceita risco: Não

FLUXO DE CAIXA (Outubro/2025):
- Entradas: R$ 5.000
- Saídas totais: R$ 2.488,90
- Saldo: R$ 2.511,10

GASTOS POR CATEGORIA:
- Moradia: R$ 1.380
- Alimentação: R$ 570
- Transporte: R$ 295
- Saúde: R$ 188
- Lazer: R$ 55,90

HISTÓRICO DE ATENDIMENTO:
- Já aprendeu sobre: Tesouro Selic, CDB, metas financeiras
- Último atendimento: Atualização cadastral (25/10)

PRODUTOS PARA ENSINO (somente explicação):
- Tesouro Selic (renda fixa, risco baixo)
- CDB Liquidez Diária (renda fixa, risco baixo)
- LCI/LCA (renda fixa, risco baixo)
- Fundo Multimercado (renda variável, risco médio)
- Fundo de Ações (renda variável, risco alto)

REGRAS DO AGENTE:
- Não recomenda investimentos
- Foca em fluxo de caixa, contas a pagar e recebimentos
- Tom informal e didático
```

---
