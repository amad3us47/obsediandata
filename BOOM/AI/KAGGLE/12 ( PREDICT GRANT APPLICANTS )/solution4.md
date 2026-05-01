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
data=pd.read_csv("unimelb_training.csv",low_memory=False)
data.head()
```

```python
list(data)
```

```python
data.isna().sum()
```

```python
data1=data.iloc[:,1:40]
data1
```

```python
data1.isna().sum()
```

```python
data2= data1.drop(['Country.of.Birth.1','Sponsor.Code','Grant.Category.Code','Start.date','Contract.Value.Band...see.note.A','Home.Language.1','With.PHD.1','No..of.Years.in.Uni.at.Time.of.Grant.1'],axis =1)
```

```python
data2.shape
```

```python
data2.isna().sum()
```
