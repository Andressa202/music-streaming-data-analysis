##### **Biblioteca Pandas**



Pandas é a biblioteca Python mais usada para processamento de dados. Possui vários recursos, incluindo:



\*Obter dados de várias fontes e uni-los.

\*Resolver problemas com dados, como remover duplicados ou preencher valores ausentes

\*Adicionar, remover ou modificar dados da tabela

\*Agrupamento de dados e cálculo de estatísticas para grupos



###### **atributos:**



**dtypes -** nos permite visualizar os tipos de dados dos valores em cada coluna.

**columns -** pode ser usado para exibir os nomes das colunas.

**shape -** é usado para entender o tamanho da tabela.



Você pode acessar cada atributo da tabela separadamente ou pode solicitá-los de uma só vez chamando o método **info()**

ex: **print(df.info())**



**import pandas as pd** 

classe **DataFrame(data, columns)** recebe dois argumentos 



**data -** espera uma lista contendo os dados 

**columns -** espera uma lista de nome de colunas que correspondam a lista de dados 



###### **exemplo de código:** 



**import pandas as pd**

\# preparando os dados e os nomes das colunas

**atlas = \[**

      **\['France', 'Paris'],**  

        **\['Russia', 'Moscow'],**  

        **\['China', 'Beijing'],**  

        **\['Mexico', 'Mexico City'],**  

        **\['Egypt', 'Cairo'],**

**]**

**geography = \['country', 'capital']**



\# fazendo um DataFrame

**world\_map = pd.DataFrame(data=atlas , columns=geography)**



\# imprimindo o DataFrame

**print(world\_map)**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### Leitura de arquivos CSV e Excel 



Para ler um arquivo CSV usando pandas, precisamos chamar a função **read\_csv()**

ex:

**import pandas as pd** 



**df = pd.read\_csv('/datasets/music\_log\_chpt\_11.csv')** # o argumento é o caminho do arquivo



Para ler um arquivo Excel usando pandas, precisamos chamar a função **read\_excel()**

ex: 

**import pandas as pd**



**df = pd.read\_excel('/datasets/music\_log.xlsx')** # o argumento é o caminho do arquivo





A Pandas fornece dois métodos para exibir o início ou o fim de um conjunto de dados: **head()** e **tail()**. O método **head()** exibe as primeiras linhas de uma tabela, enquanto **tail()** exibe as últimas linhas.



ex:

**import pandas as pd**



**df = pd.read\_csv('/datasets/music\_log\_chpt\_11.csv')**



**print(df.head())**



resultado:

      **user\_id  total play        Artist    genre                   track**

**0  BF6EA5AF   92.851388    Marina Rei      pop                  Musica**

**1  FB1E568E  282.981000  Stive Morgan  ambient             Love Planet**

**2  FB1E568E  282.981000  Stive Morgan  ambient             Love Planet**

**3  EF15C7BA    8.966000           NaN    dance     Loving Every Minute**

**4  82F52E69  193.776327        Rixton      pop  Me And My Broken Heart**





O método tail funciona de maneira semelhante, mas exibe as últimas linhas

ex:

 **import pandas as pd**



**df = pd.read\_csv('/datasets/music\_log\_chpt\_11.csv')**



**print(df.tail(3))**



resultado:

                **user\_id  total play        Artist  genre      track**

**67960  26B7058C  292.455000       Red God  metal  Действуй!**

**67961  DB0038A8   11.529112  Less Chapell    pop       Home**

**67962  FE8684F6    0.100000           NaN    NaN        NaN**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### Indexação do DataFrame



Há um atributo para acessar valores de uma tabela em um DataFrame, o atributo **loc\[]: df.loc\[row, column]**. Os colchetes após loc devem receber o número de row (linha) e o nome de column (coluna) do valor desejado.



Por exemplo, para obter os conteúdos da célula na quinta linha e na coluna 'genre', use **df.loc\[4, 'genre']**



ex

**import pandas as pd**



**df = pd.read\_csv('/datasets/music\_log\_chpt\_11.csv')**

**result = df.loc\[4, 'genre']**

**print(result)**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### Filtragem com indexação lógica



Na biblioteca pandas, esse algoritmo complexo pode ser realizado em uma linha de código

Primeiro, encontraremos todas as linhas em que uma determinada condição é atendida. Por exemplo, usando o conjunto de dados music\_log\_chpt\_11.csv com o qual trabalhamos antes, podemos verificar se a coluna 'genre' é igual a 'pop'. Podemos usar a notação abreviada da seguinte forma:

ex

**print(df\['genre'] == 'pop')**



Como alternativa, podemos usar o atributo loc:



**print(df.loc\[:, 'genre'] == 'pop')**



Agora podemos usar o resultado obtido no passo anterior para filtrar a tabela original. Devemos obter uma tabela filtrada apenas com músicas 'pop'. Para isso, utilizamos o atributo .loc mais uma vez, passando os valores booleanos obtidos na etapa anterior:

ex

**print(df.loc\[df.loc\[:, 'genre'] == 'pop'])**



Como alternativa, podemos usar:



**print(df.loc\[df\['genre'] == 'pop'])**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### contar e somar





**mean() -** calcula a media 

**count() -** conta o numero de linhas que atendem a um determinado critério 

**sum() -** faz a soma 





Aqui está o código completo que escrevemos para calcular e imprimir a média:



**import pandas as pd**



**df = pd.read\_csv('/datasets/music\_log\_chpt\_11.csv')**



**pop\_df = df\[df\['genre'] == 'pop']**



**pop\_duration = pop\_df\['total play']**



**mean\_duration = pop\_duration.mean()**



**print(mean\_duration)**



ou modo simplificado:



**import pandas as pd**



**df = pd.read\_csv('/datasets/music\_log\_chpt\_11.csv')**



**mean\_duration = df\[df\['genre'] == 'pop']\['total play'].mean()**



**print(mean\_duration)**









