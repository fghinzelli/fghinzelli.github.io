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
data[<COLUMN_KEY].value_counts() # Counts distinct values of a column
dados["NU_IDADE"].value_counts().sort_index() # Ordenated data by index
dados["NU_IDADE"].value_counts(normalize=True).mul(100).round(4).astype(str) + '%' # Percentual with ajusts
dados.loc[dados["NU_IDADE"] == 13]["SG_UF_RESIDENCIA"] # Loc select by values
```

- Generate graphs
```python
dados["NU_IDADE"].hist() # Histogram
dados["NU_IDADE"].hist(bins = 20) # Histogram with more divisions
dados["NU_IDADE"].hist(bins = 20, figsize=(10,8)) # Difine size of the picture

```
