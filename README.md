%md

# Análise de Dados de Seguros de Saúde

Este projeto tem como objetivo analisar dados de seguros de saúde, segmentar perfis de clientes e construir modelos preditivos para estimar custos médicos individuais. O trabalho segue uma abordagem completa de ciência de dados, desde a exploração inicial até a modelagem avançada.

## Etapas do Projeto

1. **Exploração e Pré-processamento**
   - Análise exploratória dos dados.
   - Tratamento de valores ausentes e outliers.
   - Engenharia de features, incluindo variáveis de risco e transformação de variáveis categóricas.

2. **Redução de Dimensionalidade**
   - Aplicação de PCA para identificar as principais componentes que explicam a variância dos dados.
   - Análise dos loadings e autovalores para interpretação das componentes.

3. **Clusterização**
   - Segmentação dos clientes utilizando K-means.
   - Determinação do número ótimo de clusters com métodos como Silhouette Score e Davies-Bouldin.
   - Análise do perfil de cada cluster e validação estatística das diferenças entre eles.

4. **Modelagem Preditiva**
   - Treinamento de modelos de regressão linear com regularização (Ridge, Lasso, ElasticNet).
   - Aplicação de métodos ensemble (Random Forest, Gradient Boosting, AdaBoost).
   - Combinação de modelos com Voting e Stacking Regressor.
   - Avaliação de modelos com dados reduzidos (PCA) e com features de clusterização.

5. **Avaliação e Seleção de Modelos**
   - Comparação de desempenho dos modelos com métricas como R², RMSE, MAE e MAPE.
   - Análise de resíduos e importância das features.
   - Validação cruzada para verificar a estabilidade dos modelos.

## Como Utilizar

1. Clone o repositório e instale as dependências necessárias.
2. Execute o notebook principal em ambiente Databricks ou Jupyter.
3. Siga as etapas sequenciais para reproduzir a análise e os resultados.

## Principais Resultados

- Identificação de perfis de risco entre os clientes.
- Modelos preditivos robustos para estimativa de custos médicos.
- Insights sobre as variáveis mais relevantes para o custo de seguro de saúde.

## Estrutura dos Dados

O dataset inclui variáveis como idade, índice de massa corporal (BMI), número de filhos, status de fumante, entre outras, além do custo anual do seguro de saúde.

## Licença

Este projeto é de uso acadêmico e educacional.

## Contato

Para dúvidas ou sugestões, entre em contato com o responsável pelo projeto.
