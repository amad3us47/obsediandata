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
import seaborn as sns
import matplotlib.pyplot as plt
```

```python
data=pd.read_csv("tourism2_revision2.csv")
exam_sub=pd.read_csv("example_submission.csv")
```

```python
exam_sub.info()
```

```python
exam_sub.head()
```

```python
exam_sub["m1"].plot(kind='line')
exam_sub["m2"].plot(kind='line')
plt.show()
```

```python
data.info()
```

```python
data.head()
```

```python
data.tail()
```

```python
data=data.iloc[:,:-2]
data.head()
```

```python
data.tail()
```

```python
data.shape
```

```python
data.isnull().sum().sort_values(ascending=False)
```

```python
no_null_columns=data.isnull().sum()[data.isnull().sum() == 0].index
```

```python
no_null_columns
```

```python
# visualization of m1 column
month_1=data["m1"]
month_1.isna().sum()
```

```python
month_1=month_1.fillna(-100)
month_1
```

```python
plt.figure(figsize=(12,6))
plt.xlabel=month_1.plot(kind='line')
plt.title("Columns of m1")
plt.show()
```

```python
month_2=data["m2"]
month_2.isna().sum()
```

```python
month_2.fillna(-100)
plt.figure(figsize=(15,5))
plt.xlabel=month_1.plot(kind='line')
plt.title("Columns of m1")
plt.show()
```

```python
col=data["q239"]
col=col.fillna(-100)
plt.figure(figsize=(15,5))
plt.xlabel=col.plot(kind='line')
plt.show()
```

```python
def plot_col(col_name="m338"):
    col=data.loc[:,col_name]
    col=col.fillna(-100)
    plt.figure(figsize=(15,5))
    plt.xlabel=col.plot(kind='line')
    plt.show()
plot_col()
```

```python
data.columns
```

```python
col=data.loc[:,"m338"]
col=col.fillna(-100).iloc[:60]
plt.figure(figsize=(15,5))
plt.xlabel=col.plot(kind='line')
plt.title("first 60 data of m338")
plt.show()
```

```python
plot_col("m330")
```

```python
plot_col("m38")
```

```python
plot_col("m39")
```

```python
# XGBoost on column m38
import xgboost as xgb
from sklearn.metrics import mean_squared_error
color_pal=sns.color_palette()
```

```python
data_m38=data["m38"]
data_m38.shape
```

```python

```
