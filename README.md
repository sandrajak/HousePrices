# House Prices
Repositório criado para explicar o projeto de preços de casas do Kaggle: https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/overview

## Etapa 1 - Primeiro Modelo
Criar um modelo inicial para verificar o quanto estamos errando e depois planejar como melhorar. Para isso:
  - Eliminamos as colunas com mais de 10% de valores vazios.
  - Substituímos todos os valores vazios restantes por -1.
  - Mantivemos apenas as colunas numéricas.
  - Separamos essa base em treino e validação.
  - Escolhemos alguns algoritmos mais simples para testar:
    - Regressão Linear
    - Árvore de Regressão
    - KNN de Regressão
  - E métodos de avaliação de erro:
    - Erro médio absoluto
    - Erro quadrático médio
  - Criamos uma visualização gráfica para ver a relação da variável alvo com as previsões feitas.
  - Optamos pelo algoritmo com menor erro quadrático médio, a mesma métrica avaliada pelo Kaggle na hora de classificar os modelos.
  - Importamos a base de teste da competição e fizemos os mesmos tratamentos realizados na base de treino.
  - Aplicamos o modelo selecionado para fazer a previsão na base de teste da competição.
  - Criamos uma coluna para a nossa previsão.
  - Extraímos somente as colunas de identificação dos dados e da previsão realizada, para submeter esse arquivo no Kaggle.
---
- O arquivo utilizado está disponível no repositório, através do link: https://github.com/sandrajak/HousePrices/blob/main/Projeto_real_para_portfolio.ipynb
- O resultado obtido foi:
<img src="https://github.com/sandrajak/HousePrices/blob/main/imagens/resultado1.png"/>
