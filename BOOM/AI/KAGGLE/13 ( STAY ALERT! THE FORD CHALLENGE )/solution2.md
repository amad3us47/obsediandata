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
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```

```python
train=pd.read_csv("fordTrain.csv")
```

```python
plt.hist(x=train["P6"])
train["IsAlert"].value_counts()
```

```python
train=train[train["P6"]<=30000]
train=train.drop(columns=["TrialID","V7","V9","P8"])
x=['P3','P6','E3','E4','E6','E7','E8','E9','E10','V3','V5','V6','V10','IsAlert']
for i in x:
    train[i]=train[i].astype('int16')
y=['P1','P2','P4','P5','P7','E1','E2','E5','E11','V1','V2','V4','V8','V11']
for i in y:
    train[i]=train[i].astype('float16')
```

```python
from sklearn.model_selection import train_test_split

x = train.drop(['IsAlert'], axis='columns')



y=train['IsAlert']
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.3)
```

```python
%%time
from sklearn.ensemble import RandomForestClassifier
model=RandomForestClassifier()
model.fit(x_train,y_train)
```

```python
%%time
y_pred=model.predict(x_test)
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)
```
