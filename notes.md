# Anotações sobre Python

Toda linguagem é composta de um **alfabeto**, **léxica**, **sintaxe** e **semântica**



A linguagem pode ser traduzida por meio da **compilação** ou **interpretação**

Por ser uma linguagem interpretada, erros de sintaxe não executados não quebram o código



Anatomia de um erro: **traceback**, **local do erro**, **conteúdo da linha errônea**, **nome do erro**





A função `print()` com mais de um argumento os printará em apenas uma linha e espaço entre os argumentos

a keyword `end` determina o caractere que sairá no output no final dos últimos valores posicionais

a `sep` escolhem o caractere que ficará entre os argumentos



keywords devem ser postos depois do último argumento posicional de uma função e seguem a regra de: `keyword = valor`



Não é possível usar vírgula ou ponto em um número em Python, invés disso, a partir do Python 3.6, foi tornado possível o uso de underline, como em **11_111_111**



0o ou 0O para valores octais e 0x ou 0X para valores hexadecimais, a função print converte automaticamente



É possível omitir o zero antes ou depois da vírgula, como: `.5` ou `5.`

Para usar notação científica: 2x10² seria `2E2` ou `2e2`

o número depois do "E" deve ser inteiro e não float



```python
# Lógica

print("+" + 10 * "-" + "+")
print(("|" + " " * 10 + "|\n") * 5, end="")
print("+" + 10 * "-" + "+")
>>>
+----------+
|          |
|          |
|          |
|          |
|          |
+----------+
```

Interessante a forma que foi usado o `\n` junto com o `end=""` na segunda linha



```python
# Lógica

for i in range(5):
    my_list.insert(0, i + 1)
```

Criando uma lista de ordem reversa

> A variável `i` fica disponível para o resto do código, não apenas para o laço `for`


```python
my_list = [10, 1, 8, 3, 5]
 
my_list[0], my_list[4] = my_list[4], my_list[0]
my_list[1], my_list[3] = my_list[3], my_list[1]
```

Revertendo uma lista já pronta

```python
# Lógica

for i in range(length // 2):
    my_list[i], my_list[length - i - 1] = my_list[length - i - 1], my_list[i]
```

Revertendo uma lista com loop



O nome de uma variável ordinária é o nome do seu conteúdo

O nome de uma lista é o nome da localização da memória onde a lista está armazenada

Ou seja, fazendo o seguinte: `lista1 = lista2`, ambas as listas são identificadas na mesma localização da memória do computador, uma modificação em uma afetará a outra

```python
list_1 = ["A", "B", "C"]
list_2 = list_1
list_3 = list_2
 
del list_1[0]
del list_2
 
print(list_3)
>>> ['B', 'C']
```

O output será este pois estará sempre apontando para a primeira conexão

```python
list_1 = ["A", "B", "C"]
list_2 = list_1
list_3 = list_2
 
del list_1[0]
del list_2[:]
 
print(list_3)
>>> []
```

Apesar de que nesta ocasião, como foi feito o fatiamento, a 3° lista é excluída também

```python
board = [[EMPTY for i in range(8)] for j in range(8)]
```
Criando um tabuleiro com compreensão de lista aninhada




## Funções
É obrigatório os argumentos posicionais virem antes dos argumentos de palavra-chave

Há apenas 2 situações que pode ser usado a keyword `None` de maneira segura:
* Alocando em uma variável ou retornando em um resultado de função
* Comparando a uma variável para diagnosticar um estado interno



É possível atribuir um valor padrão casa o parâmetro não seja passado

```python
def faz_algo(a, b, c='c', d='d')
	return a, b, c, d
```



Usa-se a convenção `*args` para passar um número indeterminado de argumentos para a função

```python
def soma(*args):
	print(sum(args))

soma(1, 2, 3)
soma(4, 5)
soma(10, 1, 14 ,57 ,89, 30)
```

Usa-se a convenção `**kwargs` 

```python
def soma(*args, **kwargs):
	print(kwargs)

soma(1, 2, 3, a='a')
soma(4, 5, b='b', c='c')
```



## Tuplas

```python
a = tuple(1)  # Tupla
b = (1,)  # Tupla
c = 1,  # Tupla
d = (1)  # Não é tupla
e = 1  #  Não é tupla
```

Não é possível modificar os elementos de uma tupla, mas é possível realizar operações com elas



É possível desempacotar uma tupla

```python
tupla = (1, 2, 3)
a, b, c = tupla
```



É possível também trocar seus valores em uma mesma linha

```python
tupla = (1, 2)
a, b = tupla
b, a = a, b
```



```python
a, b, *c, d = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(a)
print(b)
print(c)
print(d)

>>> 1
2
[3, 4, 5, 6, 7, 8]
9
```

Uma variável com um asterisco `*` como prefixo recebe todos os valores da iterável que faltam das outras variáveis



## Listas

`.extend()`: concatena a lista do parâmetro no final da lista do método



## Dicionários

`dict()`

Não são do tipo de sequência mas podem ser adaptados para um processamento de sequência

É um set de chaves-valores



Não é possível percorrer um dicionário naturalmente com o loop for, mas com estes métodos:

- `.keys()` retorna uma lista com as chaves do dicionário
- `.values()` retorna os valores do dicionário
- `.items()` retorna uma tupla com as chaves e os valores, utilizada com 2 variáveis num loop `for



Para inserir um item em um dicionário usa-se:

```python
dicionario['nova_chave'] = 'novo_valor'  # Por declaração

dicionairo.update({'nova_chave': 'novo_valor'})  # Por método
```

Para remover o último item de um dicionário usa-se `.popitem()`



Para selecionar certo valor por meio da chave:

```python
a = dicionario['chave']  # Por declaração

b = dicionario.get('chave')  # Por método
```



```python
d1 = {'Adam Smith': 'A', 'Judy Paxton': 'B+'}
d2 = {'Mary Louis': 'A', 'Patrick White': 'C'}
d3 = {}

for item in (d1, d2):
    d3.update(item)
```

Mesclando 2 dicionários



Usa-se `.copy()` para copiar um iterável



## Boas práticas de programação

Exemplos: MyPy, Pycodestyle, Pylint, Flake8, Pyflake, autopep8, yapf.



Organiza a identação do código `Crtl + Alt + L`.

Tamanho máximo de 80 caracteres para linhas de códigos Python.

Preferível não utilizar o `Tab` e não os misturar com os espaços sendo o padrão de 4 espaços de indentação para o Pep8.

São necessárias as docstrings no começo de um programa e seus métodos e ganha-se o atributo especial `__doc__` (Pep257).



Quando tem-se muitos valores, seja em uma função ou array, a presença de vírgula seguida de uma quebra de linha ajuda a visualização, alinhando o fechamento:

```python
def funcao(a, b, c, d, e, 
           f, g, h, i, j):
	print(a, b, c, d, e, f, g, h, i, j)
	

funcao(
	1, 2, 3, 4, 5,
	6, 7, 8, 9, 10,
)

pares = [
	0, 2, 4, 
    6, 8, 10, 
    12, 14, 16,
    ]
```



É possível usar somente um `with` para abrir mais de um arquivo e um \ para quebra de linha:

```python
with open('arquivo.txt', 'r') as arq, \
     open('arquivo2.txt', 'r') as arq2
```



Funções dentro de uma classe viram métodos

Nas classes, há a diferença de 2 linhas para funções e apenas 1 linha para seus métodos.

É necessário declarar todas as variáveis em uma classe mesmo não as usando inicialmente:

```python
class Lobo:
	def __init__(self, cor, dente):
		self.cor = cinza
        self.dente = True
        self.comer = None  # Comentário
        
    def comer(self, animal):
        self.comer = animal  # Comentário
```

2 espaços para um comentário na mesma linha.



Importa-se na mesma linha as dependências de somente uma biblioteca.

Primeiro importam-se as bibliotecas padrões.

Segundo as bibliotecas de terceiros.

Terceiro as bibliotecas locais.

```python
import os  # Já vem no Python

import pandas  # Necessitam ser baixadas pelo Pip

import pysmells  # Você quem faz :)
```

Certas bibliotecas e variáveis são especiais e são importadas ou declaradas antes mesmo da importações das bibliotecas padrões.



Docstrings devem ser feitas neste padrão:

```python
def pylint_insight(self, count_by_type=False):
    """
    Gives insights in Pylint format of specified project
    :param count_by_type: 
    :type count_by_type Bool:
    :return: panda series with errors counted by type
    """
```

Um resumo sobre o que a função faz e depois seus parâmetros e seus tipos



As descrições dos módulos de um projeto são feitos no começo do programa:

```python
"""
PySmells is a program that gives insights about your code
__author__: Marco Aurelio
__modified__: Initial Check-In xx/xx/xxxx
"""
```



É uma boa conciliar a criação de relatórios com logs junto com os `try-excepts`

Caso tenha funções demais no código, é uma boa prática digitar a variável `__all__` recebendo uma lista de todas as funções para facilitar o acesso



Boas práticas para Function Annotation:

```python
def foobar(a: expression, b: expression = False) -> expression:
	pass
```

Usa-se `__annotations__` para checar as anotações do código



Usa-se o módulo chamado `unittest` para testes unitários



## Regex

**Regular Expressions** ou Expressões Regulares

Úteis em 2 ocasiões: Verificar se strings seguem um padrão e fazer substituições em uma string

```python
import re

pattern = r'py'

if re.match(pattern, 'pysmells'):
    print('Combina')
else:
    print('Não combina')
```

 `re.match()` é usado para determinar se uma string começa com uma outra certa string

O `r` que antecede a string sinaliza que tudo dentro dela será tratada como uma string, são as chamada **Raw Strings**, ou string bruta

> MUITO ÚTIL em pastas windows onde se tem a presença de contra-barra, "\\"
>
> É um equivalente ao .startswith()

- `re.search()`: é usado para comparações em qualquer lugar da string
- `re.findall()`: já retorna uma lista com todas as substrings que correspondem ao padrão
- `re.finditer()`: faz o mesmo que o de cima mas retorna um iterável



Métodos para insights sobre a correspondência:

```python
pattern = r'pam'

match = re.search(pattern, 'eggsaucepam')

if match:
    print(match.group())
    print(match.start())
    print(match.end())
    print(match.span())
```

- `.group()`: retorna a string ou conteúdo de um grupo correspondente
- `.groups()`: retorna todas as strings dentro de um grupo
- `.start()`: retorna o index do começo da primeira correspondência
- `.end()`: retorna o index do final da primeira correspondência

> o método `.start()` e `.end()` contam o index a partir de 1, invés de 0

- `.span()`:  retorna uma tupla com o index do começo e do final da primeira correspondência

```python
pattern = r"a(bc)(de)(f(g)h)i"

match = re.match(pattern, "abcdefghijklmnop")
if match:
    print(match.group())
    print(match.group(0))
    print(match.group(1))
    print(match.group(2))
    print(match.group(3))
    print(match.group(4))
    print(match.groups())
    
>>> abcdefghi
abcdefghi
bc
de
fgh
g
('bc', 'de', 'fgh', 'g')
```

> Antecipei um pouco esse conteúdo por que falava mais do método `.group()`

```python
pattern = r'(?P<primeiro>abc)(?:def)(ghi)'

match = re.match(pattern, 'abcdefghi')
if re.match(pattern, 'abcdefghi'):
    print(match.group('primeiro'))
    print(match.groups())
    
>>> abc
('abc', 'ghi')
```

> É bom alocar as correspondências em uma variável para ser possível visualizar seus grupos depois



O método `re.sub()` substitui todas as ocorrências de um padrão por uma string

```python
frase = 'Meu nome é Marco. Oi Marco.'
pattern = r'Marco'

nova_frase = re.sub(pattern, 'Izabela', frase, count=0)
print(nova_frase)

>>> Meu nome é Izabela. Oi Izabela.
```

Usa-se o parâmetro `count` para definir a quantidade de ocorrências a serem substituidas



Os **Metacharacters** são o que fazem as expressões regulares tão poderosas que métodos de strings normais

- `.` Ponto: corresponde a qualquer caractere menos uma nova linha

```python
pattern = r'gr.y'  # melhorando seria r'gr(a|e)y'

if re.match(pattern, 'grey'):
    print('Combina 1')
if re.match(pattern, 'gray'):
    print('Combina 2')
if re.match(pattern, 'blue'):
    print('Combina 3')
    
>>> Combina 1
Combina 2
```



- `|`: Barra vertical: funciona como um ou, `or`
- `^` Acento circunflexo: Corresponde ao começo da string
- `$` Cifrão: Corresponde ao final da string

```python
pattern = '^gr.y$'

if re.match(pattern, 'grey'):
    print('Combina 1')
if re.match(pattern, 'gray'):
    print('Combina 2')
if re.match(pattern, 'stingray'):
    print('Combina 3')
    
>>> Combina 1
Combina 2
```



**Character classes** faz a correspondência com uma lista específica de caracteres

- `[]` Colchete:  corresponde caso haja na string um caractere dentro dos colchetes

```python
pattern = r'[aeiou]'

if re.search(pattern, "grey"):
    print("Combina 1")

if re.search(pattern, "qwertyuiop"):
    print("Combina 2")

if re.search(pattern, "rhythm myths"):
    print("Combina 3")
    
>>> Combina 1
Combina 2
```

É possível usar o `-` Traço para corresponder a uma série de caracteres

```python
pattern = r'[A-Z][A-Z][0-9]'

if re.search(pattern, "LS8"):
    print("Combina 1")

if re.search(pattern, "aEB3i"):
    print("Combina 2")

if re.search(pattern, "1ab"):
    print("Combina 3")
    
>>> Combina 1
Combina 2
```

> O código acima irá corresponder a qualquer string q possua uma sequência dos 3 padrões acima
>
> [A-Za-z] irá corresponder a todas as letras maiúsculas e minúsculas

É possível utilizar também o `^` Acento circunflexo ANTES dos valores de uma classe para fazer uma negação dentro de uma character class, como neste exemplo: `pattern = r'[^A-Z]'`, onde serão pegos quaisquer caracteres que não sejam maiúsculos

Somente o `^` tem significado dentro de uma character class, todos os outros previamente amostrados não fazem nada



- `*` Asterisco: corresponde a NEM UMA ou várias repetições da última coisa, sendo essa coisa um único caractere, uma classe ou um grupo de caracteres em um parêntese

``` python
pattern = r'egg(spam)*'

if re.match(pattern, "egg"):
    print("Combina 1")

if re.match(pattern, "eggspamspamegg"):
    print("Combina 2")

if re.match(pattern, "spam"):
    print("Combina 3")
    
>>> Combina 1
Combina 2
```

- `()` Parênteses: serve para isolar uma cadeia de caracteres, transformando-as em um grupo
- `+` Adição: corresponde a UMA ou mais repetições 

```python
pattern = r'(42)+$'
```

Este padrão irá corresponder quando a string 42 parecer uma ou mais vezes e que seja também no final

- `?` Interrogação: corresponde a NEM UMA ou UMA repetição

```python
pattern = r'ice(-)?cream'
```



- `{}` Chaves: delimita a quantidade de ocorrências de tal correspondência

```python
pattern = r'9{1, 3}'
```

> `+` é equivalente a `{1, }` , `*` equivalente a `{0, }`, `?` equivalente a `{0, 1}`



```python
# Lógica

pattern = r'([^aeiou][aeiou][^aeiou])+'
```

Padrão de uma string que possui um ou mais ocorrências de não-vogal, vogal e não-vogal



**Special sequence** são escritas com um barra inversa seguido de um caractere

- `\1` até `\99`: significa a repetição no que foi achado no grupo de tal número entre 1 e 99

```python
pattern = r'(.+) \1'

match = re.match(pattern, "word word")
if match:
    print ("Combina 1")

match = re.match(pattern, "?! ?!")
if match:
    print ("Combina 2")    

match = re.match(pattern, "abc cde")
if match:
    print ("Combina 3")
    
>>> Combina 1
Combina 2
# revisar
```



- `\w`: equivalente a `[A-Za-z0-9]`, corresponde a letras com acento também
- `\d`: equivalente a `[0-9]`, são os números
- `\s`: equivalente a `[ \t\n\r\f\v]`, são os espaços, tabs e retornos

> As utilizando em letra maiúscula, `\W`, `\D` e `\S` significam o oposto de suas versões minúsculas

```python
pattern = r'(\D+\d)'

match = re.match(pattern, "Hi 999!")
if match:
    print("Combina 1")

match = re.match(pattern, "1, 23, 456!")
if match:
    print("Combina 2")

match = re.match(pattern, " ! $?")
if match:
    print("Combina 3")
    
>>> Combina 1
```

> Só irá corresponder ao primeiro por que precisa iniciar com um caractere que não seja um dígito



- `\A`: equivale ao começo da string
- `\Z`: equivale ao final da string
- `\B`: corresponde a uma string vazia entre os caracteres `\w` e `\W` ou caracteres `\w` no começo ou final da string 
- `\b`: corresponde a uma string vazia em qualquer outro lugar

```python
pattern = r'\b(cat)\b'

match = re.search(pattern, "The cat sat!")
if match:
    print ("Combina 1")

match = re.search(pattern, "We s>cat<tered?")
if match:
    print ("Combina 2")

match = re.search(pattern, "We scattered.")
if match:
    print ("Combina 3")

>>>
```



### Destrinchando e descomplicando sobre regex de e-mails:

```python
pattern = r'([\w\.-]+)@([\w\.-]+)(\.[\w\.]+)'
```

> Esta é um forma básica de se criar um regex para e-mail

Um endereço de e-mail básico consiste em em uma palavra que possa incluir pontos `.` e traços `-` , o arroba `@` e o nome de domínio (o nome, um ponto `.` e o sufixo do nome do domínio)

O regex acima contém 3 grupos:

1. `[\w\.-]+`: corresponde a uma ou mais ocorrência de qualquer letra, ou número, ou ponto `.` 
2. `[\w\.-]+`: mesmo do de cima
3. `\.[\w\.]+`: um ponto seguido da correspondência do de cima

> Como o ponto `.` significa qualquer caractere normalmente, põe-se uma contra-barra `\` antes para que o mesmo seja tratado como somente um ponto



## Desenvolvimento Web

```python
# Problema

select_periodo = Select(driver.find_element('name', 'P'))  # Vai dar erro

Select(driver.find_element('name', 'P')).select_by_index(i)  # Vai rodar
```

é melhor não alocar em uma variável pois quando a página tem perde noções dinâmicas o endereço de memória e deve ser achado o endereço novamente
