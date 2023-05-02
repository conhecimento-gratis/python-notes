# Classes

Objetivo: Conhecer o Paradigma da Programação Orientada  Objetos, o qual estrutura o código e abstrai os problemas para objetos, tornando-o mais modular

Uma classe é algo abstrato onde definimos as características e métodos dos objetos, sendo eles usados por meio de instâncias de classes



```python
class Bicilicleta:
    def __init__(self, cor, modelo, ano, valor):
        self.cor = cor
        self.modelo = modelo
        self.ano = ano
        self.valor = valor
        
    def __del__(self):
        print('Removendo a instância')
        
    def buzinar(self):
        print('Plim plim')
    
    def parar(self):
        pass
    
    def correr(self):
        pass
    
caloi = Bicicleta('vermelha', 'caloi', 2022, 600)
caloi.buzinar()
print(caloi.cor)

>>> 'Plim plim'
'vermelha'
```

As variáveis dentro de uma classe são chamadas de atributos

Métodos são funções que estão dentro de uma classe

Os métodos que começam e terminam com `__` são chamados de métodos especiais

`__init__` é um método construtor de classe, sempre executado na criação de uma nova instância de classe

Usa-se o método especial `__del__` para quando uma instância de um objeto for destruída

O argumento `self` representa a instância do objeto

`caloi.buzinar()` é equivalente a `Bicicleta.buzinar(caloi)` 

```python
def criar_bicicleta():
	b = Bicicleta('vermelha', 'caloi', 2022, 600)
    print(p.cor)

criar_bicileta()

>>> 'vermelha'
'Removendo a instância'
```

Todas as variáveis locais de uma função quando a mesma termina de ser executada, morrem, aplicando o método especial `__del__`



Para printar sua classe, usa-se o método `__str__`

```python
def __str__(self):
    return f'Bicicleta: cor={self.cor}, modelo={self.modelo}, ano={self.ano} , valor={self.valor}'

print(caloi)
```

modo automatizado:

```python
def __str__(self):
    return f'{self.__class__.__name__}: {', '.join([f'{chave}={valor}' for chave, valor in self.__dict__.items()])}'

print(caloi)
```

> CARA QUE SNIPPET DE CÓDIGO MARAVILHOSO MERMÃO

`self.__class__.__name__`: Retorna o nome da classe

`self.__dict__.items()`: Retorna uma tupla com todas as chaves e valores da classe

`[f'{chave}={valor}' for chave, valor in self.__dict__.items()]`: Além de botar uma f string dentro de outra f string, ele iterou a tupla acima por meio de uma compreensão de lista

e logo depois juntou tudo com o `', '.join()`



Os métodos que começam e terminam com `__` são chamados de métodos especiais

A variáveis dentro de uma classe são chamadas de atributos

Usa-se o método especial `__del__` para quando uma instância de um objeto for destruída

```python
def criar_cachorro():
	c = Cachorro('Zeus', 'branco e preto', False)
    

```



### Herança

```python
class A:
    pass

class B(A):
    pass

class C:
    pass

class D(A, C):
    pass
```

