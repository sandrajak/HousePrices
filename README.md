# House Prices
Repositório criado para a **[competição do Kaggle](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) sobre a previsão de preços das casas** na cidade de Ames, Iowa (Estados Unidos).

<img src='https://github.com/lucaslealx/HousePrices/blob/main/img/img1.png' />



## [Etapa 1 - Primeiro Modelo](https://github.com/sandrajak/HousePrices/blob/main/Etapa1.ipynb)
Foi criado um modelo inicial básico para verificar o resultado sem nenhum tipo de tratamento ou engenharia de dados:
  - Para simplificar, **foi eliminado colunas com mais de 10% de valores vazios**, **os valores vazios restantes foram substituídos por -1** e **foi mantido apenas as colunas numéricas**.
  - Foram escolhidos **3 algoritmos** para criar os modelos: **[Regressão Linear](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)**, **[Árvore de Regressão](https://scikit-learn.org/stable/modules/tree.html#regression)** e **[KNeighborsRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html#sklearn.neighbors.KNeighborsRegressor)**.
  - Métodos de avaliação de erro usados: **[erro médio absoluto](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html)** e **[erro quadrático médio](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_error.html)**, dando preferência pro segundo pois é a métrica usada na competição.
- O **score público retornado pelo Kaggle foi: 0,25476**.

## [Etapa 2: Limpeza dos dados](https://github.com/sandrajak/HousePrices/blob/main/Etapa2.ipynb)
- Iniciou-se o processo de **limpeza dos dados**, analisando **valores vazios e informações faltantes** para escolher a melhor estratégia de tratamento.
- Em algumas colunas parte dos valores vazios na verdade eram **atributos que a casa não tinha**, como por exemplo valores vazios nas colunas relacionadas a garagem indicavam que aquele imóvel não possuia garagem. Nesse caso o vazio **era uma informação**.
- Em outros casos a informação realmente estava ausente, então aplicou-se tratamentos como **substituir pela média da coluna**, **utilizar uma agregação para encontrar a melhor média para o atributo**, **utilizar a moda**, entre outros.
- Utilizou-se os mesmos modelos da etapa 1 (o que pode ser visto no arquivo **[Etapa2Modelos](https://github.com/sandrajak/HousePrices/blob/main/Etapa2Modelos.ipynb)**) e o **score público retornado pelo Kaggle foi: 0,33711**.

## [Etapa 3: Tratamento dos dados](https://github.com/sandrajak/HousePrices/blob/main/Etapa3.ipynb)
- Com a base gerada na etapa 2 - com os dados já tratados, foi analisado a **correlação entre as variáveis numéricas e os valores mais frequentes das variáveis de texto**.
- Para tratar colunas do tipo texto, primeiramente **eliminou-se as colunas com muitos valores iguais** e depois, **utilizando lambda function e funções próprias**, foram realizados mais alguns tratamentos.
- Além disso, também foi utilizado o **[OneHotEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html) para o tratamento das variáveis que não possuem relação de ordem** e o **[OrdinalEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OrdinalEncoder.html) para as variáveis ordenadas**.
- Então, **explorou-se as colunas de garagem** para ter um entendimento completo dessa categoria de variáveis.
- Também foram analisadas mais 2 variáveis que poderiam ter uma **correlação mais direta com o preço das casas**: qualidade da cozinha e do material do exterior. Por fim, analisou-se as colunas que tem maior correlação com a coluna alvo, em **busca de outliers significativos**. Alguns destes foram eliminados, para ver o comportamento do modelo.
- Nessa etapa foram geradas 2 bases, e aplicados os mesmos algoritmos e métodos de avaliação de erros anteriores:
   - a primeira (_1), **apenas com as colunas analisadas a fundo**: executado os modelos no arquivo **[Etapa3_1Modelos](https://github.com/sandrajak/HousePrices/blob/main/Etapa3_1Modelos.ipynb)** e obteve-se um **score público do Kaggle de 0,35619**.
   - a segunda (_2), **tratamento de apenas mais 2 colunas de texto** e **exclusão de alguns outliers significativos**: para essa base foi executado o **[Etapa3_2Modelos](https://github.com/sandrajak/HousePrices/blob/main/Etapa3_2Modelos.ipynb)** e obteve-se um **score público do Kaggle de 0,17124**.

## Etapa 4: Testando algoritmos novos
- Introduzido 2 novos modelos para testar além da regressão linear (modelo que tinha gerado o melhor resultado até então). Esses modelos são indicados na própria competição do Kaggle: **[RandomForestRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html#sklearn.ensemble.RandomForestRegressor)** e **[XGBoost](https://xgboost.readthedocs.io/en/stable/index.html)**.
- Executou-se esses 2 algoritmos novos nos mesmos arquivos:
  - No arquivo usado para testar os modelos anteriores na Etapa3_1, executado o **[Etapa4_1](https://github.com/sandrajak/HousePrices/blob/main/Etapa4_1.ipynb)**. Optou-se pelo Random Forest pois apresentou o menor erro quadrático médio, com um **score público do Kaggle de 0,15288**.
  - Já com o mesmo arquivo da Etapa3_2 - executado no **[Etapa4_2](https://github.com/sandrajak/HousePrices/blob/main/Etapa4_2.ipynb)**, o Random Forest apresentou um erro quadrático médio apenas um pouco acima da regressão linear nos dados de validação, e para os dados de teste o score público no Kaggle foi melhor, ficando em: **0,15371**.
- Apenas com a alteração do modelo o resultado melhorou!

## [Etapa 5: Melhorando os parâmetros](https://github.com/sandrajak/HousePrices/blob/main/Etapa5_Melhorando_parametros.ipynb)
Agora aliou-se o **[GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)** para encontrar **parâmetros melhores** para os 2 modelos da etapa anterior, aplicados a base das colunas analisadas a fundo (Etapa3_1).
O RandomForest teve um menor erro quadrático e o XGBoost um menor erro absoluto, então foi testado os 2 modelos nos dados de teste da competição. Resultados do score público no Kaggle:
 - Para o Random Forest: **0,15355**.
 - Para o XGBoost: **0,14253**.
   - Para os dados de teste, com os parâmetros otimizados o XGBoost gerou o melhor resultado!

Como já foi alcançado um erro de 0,14 o projeto foi finalizado. Se continuasse, poderia ocorrer um overfitting nos dados e isso não é bom, pois se almeja um modelo que seja o mais generalizável possível.
