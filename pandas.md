## Pandas

![Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Pandas_logo.svg/300px-Pandas_logo.svg.png)

```python
import pandas as pd
```

- Reading data

```python
data = pd.read_csv('file.csv')
data.head() # Fist lines
data.shape() # Size of document (lines x columns)
data[<COLUMN_KEY>] # All data in a column
data[<COLUMN_KEY>] # Unique values from a column
data[<COLUMN_KEY>].value_counts() # Counts distinct values of a column
data[<COLUMN_KEY>].value_counts().sort_index() # Ordenated data by index
data[<COLUMN_KEY>].value_counts(normalize=True).mul(100).round(4).astype(str) + '%' # Percentual with ajusts
data.loc[dados[<COLUMN_KEY_1>] == 13] # Loc select by values
data.query("IN_TREINEIRO == 1") # Query values
```

- Generate graphs
```python
data[<COLUMN_KEY>].hist() # Histogram
data[<COLUMN_KEY>].hist(bins = 20) # Histogram with more divisions
data[<COLUMN_KEY>].hist(bins = 20, figsize=(10,8)) # Difine size of the picture
data[<COLUMN_KEY>].plot.box(grid = True, figsize=(8,6)) # Box plot
data[<COLUMN_KEY>].value_counts().plot.pie(figsize=(10,8)) # Pie graph
data[<COLUMN_KEY>].value_counts().plot.bar(figsize=(10,8)) # Bars graph
```

- Utils functions
```python
data[<COLUMN_KEY>].mean() # Media
data[<COLUMN_KEY>].std() # Desvio Padrao
columns = ["NU_NOTA_CN", "NU_NOTA_CH", "NU_NOTA_MT", "NU_NOTA_LC", "NU_NOTA_REDACAO"]
data[columns].describe() # Several info
```

