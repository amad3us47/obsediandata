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
import matplotlib.pyplot as plt
```

```python
test=pd.read_csv("test_data.csv")
train=pd.read_csv("training_data.csv")
```

```python
train.head()
```

```python
import seaborn as sns
sns.countplot(train['Resp'])
```

```python
from sklearn.model_selection import train_test_split
X = train[['VL-t0','CD4-t0']]
Y = train['Resp'].values
x_train, x_test, y_train, y_test = train_test_split(X, Y, test_size=0.3, random_state=2)
```

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score
knn_model = KNeighborsClassifier()
knn_model.fit(x_train, y_train)
predicted = knn_model.predict(x_test)
print('KNN', accuracy_score(predicted, y_test))
```

```python
from sklearn.ensemble import RandomForestClassifier
rfc_model = RandomForestClassifier()
rfc_model.fit(x_train, y_train)
predicted = rfc_model.predict(x_test)
print('Random Forest', accuracy_score(y_test, predicted))
```

```python
from sklearn.svm import SVC
svc_model = SVC(gamma='auto')
svc_model.fit(x_train, y_train)
predicted = svc_model.predict(x_test)
print('SVM', accuracy_score(y_test, predicted))
```

```python
from xgboost import XGBClassifier
xgb_model = XGBClassifier()
xgb_model.fit(x_train, y_train)
predicted = xgb_model.predict(x_test)
print('XGBoost', accuracy_score(y_test, predicted))
```
