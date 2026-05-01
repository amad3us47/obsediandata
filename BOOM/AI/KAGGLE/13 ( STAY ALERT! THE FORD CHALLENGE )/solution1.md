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
train=pd.read_csv("fordTrain.csv")
test=pd.read_csv("fordTest.csv")
```

```python
train.head()
```

```python
test.head()
```

```python
test=test.drop('IsAlert',axis=1)
```

```python
test
```

```python
test.shape ,train.shape
```

```python
train.isnull().sum()
```

```python
train.info()
```

```python
train=train.drop(['TrialID','ObsNum'],axis=1)
```

```python
train.head()
```

```python
test=test.drop(['TrialID','ObsNum'],axis=1)
```

```python
test.head()
```

```python
train.skew()
```

```python
from sklearn.model_selection import train_test_split
X=train.drop('IsAlert',axis=1)
y=train['IsAlert']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4)
```

```python
from sklearn.ensemble import RandomForestClassifier
```

```python
model=RandomForestClassifier()
model.fit(X_train,y_train)
```

```python
y_pred=model.predict(X_test)
```

```python
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)
```
