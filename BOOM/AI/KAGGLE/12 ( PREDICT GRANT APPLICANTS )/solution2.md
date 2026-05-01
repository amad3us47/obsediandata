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
import seaborn as sns
```

```python
train=pd.read_csv("unimelb_training.csv",low_memory=False)
train.head()
```

```python
train.describe
```

```python
train.columns
```

```python
train.info()
```

```python
import matplotlib.pyplot as plt
train.isnull().sum().any
```

```python
train.columns
```

```python
train.isnull().values.any()
```

```python
new_binary = train.filter(['Grant.Status','RFCD.Percentage.5','SEO.Percentage.5'], axis=1)
new_binary.head()
```

```python
new_binary.fillna(0, inplace=True)
new_binary.head()
```

```python
x = new_binary.iloc[:,1:]
x.head()
```

```python
y = new_binary.iloc[:,0]
y.head()
```

```python
from sklearn import tree, metrics
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(x, y, test_size=0.2)

```

```python
from sklearn import tree, metrics
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(x, y, test_size=0.2)
```

```python
dtree = tree.DecisionTreeClassifier(criterion='entropy', max_depth=3, random_state=0)
dtree.fit(X_train, y_train)
```

```python
y_pred = dtree.predict(X_test)

# how did our model perform?
count_misclassified = (y_test != y_pred).sum()
print('Misclassified samples: {}'.format(count_misclassified))
accuracy = metrics.accuracy_score(y_test, y_pred)
print('Accuracy: {:.2f}'.format(accuracy))
```
