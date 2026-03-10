###### Problemas com dados: garbage in, garbage out



**NaN** significa "não é um número" e é uma maneira comum de marcar valores ausentes.

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### Renomear colunas

Recomendamos começar com o método info() para obter uma ideia geral sobre o conjunto de dados.



Vamos lembrar como usá-lo:



**print(df.info())**



Como alternativa, você pode usar o atributo **.columns** que só imprime os nomes das colunas e nada mais.



**import pandas as pd**

\# as distâncias são armazenadas em uma lista de listas

**measurements = \[\['Sun', 146, 152],**

                                **\['Moon', 0.36, 0.41],** 

                                **\['Mercury', 82, 217],** 

                                **\['Venus', 38, 261],**

                                **\['Mars', 56, 401],**

                                **\['Jupiter', 588, 968],**

                                **\['Saturn', 1195, 1660],**

                                **\['Uranus', 2750, 3150],**

                                **\['Neptune', 4300, 4700],**

                                **\['Halley\\'s comet', 6, 5400]]**



\# os nomes das colunas são armazenados na variável de cabeçalho

**header = \['Celestial bodies ','MIN', 'MAX']** 

\# armazenando o DataFrame na variável celestial

**celestial = pd.DataFrame(data=measurements, columns=header)**



Para verificar os nomes das colunas, vamos imprimir o atributo columns do DataFrame:

**print(celestial.columns)**

**Index(\['Celestial bodies ','MIN', 'MAX'], dtype='object')**



Vamos alterar 'Celestial bodies ' para 'celestial\_bodies' e Substituiremos 'MIN' e 'MAX' por 'min\_distance' e 'max\_distance'



Para renomear colunas, chame o método **rename()** com um dicionário como argumento columns

ex:

\# Declarando um dicionário com os nomes antigos das colunas como as chaves

\# e os novos nomes de colunas como os valores

**columns\_new ={**

    **"Celestial bodies ": "celestial\_bodies",**

    **"MIN": "min\_distance",**

    **"MAX": "max\_distance",**

    **}**

\# Chamando o método rename e passando o dicionário como um argumento para o parâmetro columns

**celestial = celestial.rename(columns = columns\_new)**

**print(celestial.columns)**



No entanto, existe uma maneira mais elegante de renomear colunas que não requer reatribuição como fizemos acima. Precisamos apenas especificar o parâmetro **inplace** e defini-lo como **True**



\# Declarando um dicionário com os nomes antigos das colunas como as chaves

\# e os novos nomes de colunas como os valores

**columns\_new ={**

    **"Celestial bodies ": "celestial\_bodies",**

    **"MIN": "min\_distance",**

    **"MAX": "max\_distance",**

    **}**



\# Chamando o método rename e passando o dicionário como um argumento para o parâmetro **columns** e **True** como um argumento para o parâmetro **inplace**

**celestial.rename(columns = columns\_new, inplace = True)**

**print(celestial.columns)**



outro exemplo de substituição de coluna

**import pandas as pd**



**df = pd.read\_csv('/datasets/music\_log\_raw.csv')**



**df = df.rename(columns={**

    **'  user\_id': 'user\_id',** 

    **'total play': 'total\_play',**

    **'Artist': 'artist'**

**})**



**print(df.columns)**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

##### Forma automatizada de renomear colunas



**new\_col\_names = \[]**



**for old\_name in celestial.columns:**

    # Primeiro, remova os espaços no início e no final

    **name\_stripped = old\_name.strip()**

    # Em seguida, coloque todas as letras em minúsculas

    **name\_lowered = name\_stripped.lower()**

    # Por fim, substitua os espaços entre as palavras por sublinhados

    **name\_no\_spaces = name\_lowered.replace(' ', '\_')**

    # Adicione o novo nome à lista de novos nomes das colunas

    **new\_col\_names.append(name\_no\_spaces)**



\# Substitua os nomes antigos pelos novos

**celestial.columns = new\_col\_names**



Esse método de troca é útil quando você tem nomes de coluna que quer definir no formato de lista.



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### Processamento de valores ausentes



###### **identificar valores ausentes:**



**isna()** **-** verificar rapidamente quais colunas possuem valores ausentes 

 **isna()**não é tão útil sem outros métodos. Normalmente usamos junto com o método sum(). A função sum() conta todos os valores True e retorna sua soma:

ex:

**print(cholera.isna().sum())**

Você também pode encontrar o comando **isnull()** no lugar de **isna()**, eles fazem a mesma coisa.



###### **Substituição de valores:**



**fillna() -** retorna uma cópia da coluna original com todos os valores NaN substituídos pelo valor especificado

ex:

**cholera\['imported\_cases'] = cholera\['imported\_cases'].fillna(0)**



**print(cholera)**

Como alternativa, você poderia definir o argumento **inplace=True** para não precisar atribuir uma nova coluna no lugar da antiga:

**cholera\['imported\_cases'].fillna(0, inplace=True)**



você pode até usar o ciclo for para substituir os valores ausentes:

\# percorrendo os nomes das colunas e substituindo valores ausentes com 0s

**columns\_to\_replace = \['imported\_cases']**



**for col in columns\_to\_replace:**

    **cholera\[col].fillna(0, inplace=True)**



###### **Remoção de linhas**



**dropna() -** remove linhas ou colunas com valores ausentes em um DataFrame

&nbsp;Esse método remove linhas com pelo menos um valor ausente. Você também pode especificar uma lista de colunas para o parâmetro **subset=** e ele vai remover as linhas com valores nulos apenas nessas colunas.

ex:

**cholera = cholera.dropna(subset=\['total\_cases', 'deaths', 'case\_fatality\_rate'])**

**print(cholera)**



Usaremos o método **dropna()** novamente, mas desta vez adicionaremos outro argumento: **axis=**. Este argumento nos permite especificar se queremos remover linhas ou colunas



ex:

**cholera = cholera.dropna(axis='columns')**

**print(cholera)**



você pode usar o método drop() para controlar quais colunas deseja descartar. Isso é o que você deve fazer se quiser descartar apenas a coluna 'notes' usando o método drop()



**cholera = cholera.drop(labels=\['notes'], axis='columns')**



Ambos drop() e dropna() suportam o argumento inplace=, que permite realizar a operação no local sem reatribuição



**cholera.drop(labels=\['notes'], axis='columns', inplace=True)**



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



##### Processamento de valores duplicados



###### métodos:

 

**duplicated() -** ele retorna True se um valor for duplicado e False caso contrário.

ex:

**import pandas as pd**

**df = pd.read\_csv('/datasets/music\_log\_raw.csv')**



**print(df.duplicated().sum())  ---** conta quantos valores duplicados existem no DataFrame

----------------------------------------------------------------------------------------------------------

**drop\_duplicates() -** Para remover linhas totalmente duplicadas

ex:

**df = df.drop\_duplicates()**



**print(df.duplicated().sum())** 



Alternativamente, podemos especificar **inplace=True**, assim não haverá necessidade de reatribuição:



**df.drop\_duplicates(inplace=True)**



**print(df.duplicated().sum())**

----------------------------------------------------------------------------------------------------------

é importante atualizar os índices quando você remove linhas. Para fazer isso, chame o método:

**reset\_index() -**

**ex:**

**df = df.drop\_duplicates().reset\_index()**



**print(df.head())**  # chama as 5 primeira linhas do DataFrame



para remover a coluna index que armazena os indices antigos basta definir o parâmetro **drop=True**

ex: 

**df = df.drop\_duplicates().reset\_index(drop=True)**

----------------------------------------------------------------------------------------------------------

Para ver todos os valores únicos em uma coluna, use o método:

**unique() -**

Este método retorna todos os valores únicos em uma coluna especificada

ex:

**print(df\['column'].unique())**

Para descobrir duplicados menos óbvios, os analistas fazem suas pesquisas por valores únicos, que podem incluir:

\*Ortografias alternativas da mesma palavra (por exemplo, ortografia brasileira vs. portuguesa)

\*Erros ortográficos (por exemplo, 'jazzz' em vez de 'jazz')

\*Inconsistências entre letras maiúsculas e minúsculas

----------------------------------------------------------------------------------------------------------

Às vezes, queremos apenas saber o número de valores únicos em uma coluna, em vez dos próprios valores reais. Nesse caso, podemos usar o método: 

**nunique() -**  O n em **nunique()** significa número, esta função retorna o número de valores únicos

ex:

**print(tennis\['name'].nunique())**







###### Removendo duplicados implícitos:

Use o método replace() para corrigir ortografia incorreta ou alternativa

ex:

**tennis\['name'] = tennis\['name'].replace('Roger Federerr', 'Roger Federer')**

**tennis\['name'] = tennis\['name'].replace('Roger Fedrer', 'Roger Federer')**

**tennis\['name'] = tennis\['name'].replace('Rafael Nadal', 'Rafael Nadal Parera')**



**print(tennis)**



Automatizando com funções personalizadas

Para evitar repetir o mesmo código várias vezes vamos criar uma função que recebe quatro argumentos:

\*O DataFrame

\*O nome da coluna onde queremos fazer a substituição

\*Uma lista de valores incorretos

\*O valor correto

ex:

**def replace\_wrong\_values(df, column, wrong\_values, correct\_value):** # passando uma lista de valores incorretos e uma string com o valor correto como entrada da função

    **for wrong\_value in wrong\_values:** # percorrendo com um ciclo os nomes mal escrito

        **df\[column] = df\[column].replace(wrong\_value, correct\_value)** # chamando replace() para cada nome errado

    **return df** # retornando o dataframe modificado



**duplicates = \['Roger Federerr', 'Roger Fedrer']** # uma lista de nomes mal escritos

**name = 'Roger Federer'** # nome corret**o**

**tennis = replace\_wrong\_values(tennis, 'name', duplicates, name)** # chamada da função, replace() será chamada duas vezes

**print(tennis)** # o novo DataFrame sem duplicados



**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



#### Agrupamento de dados

Na Pandas, agrupamos os dados usando o método **groupby()**



\*Assume o nome de uma coluna na qual os dados devem ser agrupados como um argumento. Este parâmetro é chamado by=. No nosso caso, vamos agrupar os dados pelo ano de descoberta.



\*Retorna um objeto de um tipo especial: DataFrameGroupBy. Este objeto corresponde a dados agrupados. Se você aplicar um método da biblioteca pandas nele, ele vai se transformar em uma nova estrutura de dados.



\*Vamos encontrar o número de exoplanetas agrupados por ano utilizando o método count()

ex:

**print(exoplanet.groupby(by='discovered'))**

**print()** # vai aparecer como uma linha vazia entre duas impressões

**print(exoplanet.groupby(by='discovered').count())**



Caso precise comparar observações usando apenas um parâmetro, use o método no objeto DataFrameGroupBy e indique a coluna desejada, por exemplo, 'radius' 

ex:

**exo\_number = exoplanet.groupby('discovered')\['radius'].count()**

**print(exo\_number)**



Para encontrar a soma dos raios, use o método sum():

ex:

**exo\_radius\_sum = exoplanet.groupby('discovered')\['radius'].sum()**

**print(exo\_radius\_sum)**



Em seguida, precisamos dividi-lo pelo número de exoplanetas descobertos cada ano.

ex:

**exo\_radius\_mean = exo\_radius\_sum / exo\_number**

**print(exo\_radius\_mean)**

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

#### Ordenamento de dados



**sort\_values() -** O método  em pandas é uma ferramenta poderosa para ordenar valores. Ele consegue ordenar a tabela inteira ou grupos de linhas da tabela.

Este método é aplicado a um DataFrame e possui dois parâmetros:

**by=** **—** o nome ou nomes das colunas cujos valores são usados para ordenar as linhas do DataFrame.

**ascending= —** a ordem da ordenação. Seu valor padrão é True. Para ordenar os dados em ordem decrescente, defina esse parâmetro como False.

ex:

**exoplanet.sort\_values(by='radius',ascending=False)**

###### 

###### **Ordenando os dados sobre exoplanetas:**



**print(exoplanet.sort\_values(by='radius').head(10))**



Aqui está o código que ordena apenas a coluna radius (raio) e imprime os 10 primeiros resultados:

**print(exoplanet\['radius'].sort\_values().head(10))**



Lembre-se de que um valor igual a 1 indica que o raio é o mesmo que o da Terra. 

Podemos obter todos os exoplanetas com raios menores que o da Terra usando indexação lógica:

 

\# Exoplanetas menores que a Terra e descobertos em 2014

**exo\_small\_14 = exoplanet\[exoplanet\['radius'] < 1]**

**exo\_small\_14 = exo\_small\_14\[exo\_small\_14\['discovered'] == 2014]**

**print(exo\_small\_14)**



Vamos ordenar o resultado por raio em ordem decrescente:



**print(exo\_small\_14.sort\_values(by='radius', ascending=False))**



























