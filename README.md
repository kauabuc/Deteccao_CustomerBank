# Detecção de cancelamento de Conta
Projeto visando aprimorar minhas habilidades e buscando achar possíveis dificuldades e erros presentes para evoluir. O problema é que o banco está buscando entender e achar possíveis causas de cancelamentos de conta, para isso foi feita o processamento, análise, e construindo um modelo de machine learning para fazer futuras previsões com uma accuracia de 86%. Os dados brutos podem ser visualizados no 'Churn_Modelling.csv' ou no <a href="https://www.kaggle.com/datasets/adammaus/predicting-churn-for-bank-customers">Kaggle</a> seguindo o link.

## Para o Projeto
Foi usado os seguinte frameworks da linguagem Python: 
Pandas 
Numpy
Seaborn
MatplotLib
Sklearn
E todo o código foi montado dentro da IDE do Anaconda.

# Passos

## Processando os Dados
Começamos fazendo a importação das libraries necessárias para o projeto, e logo após importamos o nosso arquivo com a função do pandas read_csv.
A partir disso fizemos uma análise exploratória dos dados, buscando olhar como está o dataframe, qunatas colunas temos, quais vão ser necessárias, seu 'shape'
e se existem informações nulas ou faltantes. Junto disso fizemos uma análise estatística tendo os valores com a função describe().

### Manipulando os Dados
Tendo em vista as colunas necessárias após a primeira avaliação, descartamos as colunas que nao fariam sentido para o modelo de teste, (Surname, CustomerID, RowNumber),
se tratando de informações desnecessárias, usamos o drop e tiramos do dataset. <br>
Após isso vimos as colunas (Gender, Geography) onde precisamos passar elas para númerica, para fazer foi feita uma visualização das informações que obtinhamos nessas colunas e 
passamos elas para número usando a função do pandas get_dummies, onde ela transforma as informações e usamos o paramêtros drop_first, que ele funciona como a primeira informação 
obtida, na nova coluna se transforma em 0. Exemplo em Geography o primeiro país obtido foi France, ele transformou em duas novas colunas(Geography_Germany. Geography_Spain) que quando as duas são
zero é igual a France.

## Visualizando os Dados
Com a função countplot visualizamos o quantos clientes saiíram (1), e quantos permaneceram no banco (0). <br>
Foi feita também a correlação entre as variaveis onde podemos observar que nenhuma apresenta um valor tão alto.
Para esse processo foi utilizado o heatmap do  seaborn.

## Separando os dados 
Separamos nossa base de dados em duas sendo o y nossa variavel alvo, e x contendo o resto do dataset.
Separamos os dados de teste e os dados de treinamentos, sendo feita uma divisão 20/80 para os respectivos dados e aplicamos para os dados de uma padronização utilizando o StandardScaler do sklearn.

## Avaliando os possíveis modelos

Utilizando o SkLearn fizemos a importações necessárias, e já usando a validação cruzada para buscar o melhor algoritmo podemos ver os melhores resultados para a Random Forest que foi utilizado para o modelo final (foi utilizado os modelos Logistic Regression, RandomForest, SVM e KNN)

Utilizando o GridSearch para buscar os melhores parametros para montar o modelo e conseguimos 1% de melhoria nos resultados.
Montando a versão final do modelo e fazendo o treinamento do mesmo, fizemos as previsões utilizando esse modelo e para os resultados chegamos em 86% de accuracy, 83% de precisão e 73% de recall score utilizando o classification report e a validação cruzada(cross_val_score)

