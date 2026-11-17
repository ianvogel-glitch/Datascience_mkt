# 📊 Consumo Digital na Europa: Comportamento de Compra pela Internet

> **Analisar o comportamento de compra online dos consumidores europeus, identificando padrões e tendências que possam contribuir para estratégias de Marketing mais eficazes.**

---

## 📌 Visão Geral do Projeto (Metodologia CRISP-DM)


Este projeto tem como foco analisar o comportamento de compra pela internet na Europa, procurando compreender como esse hábito se manifesta em diferentes países e grupos de consumidores. A partir de dados públicos do Eurostat, serão exploradas características demográficas e tendências relacionadas às compras online. A análise pretende identificar padrões de consumo e transformar os dados em informações relevantes para o Marketing, contribuindo para uma melhor compreensão do consumidor digital e para o desenvolvimento de estratégias mais eficazes.
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
### Problema de negócio
O crescimento das compras pela internet transformou a forma como os consumidores pesquisam, escolhem e adquirem produtos e serviços. No entanto, os hábitos de compra online não são iguais entre todos os consumidores e podem variar de acordo com o país e as características demográficas da população. Para o Marketing, compreender essas diferenças é importante para identificar oportunidades e desenvolver estratégias mais adequadas aos diferentes perfis de consumidores.

### Objetivo do projeto
Analisar os hábitos de compra online na Europa, identificando padrões e diferenças entre países e grupos de consumidores, com o objetivo de compreender melhor o comportamento do consumidor digital.

### Solução proposta
Utilizar dados públicos do Eurostat e técnicas de análise de dados para explorar o comportamento de compra pela internet. Através da organização, visualização e análise dos dados, pretende-se identificar tendências e padrões que possam gerar informações úteis para a tomada de decisões e o planeamento de estratégias de Marketing.

### 2. Entendimento dos Dados

### Fontes
Os dados foram obtidos através do **Eurostat**, a plataforma oficial de estatísticas da União Europeia. O ficheiro utilizado contém 558.750 registos e 11 colunas, com informações sobre compras online em 40 referências geográficas, entre 2020 e 2025. Descarregar o ficheiro Eurostat — isoc_ec_ib20_linear.csv.gz

### Análise Exploratória (EDA)
A base de dados apresenta diferentes indicadores sobre compras pela internet, frequência de utilização e características dos grupos populacionais. Nesta fase, pretende-se conhecer a estrutura dos dados, analisar os valores disponíveis e identificar possíveis dados em falta, preparando a base para as próximas etapas do projeto.

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
