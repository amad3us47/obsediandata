---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.18.1
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
data=pd.read_csv("unimelb_training.csv",low_memory=False)
test=pd.read_csv("unimelb_test.csv")
```

```python
data.shape
```

```python
data.head()
```

```python
data.info()
```

```python
data.tail()
```

```python
data.describe()
```

```python
total=data.isnull().sum().sort_values(ascending=False)
total
```

```python
percent = (data.isnull().sum() / data.isnull().count() * 100).sort_values(ascending = False)
missing_train_data = pd.concat([total, percent], axis = 1, keys = ['Total', 'Percent'])
missing_train_data.head(50)
```

```python
data.dropna(axis = 1, how = 'all')
```

```python
data.dropna(axis=1,thresh=8000,inplace=True)
```

```python
train_columns=data.columns
```

```python
test.dropna(axis=1,thresh=8000,inplace=True)
```

```python
test
```

```python
data.shape
```

```python
test.shape
```
