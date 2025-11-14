%md

Previsão de Custos de Seguro de Saúde - Projeto de Ciência de Dados
Definição do Problema
O objetivo deste projeto é prever o valor de charges (cobrança) de um seguro de saúde com base em variáveis como idade, sexo, índice de massa corporal (BMI), número de filhos, tabagismo e região.

Trata-se de um problema de regressão supervisionada, onde a variável alvo é contínua (charges). A solução permitirá estimar o custo do seguro para novos clientes, auxiliando na precificação e análise de risco.

python
features = ['age', 'sex', 'bmi', 'children', 'smoker', 'region']
target = 'charges'
Sobre o Projeto
Este projeto representa um pipeline completo de ciência de dados, desenvolvido com rigor metodológico e seguindo as melhores práticas da área. O trabalho abrange desde a análise exploratória até a construção e validação de modelos preditivos, passando por técnicas avançadas de feature engineering, redução dimensional e clustering.

O dataset utilizado contém informações de 1.338 beneficiários de seguro de saúde nos Estados Unidos, incluindo características demográficas, de saúde e geográficas. A análise busca identificar os principais fatores que influenciam os custos de seguro e construir modelos capazes de realizar predições precisas para novos clientes.

Estrutura do Projeto
1. Análise Exploratória de Dados (EDA)
A fase inicial envolveu uma investigação profunda dos dados através de múltiplas perspectivas:

Análise estatística descritiva: Cálculo de medidas de tendência central, dispersão, assimetria e curtose para todas as variáveis numéricas.

Visualizações gráficas: Criação de 15 tipos diferentes de visualizações, incluindo histogramas, boxplots, gráficos de densidade (KDE), Q-Q plots, scatter plots, violinplots e pairplots.

Detecção de outliers: Identificação e análise de valores atípicos utilizando o método do intervalo interquartil (IQR).

Análise bivariada e multivariada: Investigação das relações entre variáveis através de matriz de correlação e análise de charges por categorias demográficas e geográficas.

Os principais insights obtidos incluem a forte correlação entre tabagismo e custos de seguro, a distribuição assimétrica positiva da variável target, e diferenças regionais nos padrões de cobrança.

2. Inferência Estatística
Uma etapa diferenciada deste projeto foi a aplicação rigorosa de testes de hipóteses estatísticos:

Teste de Normalidade: Avaliação da distribuição da variável charges utilizando o teste de normalidade de D'Agostino-Pearson, revelando uma distribuição não-normal.

Teste t de Student: Comparação das médias de charges entre fumantes e não-fumantes, confirmando diferença estatisticamente significativa (p < 0.001).

ANOVA: Análise de variância para comparar custos entre diferentes regiões geográficas.

Teste Chi-Quadrado: Verificação da independência entre variáveis categóricas (sexo vs tabagismo, região vs tabagismo).

Correlações de Pearson: Cálculo e teste de significância para correlações entre variáveis numéricas e a variável target.

Intervalos de Confiança: Estimação de intervalos de confiança de 95% para as médias populacionais.

Estes testes estatísticos forneceram fundamentação científica para as decisões tomadas nas etapas subsequentes do projeto.

3. Feature Engineering
A engenharia de features foi realizada de forma extensiva, criando 27 novas variáveis a partir das features originais:

Features Polinomiais: Transformações quadráticas e cúbicas de idade e BMI para capturar relações não-lineares.

Features de Interação: Produtos cruzados entre variáveis (BMI × idade, BMI × filhos, idade × filhos) para modelar efeitos combinados.

Transformações Matemáticas: Aplicação de logaritmo natural e exponencial para normalização e captura de relações multiplicativas.

Categorização: Discretização de variáveis contínuas em grupos significativos (faixas etárias, categorias de IMC, número de filhos).

Indicadores Binários: Criação de flags para condições específicas (fumante, obeso, idoso, alto risco).

Features Compostas: Desenvolvimento de um score de risco ponderado combinando múltiplas variáveis.

Normalização: Padronização de variáveis numéricas para média zero e desvio padrão unitário.

Esta etapa elevou o número de features de 6 para 33, enriquecendo significativamente a capacidade preditiva dos modelos.

4. Análise de Componentes Principais (PCA)
Para lidar com a alta dimensionalidade resultante da feature engineering, aplicamos PCA:

Análise da variância explicada por cada componente principal, revelando que 95% da variância dos dados pode ser capturada por aproximadamente 20 componentes.

Estudo dos loadings (autovetores) para interpretar a contribuição de cada feature original nas componentes principais.

Redução dimensional estratégica, mantendo apenas os componentes que explicam 95% da variância total, resultando em uma redução de aproximadamente 40% nas dimensões.

Esta técnica de álgebra linear permitiu não apenas reduzir a complexidade computacional, mas também mitigar problemas de multicolinearidade entre as features.

5. Clustering com K-means
Implementamos segmentação não-supervisionada para identificar perfis distintos de beneficiários:

Determinação do número ótimo de clusters: Utilizamos o método do Silhouette Score, testando valores de K entre 2 e 10. O valor ótimo identificado foi K=3, com score de aproximadamente 0.35.

Caracterização dos clusters: Análise detalhada do perfil médio de cada cluster revelou segmentos como "baixo risco", "risco moderado" e "alto risco".

Validação estatística: Aplicação de ANOVA para confirmar que os clusters diferem significativamente em variáveis-chave como idade, BMI e charges (p < 0.001).

Integração ao modelo: Os clusters foram codificados como features adicionais, permitindo que os modelos capturem padrões de segmentação.

6. Modelagem Preditiva
Foram treinados e avaliados quatro modelos de regressão, representando diferentes abordagens:

Ridge Regression (L2): Regressão linear com regularização L2, penalizando coeficientes grandes para prevenir overfitting. Parâmetro alpha=10.0 otimizado.

Random Forest: Ensemble de 200 árvores de decisão com profundidade máxima de 20 níveis, utilizando bootstrap aggregating para reduzir variância.

Linear Regression: Modelo baseline de regressão linear múltipla sem regularização, servindo como referência de comparação.

Lasso Regression (L1): Regressão linear com regularização L1, que além de prevenir overfitting, realiza seleção automática de features ao zerar coeficientes irrelevantes.

Todos os modelos foram treinados em 80% dos dados e testados nos 20% restantes.

7. Avaliação e Validação
A avaliação dos modelos foi realizada através de múltiplas métricas complementares:

Métricas de Erro:

RMSE (Root Mean Squared Error): Penaliza erros grandes mais fortemente

MAE (Mean Absolute Error): Erro médio absoluto, interpretável na escala original

MAPE (Mean Absolute Percentage Error): Erro percentual médio

Métricas de Ajuste:

R² Score: Proporção da variância explicada pelo modelo

Análise de Overfitting: Diferença entre R² de treino e teste

Validação Cruzada 5-Fold:
Implementamos validação cruzada estratificada com 5 partições, garantindo que cada observação seja usada tanto para treino quanto para teste. Esta técnica fornece uma estimativa mais robusta da capacidade de generalização do modelo.

Análise de Resíduos:
Exame detalhado dos erros de predição através de:

Gráficos de resíduos vs predições

Histograma de resíduos

Q-Q plot para verificar normalidade dos erros

Análise temporal de resíduos

8. Feature Importance
Para o modelo de melhor desempenho (Random Forest), realizamos análise de importância de features baseada na redução de impureza Gini. As 15 features mais importantes foram identificadas e ranqueadas, revelando que variáveis como is_smoker, age e bmi têm papel dominante nas predições.

Esta análise fornece insights valiosos sobre quais fatores mais influenciam os custos de seguro, sendo útil tanto para interpretabilidade do modelo quanto para decisões de negócio.

Resultados
Performance dos Modelos
Modelo	R² Test	RMSE ($)	MAE ($)	MAPE (%)	Overfitting
Ridge Regression (L2)	0.8819	4,282.68	2,392.46	30.70	0.0162
Random Forest	0.8814	4,290.14	2,412.61	30.44	0.0637
Linear Regression	0.8802	4,311.93	2,422.98	30.77	0.0140
Lasso Regression (L1)	0.8801	4,313.60	2,413.54	30.63	0.0142
Melhor Modelo: Ridge Regression (L2)
O modelo de Ridge Regression apresentou o melhor desempenho geral, com:

R² de 0.8819, explicando aproximadamente 88% da variância dos custos de seguro

RMSE de $4,282.68, indicando erro médio quadrático aceitável

Baixo overfitting (0.0162), demonstrando boa capacidade de generalização

Validação cruzada: R² médio de 0.8797 ± 0.0089, confirmando estabilidade

Insights de Negócio
Tabagismo é o fator dominante: Fumantes têm custos médios significativamente superiores aos não-fumantes (diferença estatisticamente significativa com p < 0.001).

Idade e BMI têm relação não-linear: As transformações polinomiais melhoraram a performance, indicando que o aumento de custos acelera com idade e obesidade.

Segmentação de clientes: Os três clusters identificados representam perfis de risco distintos, úteis para estratégias diferenciadas de precificação.

Features de interação são relevantes: A combinação BMI × idade aparece entre as top features, sugerindo efeito sinérgico destes fatores.
