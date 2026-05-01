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

```

```python
train=pd.read_csv("overfitting.csv")
```

```python
train
```

```python
train.isna().sum()
```

```python
list(train)
```

```python
train['train'].info()
```

```python
## Information Gain  ( Feature Selection ) 

X=train.drop('case_id', axis=1)
y=train['Target_Practice']
```

```python
from sklearn.model_selection import train_test_split
from sklearn.feature_selection import mutual_info_classif

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30, random_state=0)
# Find Mutual Information
mutual_info = mutual_info_classif(X_train, y_train)

# Restructure the mutual information values for ease of reading
mutual_info = pd.Series(mutual_info)
mutual_info.index = X_train.columns
mutual_info.sort_values(ascending=False)
```

```python
from sklearn.ensemble import RandomForestClassifier
model=RandomForestClassifier()
model.fit(X_train,y_train)
y_pred=model.predict(X_test)
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)
```
