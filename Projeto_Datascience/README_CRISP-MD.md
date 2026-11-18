# 📊 Consumo Digital na Europa: Tendências, Desigualdades e Oportunidades para o Marketing Digital

> **Objetivo geral:** Analisar a evolução das compras online em países europeus entre 2020 e 2025, investigando diferenças geográficas e demográficas no comportamento dos consumidores, a fim de identificar oportunidades para estratégias de Marketing Digital mais eficazes e inclusivas.

---

## 📌 Visão Geral do Projeto

O comércio eletrônico tem transformado os hábitos de consumo e ampliado as possibilidades de atuação das empresas no ambiente digital. Entretanto, a participação nas compras online não ocorre necessariamente da mesma maneira entre países e grupos de consumidores.

Este projeto utiliza dados públicos do **Eurostat**, referentes ao período de **2020 a 2025**, para investigar tendências de consumo digital em países europeus.

A análise busca compreender como a participação nas compras online evoluiu ao longo do tempo, identificar diferenças entre países e faixas etárias e examinar a frequência das compras realizadas pela internet.

O projeto foi desenvolvido em Python, no Google Colab, utilizando a metodologia **CRISP-DM (Cross-Industry Standard Process for Data Mining)**.

Além da análise estatística, são discutidas possíveis aplicações dos resultados em estratégias de Marketing Digital, incluindo oportunidades de segmentação, relacionamento com consumidores e inclusão digital.

### Perguntas de investigação

1. Como a participação nas compras online evoluiu entre 2020 e 2025?
2. Quais países apresentaram maiores e menores variações nesse período?
3. Como o comportamento de compra online varia entre diferentes faixas etárias?
4. Como se distribui a frequência de compras entre os consumidores digitais?
5. De que maneira os resultados podem contribuir para estratégias de Marketing Digital mais eficazes e inclusivas?

### Tecnologias utilizadas

- **Python:** linguagem utilizada para o tratamento e a análise dos dados.
- **Pandas:** manipulação, limpeza, organização e agregação dos dados.
- **Matplotlib:** construção de gráficos e visualizações.
- **Scikit-learn:** implementação e avaliação do modelo de regressão linear.
- **Google Colab:** ambiente de desenvolvimento e execução do projeto.
- **GitHub:** documentação e apresentação do projeto.

---

# 🛠️ Desenvolvimento do Projeto — Metodologia CRISP-DM

## 1. Entendimento do Negócio (Business Understanding)

### Problema de negócio

O crescimento do comércio eletrônico amplia as oportunidades para empresas que desejam alcançar consumidores por meio de canais digitais.

Entretanto, os hábitos de compra online variam entre países e grupos demográficos. Essas diferenças podem influenciar a escolha dos públicos, dos canais de comunicação e das estratégias de relacionamento utilizadas pelas organizações.

Para o Marketing Digital, compreender tais diferenças é importante para evitar estratégias excessivamente generalizadas e identificar oportunidades de atuação em mercados e segmentos específicos.

### Objetivo do projeto

Investigar a evolução e as diferenças no comportamento de compra online em países europeus, utilizando dados estatísticos para apoiar decisões de segmentação e planejamento de Marketing Digital.

### Objetivos específicos

- Analisar a evolução das compras online entre 2020 e 2025.
- Comparar o crescimento da participação nas compras online entre países.
- Identificar diferenças de participação entre faixas etárias.
- Investigar a frequência de compras entre consumidores digitais.
- Aplicar um modelo estatístico para representar a tendência temporal observada.
- Discutir oportunidades de Marketing Digital e possíveis contribuições para a inclusão digital.

### Solução proposta

Utilizar dados públicos do Eurostat, técnicas de análise exploratória, estatística descritiva, visualização de dados e regressão linear simples.

Os resultados serão interpretados sob a perspectiva do Marketing Digital, considerando tanto oportunidades de negócio quanto limitações dos dados e possíveis impactos sociais.

---

## 2. Entendimento dos Dados (Data Understanding)

### Fonte dos dados

Os dados foram obtidos no **Eurostat**, órgão responsável pela divulgação de estatísticas oficiais da União Europeia.

**Dataset:** `isoc_ec_ib20`

**Arquivo utilizado:** `isoc_ec_ib20_linear.csv.gz`

**Período analisado:** 2020 a 2025.

**Fonte:** [Eurostat — Base de dados estatísticos](https://ec.europa.eu/eurostat/data/database)

### Características do conjunto de dados

O arquivo original apresenta:

| Característica | Quantidade |
|---|---:|
| Registros | 558.750 |
| Colunas | 11 |
| Referências geográficas | 40 |
| Indicadores de comportamento digital | 13 |
| Categorias demográficas | 147 |
| Período | 2020–2025 |

As referências geográficas incluem países e agregados regionais.

O conjunto de dados contém **percentuais estatísticos agregados**, e não registros individuais de compras ou transações financeiras.

### Principais variáveis

| Variável | Descrição |
|---|---|
| `geo` | País ou agregado geográfico |
| `TIME_PERIOD` | Ano da observação |
| `ind_type` | Grupo populacional ou demográfico |
| `indic_is` | Indicador relacionado ao comportamento de compra online |
| `unit` | Unidade de medida e população utilizada como referência |
| `OBS_VALUE` | Valor percentual observado |
| `OBS_FLAG` | Informação complementar sobre a qualidade da observação |

### Análise exploratória inicial

Durante a exploração dos dados, foram investigados:

- Estrutura e tipos das variáveis.
- Valores ausentes.
- Existência de registros duplicados.
- Distribuição das informações por país e ano.
- Indicadores disponíveis.
- Categorias demográficas.
- Diferenças entre unidades de medida.

Foram identificados **27.912 registros sem valor em `OBS_VALUE`**, correspondentes a aproximadamente 5% do conjunto original.

Também foi constatado que alguns indicadores apresentam diferentes unidades de medida, exigindo atenção à população utilizada como denominador em cada percentual.

---

## 3. Preparação dos Dados (Data Preparation)

A preparação dos dados teve como objetivo organizar as informações e garantir maior consistência nas comparações.

### Limpeza e tratamento

Foram realizados os seguintes procedimentos:

1. Remoção da coluna `CONF_STATUS`, que não apresentava informações.
2. Exclusão de 27.912 registros sem valor na variável `OBS_VALUE`.
3. Verificação de duplicatas, sem identificação de registros duplicados na base tratada.
4. Preservação da coluna `OBS_FLAG`, que contém informações relacionadas à qualidade dos dados.
5. Remoção das colunas técnicas `DATAFLOW`, `LAST UPDATE` e `freq`, por apresentarem valores constantes.
6. Seleção de indicadores e unidades de medida compatíveis com cada análise.
7. Identificação das localidades com informações disponíveis durante todo o período de 2020 a 2025.
8. Separação dos países individuais dos agregados regionais da União Europeia e da zona do euro.

### Bases utilizadas

| Base | Registros | Finalidade |
|---|---:|---|
| `df` | 558.750 | Conjunto original |
| `df_tratado` | 530.838 | Base limpa para diferentes análises |
| `df_analise` | 221 | Indicador geral de compras online |
| `df_temporal` | 198 | Localidades com cobertura temporal completa |
| `df_paises` | 186 | Comparação de 31 países entre 2020 e 2025 |

As bases `df_idades` e `df_frequencia` também foram criadas para investigar grupos etários e frequência de compras.

### Critérios de seleção

Para a análise temporal e a comparação entre países, foi utilizado o indicador:

**Last online purchase: in the last 3 months**

A unidade selecionada foi:

**Percentage of individuals**

Esse recorte representa o percentual de indivíduos cuja última compra online ocorreu nos três meses anteriores.

Para a análise da frequência de compras, foi utilizada outra unidade:

**Percentage of individuals who purchased online in the last 3 months**

Essa distinção é necessária porque os indicadores possuem populações de referência diferentes.

A seleção dos 31 países com dados completos permitiu acompanhar o mesmo conjunto de localidades ao longo dos seis anos.

---

## 4. Modelagem (Modeling)

### Técnica utilizada

Foi aplicada uma **regressão linear simples**, utilizando a biblioteca Scikit-learn.

O objetivo foi representar estatisticamente a tendência temporal da média de participação nas compras online entre os 31 países analisados.

### Variáveis do modelo

- **Variável independente (X):** ano, de 2020 a 2025.
- **Variável dependente (y):** média anual dos percentuais de participação nas compras online.

A média foi calculada atribuindo o mesmo peso a cada país, independentemente de sua população.

### Resultados da modelagem

| Indicador | Resultado |
|---|---:|
| Variação anual estimada | +2,17 pontos percentuais |
| Coeficiente de determinação (R²) | 0,9251 |

O coeficiente da regressão indica uma tendência linear positiva de aproximadamente **2,17 pontos percentuais por ano**.

O R² de **0,9251** indica que a reta ajustada representa aproximadamente **92,51% da variação observada nas seis médias anuais**.

### Limitações da modelagem

O modelo foi ajustado com apenas seis observações anuais agregadas.

Embora apresente bom ajuste aos valores históricos, não considera diferenças individuais entre países, características demográficas ou fatores externos que possam influenciar as compras online.

Por isso, a regressão foi utilizada como ferramenta **exploratória e descritiva**, sem finalidade de previsão precisa ou identificação de relações causais.

---

## 5. Avaliação (Evaluation)

A avaliação considerou o ajuste estatístico do modelo e sua utilidade para os objetivos do projeto.

### Métrica utilizada

Foi calculado o **Erro Absoluto Médio (MAE)**, por meio da biblioteca Scikit-learn.

| Métrica | Resultado |
|---|---:|
| R² | 0,9251 |
| MAE | 0,76 ponto percentual |

O MAE de **0,76 ponto percentual** indica que a diferença absoluta média entre os valores observados e os estimados foi relativamente pequena.

Entretanto, a avaliação foi realizada com os mesmos seis valores utilizados no ajuste da regressão.

Portanto, o resultado representa o **erro de ajuste histórico**, não uma avaliação independente da capacidade preditiva do modelo.

### Avaliação em relação ao objetivo de negócio

A regressão contribuiu para representar a tendência geral de crescimento das compras online.

Contudo, as análises por país, faixa etária e frequência de compra são fundamentais para interpretar diferenças entre mercados e consumidores.

Assim, o modelo estatístico complementa a análise exploratória, mas não substitui a investigação dos diferentes segmentos.

---

## 📈 Principais Resultados das Análises

### 1. Evolução temporal das compras online

A média dos percentuais de participação nas compras online entre os 31 países apresentou os seguintes resultados:

| Ano | Média entre países |
|---|---:|
| 2020 | 47,73% |
| 2021 | 53,18% |
| 2022 | 52,37% |
| 2023 | 55,23% |
| 2024 | 57,73% |
| 2025 | 59,62% |

Entre 2020 e 2025, foi observado um aumento de **11,89 pontos percentuais**.

Apesar de uma pequena redução entre 2021 e 2022, a tendência geral do período foi de crescimento.

Esses valores representam médias simples dos percentuais dos países, e não uma taxa populacional ponderada para toda a Europa.

### 2. Comparação entre países

A análise identificou diferenças importantes na evolução das compras online entre 2020 e 2025.

**Maiores crescimentos observados:**

| País | Variação |
|---|---:|
| Chipre | +27,10 pp |
| Grécia | +24,57 pp |
| Irlanda | +23,42 pp |
| Sérvia | +21,51 pp |
| Romênia | +19,42 pp |

**Menores variações observadas:**

| País | Variação |
|---|---:|
| Alemanha | −4,62 pp |
| Luxemburgo | +0,17 pp |
| Eslovênia | +1,60 pp |
| Bélgica | +2,01 pp |
| Dinamarca | +2,57 pp |

Os resultados demonstram que o crescimento das compras online não ocorreu de maneira uniforme.

É importante destacar que países com menor crescimento podem apresentar níveis elevados de participação desde o início do período.

Por exemplo, a Dinamarca já apresentava 79,36% em 2020, alcançando 81,93% em 2025.

Dessa forma, o nível de participação e a velocidade de crescimento devem ser considerados separadamente.

### 3. Diferenças entre faixas etárias

A análise de 2025 considerou seis faixas etárias, com dados disponíveis para os 31 países.

| Faixa etária | Média de participação |
|---|---:|
| 16–24 anos | 70,08% |
| 25–34 anos | 75,87% |
| 35–44 anos | 72,17% |
| 45–54 anos | 62,37% |
| 55–64 anos | 46,30% |
| 65–74 anos | 30,03% |

A maior média foi observada entre indivíduos de **25 a 34 anos**, enquanto a menor ocorreu no grupo de **65 a 74 anos**.

A diferença entre esses grupos foi de **45,84 pontos percentuais**.

Esse resultado evidencia diferenças relevantes na participação nas compras online conforme a idade.

Entretanto, os dados não permitem determinar isoladamente as causas dessas diferenças.

### 4. Frequência de compras online

A análise da frequência considerou consumidores que realizaram compras pela internet nos últimos três meses, em 2025.

| Frequência de compra | Média entre países |
|---|---:|
| 1 ou 2 compras | 32,88% |
| 3 a 5 compras | 34,54% |
| 6 compras ou mais | 32,43% |

A distribuição apresentou relativa proximidade entre as três categorias.

O grupo de **3 a 5 compras** apresentou a maior média, com 34,54%, mas sem uma diferença expressiva em relação aos demais.

Esses resultados indicam diferentes intensidades de compra entre os consumidores digitais.

---

## 💼 Recomendações para o Marketing Digital

As análises realizadas permitem propor algumas orientações para estratégias de Marketing Digital.

### Segmentação por mercado

Os países apresentam diferentes níveis de participação e ritmos de crescimento das compras online.

Assim, estratégias de Marketing podem considerar tanto mercados com participação elevada quanto aqueles em que o comércio eletrônico ainda apresenta menor alcance.

A escolha de campanhas, canais e investimentos deve ser complementada por informações específicas sobre cada mercado.

### Segmentação por faixa etária

As diferenças observadas entre os grupos etários sugerem a importância de adaptar a comunicação aos diferentes perfis de consumidores.

Ações de Marketing podem considerar preferências de canais, clareza das informações, facilidade de navegação e necessidades específicas dos públicos.

Entretanto, essas características precisam ser investigadas diretamente, pois os dados analisados não identificam as causas da menor participação de determinados grupos.

### Relacionamento e fidelização

A distribuição da frequência de compras indica a presença de consumidores com diferentes níveis de atividade no comércio eletrônico.

Essa informação pode orientar propostas de relacionamento e fidelização, desde que as empresas utilizem dados próprios para identificar o comportamento de seus clientes.

O conjunto de dados do Eurostat não permite identificar consumidores individualmente nem medir o desempenho de campanhas específicas.

---

## 🌍 Impacto Social e Inovação na Estratégia de Marketing Digital

### 1. Necessidade social identificada

Uma questão relevante para o comércio eletrônico é a possibilidade de diferenças na participação digital entre grupos de consumidores.

Na análise dos dados do Eurostat referentes a 2025, a média de participação nas compras online foi de **75,87% entre pessoas de 25 a 34 anos**, enquanto o grupo de **65 a 74 anos apresentou 30,03%**.

A diferença de 45,84 pontos percentuais demonstra uma desigualdade de participação entre esses grupos no conjunto dos países analisados.

Esse resultado não comprova que a diferença seja causada por problemas de acessibilidade, falta de conhecimento tecnológico ou dificuldades de navegação.

Entretanto, justifica investigar se determinadas características dos canais digitais podem representar barreiras para parte dos consumidores.

### 2. Públicos afetados, benefícios e riscos

A proposta considera dois públicos principais:

**Pessoas de 65 a 74 anos:** grupo que apresentou menor participação média nas compras online e que poderá ser incluído em pesquisas para identificar possíveis dificuldades de compreensão, navegação e confiança.

**Pessoas de 25 a 34 anos:** grupo que apresentou maior participação média e que poderá servir como referência comparativa para investigar diferenças na experiência de compra.

A proposta também poderá beneficiar consumidores de outras idades que encontrem dificuldades para compreender informações ou utilizar plataformas digitais.

**Benefício social esperado:** facilitar o acesso a informações de compra e tornar a experiência digital mais clara e acessível.

**Risco identificado:** a segmentação por idade pode produzir estereótipos ou excluir consumidores de determinados conteúdos e oportunidades.

**Medida de redução do risco:** utilizar linguagem inclusiva, oferecer recursos de acessibilidade a todos os públicos e evitar presumir capacidades ou dificuldades individuais apenas com base na idade.

Também deverão ser adotadas medidas de proteção de dados pessoais durante eventuais pesquisas ou testes com consumidores.

### 3. Fundamentação com dados

**Fonte:** Eurostat, conjunto de dados `isoc_ec_ib20`.

**Período:** 2025, para a comparação entre faixas etárias.

**Público:** indivíduos de 16 a 74 anos, organizados em seis faixas etárias, nos 31 países selecionados.

**Indicador:** percentual de indivíduos cuja última compra online ocorreu nos três meses anteriores.

Os resultados demonstraram diferenças expressivas entre as faixas etárias, com menor participação média nos grupos de maior idade.

Entretanto, os dados são agregados e não permitem identificar diretamente dificuldades individuais, motivações de compra ou barreiras de acessibilidade.

Portanto, a necessidade de melhorar a experiência digital será tratada como uma hipótese de intervenção, que deverá ser investigada por meio de testes e consultas aos públicos envolvidos.

### 4. Proposta de inovação social

**Ação proposta: Comunicação Digital Acessível para Compras Online**

Propõe-se desenvolver uma iniciativa de melhoria da comunicação digital em páginas de produtos, anúncios e orientações de compra de uma empresa de comércio eletrônico.

A proposta contempla:

- Revisão de textos para utilizar linguagem clara e objetiva.
- Orientações passo a passo sobre como realizar compras.
- Informações visíveis sobre pagamento, entrega, trocas e devoluções.
- Melhoria da legibilidade e da organização visual das páginas.
- Testes de compreensão e navegação com consumidores de diferentes faixas etárias.
- Disponibilização de canais de atendimento acessíveis para esclarecimento de dúvidas.

**Canais:** site de comércio eletrônico, páginas de produtos, e-mail e conteúdos informativos em redes sociais.

**Recursos necessários:** equipe de Marketing, apoio de profissionais de experiência do usuário, revisão de conteúdo, ferramentas de pesquisa e participantes voluntários para testes.

**Objetivo de negócio:** melhorar a experiência de compra e reduzir dificuldades que possam prejudicar a conclusão de compras.

**Benefício social esperado:** ampliar a clareza das informações e facilitar o uso dos canais digitais por diferentes públicos.

A iniciativa constitui uma **proposta**, não uma campanha já executada.

### 5. Indicadores de acompanhamento

Para avaliar a contribuição da ação, são propostos quatro indicadores.

| Indicador | Como medir | Quando medir |
|---|---|---|
| Conteúdos revisados para acessibilidade (%) | Dividir a quantidade de conteúdos revisados pelo total de conteúdos selecionados e multiplicar por 100 | Antes e após a revisão |
| Compreensão das informações de compra (%) | Aplicar perguntas sobre pagamento, entrega e devolução; calcular o percentual de participantes que responderem corretamente | Em testes com as versões original e revisada |
| Conclusão de compra simulada sem ajuda (%) | Dividir o número de participantes que concluírem a tarefa sem ajuda pelo total de participantes testados e multiplicar por 100 | Em testes com as duas versões |
| Tempo para concluir a tarefa | Registrar o tempo necessário para concluir uma compra simulada | Em testes com as versões original e revisada |

### Planejamento da avaliação

Antes de implementar a proposta, deverá ser realizada uma medição inicial com a versão atual das páginas e orientações.

Posteriormente, os mesmos procedimentos serão aplicados à versão revisada, buscando utilizar tarefas equivalentes e grupos comparáveis.

Os resultados deverão ser apresentados com o número de participantes, o período de coleta e as limitações da avaliação.

Uma melhoria observada após a intervenção poderá indicar uma contribuição positiva, mas não demonstrará, isoladamente, que todas as mudanças foram causadas pela ação.

**Situação atual:** os indicadores ainda não foram medidos. Seus resultados são esperados e dependerão da implementação e da avaliação da proposta.

---

## 6. Implantação e Comunicação dos Resultados (Deployment)

Nesta etapa, os resultados do projeto são organizados e comunicados para apoiar a interpretação dos dados e possíveis decisões de Marketing Digital.

### Forma de apresentação

O projeto utiliza:

- Notebook no Google Colab com os códigos de preparação, análise e modelagem.
- Tabelas com os principais resultados.
- Gráficos de evolução temporal, comparação entre países, faixas etárias e frequência de compras.
- Visualização da regressão linear.
- Documentação do projeto no GitHub.

### Aplicação dos resultados

As análises podem contribuir para:

- Identificar diferenças de participação no comércio eletrônico entre países.
- Apoiar decisões iniciais de segmentação de mercado.
- Investigar necessidades de comunicação de diferentes faixas etárias.
- Orientar propostas de relacionamento com consumidores.
- Fundamentar iniciativas de comunicação digital mais inclusiva.

**Não foi realizado o desenvolvimento de um sistema de previsão em produção, painel automatizado ou campanha real de Marketing.**

A implantação, neste projeto acadêmico, corresponde à documentação e à apresentação dos resultados e recomendações.

---

## 📝 Considerações Finais

O projeto analisou o comportamento de compra online em países europeus entre 2020 e 2025, utilizando dados públicos do Eurostat e a metodologia CRISP-DM.

Os resultados demonstraram uma tendência geral de crescimento na média de participação nas compras online dos 31 países selecionados, passando de 47,73% em 2020 para 59,62% em 2025.

Entretanto, a comparação entre países revelou diferenças importantes nos ritmos de crescimento. Chipre, Grécia e Irlanda apresentaram avanços expressivos, enquanto a Alemanha registrou redução entre os dois anos analisados.

A análise demográfica também identificou diferenças relevantes entre faixas etárias, especialmente entre os grupos de 25 a 34 anos e de 65 a 74 anos.

A investigação da frequência de compras mostrou uma distribuição relativamente equilibrada entre consumidores com diferentes intensidades de compra.

Na etapa de modelagem, a regressão linear apresentou tendência estimada de crescimento de 2,17 pontos percentuais por ano, com R² de 0,9251 e MAE de 0,76 ponto percentual. Esses resultados indicam bom ajuste histórico, mas não garantem desempenho preditivo futuro.

Sob a perspectiva do Marketing Digital, as descobertas reforçam a importância de considerar diferenças geográficas e demográficas no planejamento de estratégias, evitando abordagens excessivamente generalizadas.

Na dimensão social, a menor participação média nas compras online entre pessoas de 65 a 74 anos motivou uma proposta de comunicação digital mais acessível.

A proposta busca facilitar a compreensão das informações e a realização de tarefas em canais digitais. Entretanto, seus benefícios ainda precisam ser verificados por meio de testes comparativos e indicadores específicos.

Conclui-se que a análise de dados pode contribuir tanto para decisões de negócio quanto para a identificação de oportunidades de inovação social, desde que os resultados sejam interpretados de forma crítica, considerando suas limitações.

---

## ⚠️ Limitações do Projeto

- Os dados representam percentuais agregados, não registros individuais de consumidores.
- As médias entre países não foram ponderadas pelo tamanho da população.
- A comparação temporal foi restrita a 31 países com dados completos entre 2020 e 2025.
- Os resultados não explicam isoladamente as causas das diferenças observadas.
- Os indicadores de qualidade disponibilizados pelo Eurostat foram preservados, mas não foi realizada uma análise específica de sensibilidade às sinalizações.
- A regressão linear foi ajustada com apenas seis médias anuais.
- O modelo não foi validado com dados independentes.
- Não foram coletados dados próprios de campanhas ou experiências de consumidores.
- A ação de inovação social foi proposta, mas ainda não implementada.

---

## 📚 Referências

**EUROSTAT.** Base de dados estatísticos da União Europeia. Conjunto de dados `isoc_ec_ib20`. Disponível em: https://ec.europa.eu/eurostat/data/database.

**CHAPMAN, P. et al.** CRISP-DM 1.0: Step-by-step data mining guide. 2000.

**SCIKIT-LEARN.** Documentação oficial da biblioteca. Disponível em: https://scikit-learn.org/stable/.

**PANDAS.** Documentação oficial da biblioteca. Disponível em: https://pandas.pydata.org/docs/.

**MATPLOTLIB.** Documentação oficial da biblioteca. Disponível em: https://matplotlib.org/stable/.

---

## 👥 Autoria

**Ian Roscoe Vogel**

Projeto acadêmico desenvolvido na área de Ciência de Dados e Marketing Digital.

---

**Fonte dos dados:** Eurostat | **Período:** 2020–2025 | **Metodologia:** CRISP-DM
