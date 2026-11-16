# 📊 nálise Comparativa de Indicadores Econômicos, Sociais e Ambientais entre Países

> **]Uma análise orientada por dados para identificar padrões e relações entre desenvolvimento econômico, condições sociais e sustentabilidade ambiental em diferentes países e como desenvolver algo no marketing com essa análise.**

---

## 📌 Visão Geral do Projeto (Metodologia CRISP-DM)


Este projeto tem como objetivo analisar como as populações de diferentes países percebem e reagem às mudanças climáticas, investigando possíveis impactos na preocupação ambiental e nos hábitos de consumo. Por meio de técnicas de Ciência de Dados, serão identificados padrões e diferenças entre países.

A partir dos resultados, busca-se compreender como essas mudanças de comportamento podem influenciar o mercado e contribuir para o desenvolvimento de estratégias de Marketing.

O trabalho seguirá a metodologia **CRISP-DM**, utilizando Python para coleta, tratamento, análise e visualização dos dados.

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
* **Problema de Negócio:** As mudanças climáticas podem influenciar a percepção ambiental e os hábitos de consumo da população. Entretanto, essas reações podem variar entre países, tornando importante compreender como o comportamento dos consumidores se modifica diante das questões climáticas e quais desafios e oportunidades isso representa para as estratégias de Marketing.
* **Objetivo:** Analisar como as populações de diferentes países percebem e reagem às mudanças climáticas, identificando possíveis relações com a preocupação ambiental e os hábitos de consumo. A partir dos resultados, buscar compreender como essas diferenças podem influenciar o comportamento dos consumidores e contribuir para o desenvolvimento de estratégias de Marketing.
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
