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

```python jupyter={"is_executing": false}
import numpy as np
import pandas as pd
import seaborn as sns
```

```python jupyter={"is_executing": false}
df=pd.read_csv("training_data.csv")
```

```python jupyter={"is_executing": false}
df.head(10)
```

```python
list(df)
```

```python
data = df[['PatientID', 'Resp', 'VL-t0', 'CD4-t0']]
```

```python
data.head(10)
```

```python
data['Resp'].value_counts(1) * 1000
```

```python
import matplotlib.pyplot as plt
import seaborn as sns
plt.figure(figsize=(12,6))
sns.countplot(x="Resp",data=data)
```

```python
data['Resp'].nunique() # gets unqiue values inside the column of data frame
```

```python
data['Resp'].unique()
```

```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split

```

```python
X = data[['VL-t0','CD4-t0']].values
Y = data[['Resp']].values
```

```python
X_train,X_test,Y_train,Y_test = train_test_split(X,Y,test_size = 0.2, random_state =2 )  #training set
model = LogisticRegression()
model.fit(X_train, Y_train)

```


```python
prediction=model.predict(X_test)
```

```python
from sklearn.metrics import classification_report 
print(classification_report(Y_test, prediction))
```

```python
from sklearn.neighbors import KNeighborsClassifier
classifier = KNeighborsClassifier(n_neighbors = 5, metric = 'minkowski', p = 2)
classifier.fit(X_train, Y_train)
```

```python
y_pred = classifier.predict(X_test)


print(classification_report(Y_test, y_pred))


```
