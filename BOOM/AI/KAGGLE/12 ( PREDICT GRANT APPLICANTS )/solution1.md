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
import numpy as np
import matplotlib.pyplot as plt
```

```python
train_data=pd.read_csv("unimelb_training.csv",low_memory=False)
```

```python
train_data.head()
```

```python
from sklearn.model_selection import StratifiedGroupKFold
from sklearn.metrics import accuracy_score
```

```python
train_data.shape
```

```python
train_data.describe()
```

```python
import seaborn as sns
train_data.hist(bins=4, figsize=(30,50))
plt.show()
```

```python
train_data.columns
```

```python
vars=['Grant.Application.ID','Grant.Status','RFCD.Code.1','RFCD.Percentage.1','RFCD.Code.2','RFCD.Percentage.2','RFCD.Code.3','RFCD.Percentage.3','RFCD.Code.4','RFCD.Percentage.4','RFCD.Code.5','RFCD.Percentage.5','SEO.Code.1','SEO.Percentage.1']
```

```python
df1 = [col for col in train_data.columns if train_data[col].dtype == 'object']
```

```python
train_data.dtypes
```

```python
df1=train_data[vars]
```

```python
df1.fillna(df1.mean(), inplace= True)
```

```python
df1.columns
```

```python
input = [col for col in df1.columns if df1[col].dtype != 'object']
```

```python
output='Grant.Status'
```

```python
input.remove(output)
```

```python
from sklearn.linear_model import LogisticRegression
```

```python
log1 = LogisticRegression(max_iter=20)
```

```python
log1.fit(X=df1[input], y=df1[output])
```

```python
from sklearn.metrics import accuracy_score
```

```python
preds = log1.predict(X=df1[input])
```

```python
preds
```

```python
print(accuracy_score(y_pred=preds, y_true=df1[output]))
```

```python
from sklearn.ensemble import RandomForestClassifier
```

```python
random_forest1 = RandomForestClassifier()
```

```python
random_forest1.fit(X=df1[input], y=df1[output])
```

```python
print(accuracy_score(y_pred=random_forest1.predict(X=df1[input]), y_true=df1[output])*100)
```

```python
from sklearn.metrics import confusion_matrix
confusion_matrix = confusion_matrix(df1[output], random_forest1.predict(X=df1[input]))
print(confusion_matrix)
```
