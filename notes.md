# Anotações sobre Python

Toda linguagem é composta de um **alfabeto**, **léxico**, **sintaxe** e **semântica**



A linguagem pode ser traduzida por meio da **compilação** ou **interpretação**



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



**Lógica**

```python
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

```
board = [[EMPTY for i in range(8)] for j in range(8)]
```
Criando um tabuleiro com compreensão de lista aninhada


## Funções
É obrigatório os argumentos posicionais virem antes dos argumentos de palavra-chave

Há apenas 2 situações que pode ser usado a keyword None de maneira segura:
* Alocando em uma variável ou retornando em um resultado de função
* Comparando a uma variável para diagnosticar um estado interno

