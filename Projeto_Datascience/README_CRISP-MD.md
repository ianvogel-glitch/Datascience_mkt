# 📊 [Nome do Seu Projeto de Dados]

> **[Uma frase curta e direta explicando o impacto do projeto. Ex: Modelo preditivo de Churn integrado a um painel analítico para redução de perdas de clientes.]**

---

## 📌 Visão Geral do Projeto (Metodologia CRISP-DM)

Este projeto tem como objetivo analisar os padrões climáticos dos Estados Unidos por meio de técnicas de Ciência de Dados, utilizando dados históricos e modelos preditivos para identificar tendências e estimar possíveis mudanças nas condições climáticas. A partir dessas análises, busca-se compreender como os cenários climáticos podem impactar diferentes setores econômicos e gerar oportunidades ou desafios para o marketing.

O desenvolvimento seguirá a metodologia **CRISP-DM**, estruturando o trabalho desde a compreensão do problema e dos dados até a modelagem, avaliação e apresentação dos resultados. Além disso, serão utilizadas ferramentas de **Business Intelligence (BI)** para transformar os dados e as previsões em visualizações que facilitem a interpretação dos cenários e apoiem a tomada de decisões estratégicas.

```text
       ┌────────────────────────────────────────────────────────┐
       │                                                        │
       ▼                                                        │
┌──────────────┐      ┌──────────────┐      ┌──────────────┐    │
│ 1. Entendimento     │ 2. Entendimento     │ 3. Preparação│    │
│    do Negócio│ ───> │    dos Dados │ ───> │    dos Dados │    │
└──────────────┘      └──────────────┘      └──────────────┘    │
                                                   │            │
                                                   ▼            │
┌──────────────┐      ┌──────────────┐      ┌──────────────┐    │
│ 6. Implantação      │ 5. Avaliação │ <─── │ 4. Modelagem │    │
│   (BI e Prod)│ <─── │  (Métricas)  │      │  (Algoritmos)│    │
└──────────────┘      └──────────────┘      └──────────────┘    │
       │                                                        │
       └────────────────────────────────────────────────────────┘
```

---

## 🛠️ Ciclo de Vida do Projeto (Fases do CRISP-DM)

### 1. Entendimento do Negócio
* **Problema de Negócio:** [Ex: O time de retenção sofre com surpresas na saída de clientes recorrentes, sem tempo hábil para ações preventivas.]
* **Objetivo:** [Ex: Prever com pelo menos 30 dias de antecedência quais clientes têm alta propensão ao cancelamento.]
* **Solução Proposta:** Um modelo preditivo de Machine Learning integrado a um painel de BI atualizado diariamente para tomadas de decisão.

### 2. Entendimento dos Dados
* **Fontes:** Dados extraídos do CRM ([Nome do sistema]) e do banco de transações ERP.
* **Análise Exploratória (EDA):** Identificação de distribuições, valores nulos e correlações iniciais. *(Os notebooks desta fase estão localizados em `notebooks/1_eda/`)*.

### 3. Preparação dos Dados
* **Limpeza e Tratamento:** Tratamento de dados faltantes, remoção de *outliers* e unificação de formatos de data.
* **Engenharia de Recursos (Feature Engineering):** Criação de novas variáveis como tempo de contrato, frequência de uso recente e ticket médio histórico.
* **Modelagem Dimensional (BI):** Estruturação das tabelas em formato **Star Schema** (Tabelas Fato e Dimensão) prontas para o consumo no BI.

### 4. Modelagem
* **Algoritmos Testados:** Regressão Logística, Random Forest e [XGBoost / LightGBM].
* **Abordagem:** Treinamento supervisionado com divisão da base em treino, validação e teste (proporção 70/15/15).

### 5. Avaliação
* **Métricas do Modelo:** O modelo final alcançou uma **Acurácia de [X]%** e um **Recall de [Y]%** (foco em minimizar os falsos negativos).
* **Métricas de BI / KPIs de Negócio:** 
  * **[KPI 1, ex: Taxa de Churn]:** Taxa geral de cancelamento.
  * **[KPI 2, ex: Receita em Risco (MRR)]:** O volume financeiro mapeado nas faixas de alta propensão do modelo.

### 6. Implantação
* **Pipeline em Produção:** O script de predição roda de forma automatizada [ex: via Airflow / Cron] gerando novos scores de risco todas as noites.
* **Camada de Visualização (BI):** Os resultados são disponibilizados em um painel interativo no **[Power BI / Tableau / Looker Studio]** com duas visões principais:
  1. *Visão Executiva:* Tendências de mercado e comportamento macro de churn.
  2. *Visão Operacional:* Tabela dinâmica com a lista de clientes ordenada por maior risco, permitindo ações imediatas.

---

## 📁 Estrutura de Pastas (Mapeada pelo CRISP-DM)

```text
├── docs/                  # 1. Negócio: Dicionário de dados, atas e escopo do projeto
├── notebooks/             # 2. Dados: Jupyter Notebooks de Análise Exploratória (EDA)
│   ├── 1_eda/
│   └── 2_testes_modelagem/
├── src/                   # 3, 4 e 6. Scripts de Produção
│   ├── data_prep.py       # Preparação e ETL
│   ├── train_model.py     # Script de treinamento e tunagem
│   └── predict.py         # Script de inferência diária para produção
├── bi/                    # 6. Implantação: Arquivos e consultas SQL do Dashboard (.pbix, .twbx)
├── requirements.txt       # Bibliotecas e dependências do projeto
└── README.md              # Este arquivo
```
*Para abrir e editar a camada de BI, abra o arquivo localizado em `bi/[nome_do_painel].pbix` utilizando o [Power BI Desktop].*

---

## 👥 Autores e Contato

* **[Ian Roscoe Vogel]** - *Cientista de Dados / Analista de BI* - [Seu LinkedIn](https://linkedin.com)
