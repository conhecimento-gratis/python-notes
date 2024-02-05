Para concatenar vários arquivos de uma só vez, pode-se usar loop junto com a biblioteca `glob` (retorna uma lista com todos os caminhos dos arquivos que correspondem ao padrão passado no parâmetro)

```python
# Lógica

import pandas as pd
import glob

caminho_estados_gerais = glob.glob('bd/consulta_*.csv')

lista_df = []

for dados_estado in caminho_estados_gerais:
    lista_df.append(pd.read_csv(dados_estado, sep=';', encoding='latin_1'))

df_todos_estados = pd.concat(lista_df, axis=0, ignore_index=True)
```



# Passar para DataScience

```python
novo_dataframe = dataframe.loc[dataframe['Coluna1'] > 10, ['Coluna2', 'Coluna3']]
# dataframe.loc[filtro_linhas, colunas_desejadas]
```

**⮴ Constrói um dataframe com as colunas desejadas e as linhas que cumprem a condição informada**



A função `.filter()` filtra dados a partir dos rótulos dos índices das colunas e linhas

like: trecho a ser pesquisado nos rótulos

axis: 0 para linha e 1 para coluna

