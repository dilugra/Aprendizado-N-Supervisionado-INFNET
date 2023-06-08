# Escolha de base de dados

Para as questões a seguir, usaremos uma base de dados e faremos a análise exploratória dos dados, antes da clusterização.

Baixe os dados disponibilizados na plataforma Kaggle sobre dados sócio-econômicos e de saúde que determinam o índice de desenvolvimento de um país. Esses dados estão disponibilizados através do link: https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data
Quantos países existem no dataset?
Mostre através de gráficos a faixa dinâmica das variáveis que serão usadas nas tarefas de clusterização. Analise os resultados mostrados. O que deve ser feito com os dados antes da etapa de clusterização?
Realize o pré-processamento adequado dos dados.
Clusterização

Para os dados pré-processados da etapa anterior você irá:

Realizar o agrupamento dos países em 3 grupos distintos. Para tal, use:
K-Médias
Clusterização Hierárquica
Para os resultados, do K-Médias:
Interprete cada um dos clusters obtidos citando:
Qual a distribuição das dimensões em cada grupo;
O país, de acordo com o algoritmo, melhor representa o seu agrupamento. Justifique.
Para os resultados da Clusterização Hierárquica, apresente o dendograma e interprete os resultados.
Compare os dois resultados, aponte as semelhanças e diferenças e interprete.
Escolha de algoritmos

Escreva em tópicos as etapas do algoritmo de K-médias até sua convergência.
O algoritmo de K-médias converge até encontrar os centróides que melhor descrevem os clusters encontrados (até o deslocamento entre as interações dos centróides ser mínimo). Lembrando que o centróide é o baricentro do cluster em questão e não representa, em via de regra, um dado existente na base. Refaça o algoritmo apresentado na questão 1 a fim de garantir que o cluster seja representado pelo dado mais próximo ao seu baricentro em todas as iterações do algoritmo.
Obs: nesse novo algoritmo, o dado escolhido será chamado medóide.
 O algoritmo de K-médias é sensível a outliers nos dados. Explique.
Por que o algoritmo de DBScan é mais robusto à presença de outliers?

### RESPOSTA
### COLOQUEI NA PASTA CODE DO GITHUB ANALISE, PREPROCESSAMENTO E MODELO , NA PREPROCESSAMENTO É UMA VERIFICAÇÃO BÁSICA, NA ANÁLISE É UMA VERIFICAÇÃO DOS DADOS A FIM DE ENTENDER MELHOR COMO EXECUTAR E MODELO É A APLICAÇÃO EM SI.
### para encontrar os Países que melhor representa os clusters, eu usei o método cluster_centers_ para determinar os centroides e busquei os indices mais próximos do meu centroide. QUE SÃO ZAMBIA, ICELAND E SURINAME, VEJA O ARQUIVO MODEL_BASE_PAÍSES PARA VER O COMO CALCULADO.
### O dendograma esta no arquivo model, mas a interpretação dele esta aqui também. ### Interpretação do Dendograma

O dendograma da clusterização hierarquica mostra a estrutura dos clusters e como eles se relacionam. temos claramente que nossa hierarquia se divide em 2 etapas em uma dessas etapas temos um cluster definido pela cor Laranja, esse grupo laranja tem um Threshold ligeralmente abaixo de 13, esses são os países mais pobres e com piores ínices. Os países com índices medianos e bons, tem algumas coisas em comum.  Temos claramente que por volta do Threshold 11(green) temos 2 grupos muito parecidos, porém se difere na segunda ramificação da arvore. 

### Comparando os resultados dos modelos

O Kmeans após aplicada uma PCA para redução de dimensionalidade, ele ficou mais eficiente na questão de separar de forma mais efetiva as variáveis.

Temos a facilidade de mostrar as componentes da PCA 1 vs a outra, isso facilita a verificação e a obtenção de informação para saber como a classificação poderá ocorrer componente a componente. 

Na Hierarquica temos um pouco mais enrigecido, pois ela cria as ramificações, e mesmo que tenhamos distancias iguais dentro de alguns nós , pode ser diferentes clusters pois um nó superior é dividido por alguma componente. isso pode restringir as divisões que queremos fazer e até possiveis reduções de dimensionalidade, pois se as componentes quando plotadas ficarem altamente correlacionadas, temos sim uma possibilidade de ampliar nossa PCA.

A Clusterirzação Hirarquica nos da uma visão de como poderá ser feito, uma panorama da estrutura dos dados e relações, com elas temos a possibilidade de fazer uma clusterização pelo Kmeans de forma mais eficiente. Logo eu entendo como a hierarquica como um passo para entender os dados e o kmeans para começar a classificar efeticamente os dados.

### Escoilha dos algoritmos -- resposta
 
* O kmeans funciona selecionando de forma aleatória um centroide. A quantidade de centroide é indicada por nós quando passamos o n_cluster.
* Depois de atribuir o N número de centroides , ele faz uma verificação entre as médias das distancias entre os pontos do cluester e o centroide. Atualizando os centroides para ser o centro do cluster.
* Essa etapa acima de atribuir um centroide, calcular a distância e atualizar a posição é repetida inúmeras vezes ou até atingir o máximo de interaçõs que desejamos.
* A convergencia se da quando o centroide atribuido não se move mais quando temos a verificação das distancias pelas médias. Ou seja O algoritimo encontrou uma relação que melhor separa os dados de forma a ficar mais equilibrado em relação a distancia do ponto central do cluster e os pontos do cluester.
* o algoritmo kmeans é sensível a outliers ?  SIM , muito sensível pois os cálculos de distancia levam em consideração esses pontos fora da curva, e assim podem fazer que o centroide se desloque mais do que deveria. 
* por que o DBSscan é melhor a presença de outliers ?  Ele é melhor pois é capaz de identificar esses pontos fora da curva e ruídos , ele é sensível a densidade de pontos e não ao valor do ponto, com isso fica mais plausível o seu uso. Outra questão é a complexidade de formas de organizar os clusters, o kmeans usa centroide e distancia em relação a ele, isso significa que ele organiza de forma esférica onde vai ter um ponto central e um raio onde os dados serão classificados como dentro do cluster. 
