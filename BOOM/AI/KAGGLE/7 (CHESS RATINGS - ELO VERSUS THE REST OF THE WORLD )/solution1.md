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
import matplotlib.pyplot as plt
import seaborn as sns

```

```python
cv=pd.read_csv('chess/cross_validation_dataset.csv')
sub=pd.read_csv('chess/example_submission.csv')
test=pd.read_csv('chess/test_data.csv')
train=pd.read_csv('chess/training_data.csv')
```

```python
train.head()
```

```python
train.isnull().describe()
```

```python
train["Month #"].value_counts()
```

```python
sns.distplot(train['White Player #'])
plt.axvline(train['White Player #'].values.mean(),color='red',linestyle='dashed',linewidth=1)
plt.title('white player')
```

```python
sns.distplot(train['Black Player #'])
plt.axvline(train['Black Player #'].values.mean(),color='green',linestyle='dashed',linewidth=1)
plt.title('white player')
```

```python
sns.distplot(train['Score'],color='g')
plt.axvline(train['Score'].values.mean(),color='red',linestyle='dashed',linewidth=1)
plt.title('Score Distribution')
```

```python
import lightgbm as lgb
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.model_selection import GridSearchCV
from sklearn.model_selection import cross_val_score

trainDf =  pd.read_csv("chess/training_data.csv")
testDf = pd.read_csv("chess/test_data.csv")

```

```python
x=trainDf.copy().drop(["Score"],axis=1)
y=trainDf.copy()["Score"]

xTest = testDf.copy().drop(["Month #"], axis=1)

lgb_model = lgb.LGBMRegressor(
    categorical_feature= [0],
    task = 'predict',
    application = 'regression',
    objective = 'mae',
    boosting_type="gbdt",
    num_iterations = 2600,
    learning_rate = 0.09,
    num_leaves=9,
    tree_learner='feature',
    max_depth =12,
    min_data_in_leaf=10,
    bagging_fraction = 1,
    bagging_freq = 100,
    reg_sqrt='True',
    metric ='mae',
    feature_fraction = 0.8,
    random_state=42)
```

```python
lgb_model.fit(x,y)
yTest=lgb_model.predict(xTest)
predictions=pd.DataFrame(testDf["Month #"].copy())
predictions["Score"]=yTest[:]
predictions.Score=predictions.Score.apply(lambda x:round(x))
print(predictions)
```
