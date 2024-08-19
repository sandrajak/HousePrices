# House Prices
Repositório criado para a **[competição do Kaggle](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) sobre a previsão de preços das casas** na cidade de Ames, Iowa (Estados Unidos).

<img src='https://github.com/lucaslealx/HousePrices/blob/main/img/img1.png' />

## [Etapa 1 - Primeiro Modelo](https://github.com/sandrajak/HousePrices/blob/main/Etapa1.ipynb)
Foi criado um modelo inicial básico para verificar o resultado sem nenhum tipo de tratamento ou engenharia de dados:
  - Para simplificar, **eliminamos colunas com mais de 10% de valores vazios**, **substituímos os valores vazios restantes por -1** e **mantivemos apenas as colunas numéricas**.
  - Escolhemos **3 algoritmos** para criar os modelos: **[Regressão Linear](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)**, **[Árvore de Regressão](https://scikit-learn.org/stable/modules/tree.html#regression)** e **[KNeighborsRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html#sklearn.neighbors.KNeighborsRegressor)**.
  - Métodos de avaliação de erro usados: **[erro médio absoluto](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html)** e **[erro quadrático médio](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_squared_error.html)**, dando preferência pro segundo pois é a métrica usada na competição.
- O **score público retornado pelo Kaggle foi: 0,25476**.

## [Etapa 2: Limpeza dos dados](https://github.com/sandrajak/HousePrices/blob/main/Etapa2.ipynb)
- Iniciamos o processo de **limpeza dos dados**, analisando **valores vazios e informações faltantes** para escolher a melhor estratégia de tratamento.
- Em algumas colunas os valores vazios representavam **ausência dos atributos na casa**, como por exemplo o valor vazio na coluna de garagem significava que aquele imóvel não possuia garagem. Nesse caso o vazio **era uma informação**.
- Em outros casos a informação realmente estava ausente, então usamos tratamentos como **substituir pela média da coluna**, **utilizar uma agregação para encontrar a melhor média para o atributo**, **utilizar a moda**, entre outros.
- Utilizamos os mesmos modelos da etapa 1 (o que pode ser visto no arquivo **[Etapa2Modelos](https://github.com/sandrajak/HousePrices/blob/main/Etapa2Modelos.ipynb)**) e o **score público retornado pelo Kaggle foi: 0,33711.**

## [Etapa 3: Tratamento dos dados](https://github.com/sandrajak/HousePrices/blob/main/Etapa3.ipynb)
- Com a base gerada na etapa 2 - com os dados já tratados, começamos analisando a **correlação entre as variáveis numéricas e os valores mais frequentes das variáveis de texto**.
- Para tratar colunas do tipo texto, primeiramente **eliminamos as colunas com muitos valores iguais** e depois **utilizamos lambda function e funções próprias para fazer os tratamentos**.
- Além disso, também foi utilizado o **[OneHotEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html) para o tratamento das variáveis que não possuem relação de ordem** e o **[OrdinalEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OrdinalEncoder.html) para aquelas ordenadas**.
- Por fim, **nos aprofundamos nas colunas de garagem** para fazer um completo entendimento dessa categoria de variáveis. Com mais tempo e melhor entendimento do negócio, poderíamos estender essa análise para todos os outros grupos de colunas.
- Nessa etapa foram geradas 2 bases, e aplicados os mesmos algoritmos e métodos de avaliação de erros anteriores:
   - a primeira (_1) onde **selecionamos apenas as colunas que analisamos a fundo**: executamos os modelos no arquivo **[Etapa3_1Modelos](https://github.com/sandrajak/HousePrices/blob/main/Etapa3_1Modelos.ipynb)** e tivemos um **score público do Kaggle de 0,35619.**
   - a segunda (_2) onde fizemos um **tratamento genérico para todas as demais colunas de texto**: para essa base foi executado o **[Etapa3_2Modelos](https://github.com/sandrajak/HousePrices/blob/main/Etapa3_2Modelos.ipynb)** e tivemos um **score público do Kaggle de 0,45827.**
    - Esses resultados piores ocorreram, provavelmente, devido ao aumento considerável do número de colunas e aos modelos utilizados. Isso será tratado nas próximas etapas!
