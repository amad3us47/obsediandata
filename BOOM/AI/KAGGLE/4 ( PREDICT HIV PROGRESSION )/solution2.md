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
import seaborn as sns

```

```python
test=pd.read_csv("test_data.csv")
train=pd.read_csv("training_data.csv")
```

```python
test.head()
```

```python
train.head()
```

```python
train['Resp'].value_counts().plot.bar(rot=0)
```

```python
from sklearn import metrics
from sklearn.model_selection import train_test_split,GridSearchCV
import xgboost as xgb
```

```python
x_cols = ['VL-t0', 'CD4-t0']
train_,test_ = train_test_split(train[x_cols + ['Resp']],test_size=0.33,random_state=42,stratify=train.Resp)
```

```python
'train:',train_.Resp.value_counts() / len(train_),'test:',test_.Resp.value_counts() / len(test_)


params_grid = {
    'min_child_weight': [1, 5, 10],
    'gamma': [0.5, 1, 1.5, 2, 5],
    'subsample': [0.6, 0.8, 1.0],
    'colsample_bytree': [0.6, 0.8, 1.0],
    'max_depth': [3, 4, 5],
    'n_estimators': [100,300,600,1000]
}

xgc = xgb.XGBClassifier()
grid = GridSearchCV(xgc,params_grid,cv=3,verbose=1000,n_jobs=5)

```

```python
grid.fit(train_[x_cols],train_.Resp)
```
