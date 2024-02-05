# Classes

Objetivo: Conhecer o Paradigma da Programação Orientada  Objetos, o qual estrutura o código e abstrai os problemas para objetos, tornando-o mais modular

Uma classe é algo abstrato onde definimos as características e métodos dos objetos, sendo eles usados por meio de instâncias de classes



```python
class Bicicleta:
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

Usa-se o `super()__init__(x, y, z)` para chamar a implementação da classe pai, sendo `x, y, z` exemplos de argumento

Para solucionar as dificuldades de heranças múltiplas, são usadas as `**kwargs`

```python
class Mamifero():
    def __init__(self, x):
		self.x = x
        
class Ave():
    def __init__(self, y):
		self.y = y
        
class Ornitorrinco(Mamifero, Ave):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
```

`__mro__` ou `mro()`  mostra a ordem de resolução para achar os atributos e métodos dentro de uma classe



#### Encapsulamento

A variável de um objeto encapsulado somente pode ser alterada pelo método deste objeto, protegendo seus dados

Em Diagramas UML, parâmetros privados são identificados com um sinal de menos `-`, assim como os parâmetros públicos possuem um mais `+`

É necessário criar métodos para que seja possível a visualização de valores encapsulados



Um Decorador ou **Decorator** são funções que executam antes da sua função principal

```python
class Foo():
	def __init__(self):
        self._x = x
        
    @property
    def x(self):
        return self._x or 0
    
    @x.setter
    def x(self, value):
        _x = self._x or 0
        _value = value or 0
        self._x = _x + value
        
    @x.deletter
    def x(self):
        self._x = -1
        
        
foo = Foo(10)  # __init__
print(foo.x)  # 10
foo.x = 10  # x.setter
print(foo.x)  # 20
del foo.x  # x.deletter
print(foo.x)  # -1
```

Não é possível atribuir valores ou settar atributos que não tenham o `@.setter` no código

```python
@x.setter
def x(self, value):
	return self._x + value
```

O código acima não funcionaria por que ele não é um método, mas sim um atributo, tendo que usar o operador `+=` invés de somente o `+`.



### Polimorfismo

É particularmente útil nos casos em que o método herdado da classe pai não se encaixa perfeitamente na classe filha.



Um método de classe pode acessar ou modificar o estado da classe enquanto que um método estático não consegue.

```python
class Pessoa:
	def __init__(self, nome=None, idade=None):
        self.nome = nome
        self.idade = idade
        
    @classmethod
	def transformar_para_data_de_nascimento(cls, ano, mes, dia, nome):
        idade = 2023 - ano
        return cls(nome, idade)
    
    @staticmethod
    def e_maior_idade(idade):
        return idade >= 18
```

Serve para não criar mais uma instância de uma classe atoa.



Para forçar que uma classe filha tenha os mesmos métodos da classe pai, usa-se as Classes Abstratas

```python
from abc import ABC

class ControleRemoto(ABC):
    @abstractmethod
    def ligar(self):
        pass
    
    @abstractmethod
    def desligar(self):
        pass
    
    @property
    @abstractproperty
    def marca(self):
        pass
    
    
class ControleRemoto(ABC):
    pass
```

Dará erro pois não possui nem um dos 2 métodos
