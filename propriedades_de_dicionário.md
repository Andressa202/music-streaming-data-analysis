##### **propriedades de dicionário:**

exemplo de dicionário com a chave contendo o numero do voo e valor contendo a data e hora do voo

**schedule = {**

**    'SU2222': '12.06.18 12:30', # a chave fica à esquerda dos dois pontos,**

**    'SU1111': '12.06.18 14:05',    # o valor fica à direita**

**    'SU0777': '12.06.18 17:00'**

}



\*Elementos de dicionários são colocados entre chaves – {}.

\*Os itens em um dicionário (pares chave-valor) são separados por vírgulas.

\*Uma chave e um valor em um par são separados por dois pontos.

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**

###### **extrair valor de um dicionário:**



**financial\_info = {**

&nbsp;   **'American Express': 93.23,

    'Boeing': 178.44,

    'Coca-Cola': 45.15,

    'Nike': 97.99,

    'JPMorgan':96.27,
    'Walmart': 130.68**


**}**



**# acessando o valor da chave 'Coca-Cola' do dicionário**

**coca\_cola\_price = financial\_info\['Coca-Cola']**

**print(coca\_cola\_price)**



se não houver a chave definida no dicionário ele retorna uma KeyError, podemos usar o método **get()** para receber um retorno none ou definir um segundo argumento.



**ex:  pepsi\_price = financial\_info.get('pepsi', 'não tem')**

&nbsp;    **print(pepsi\\\_price)
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



###### adicionar um item a uma lista:



**financial\_info\['Walmart'] = 119.34**



###### ou se quisermos verificar se a informação ja existe e substituir o seu valor caso exista:



**if financial\_info.get('Walt Disney') == None:** # verificando se a chave Walt Disney existe

&nbsp;   **financial\\\_info\\\['Walt Disney'] = 119.34** # se não, adicionamos a chave


**else:** # se ela existe

&nbsp;   **financial\\\_info\\\['Walt Disney'] += 3.2
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**



**del -** remove um item do dicionário, também podemos usar o método **pop()** para remover e acessar o seu valor.

ex: **del financial\_info\['Nike']**

**print(financial\_info)**

