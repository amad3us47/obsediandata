```python
import pandas as pd

```


```python
train=pd.read_csv("overfitting.csv")
```


```python
train
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>case_id</th>
      <th>train</th>
      <th>Target_Practice</th>
      <th>Target_Leaderboard</th>
      <th>Target_Evaluate</th>
      <th>var_1</th>
      <th>var_2</th>
      <th>var_3</th>
      <th>var_4</th>
      <th>var_5</th>
      <th>...</th>
      <th>var_191</th>
      <th>var_192</th>
      <th>var_193</th>
      <th>var_194</th>
      <th>var_195</th>
      <th>var_196</th>
      <th>var_197</th>
      <th>var_198</th>
      <th>var_199</th>
      <th>var_200</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0.660</td>
      <td>0.106</td>
      <td>0.434</td>
      <td>0.387</td>
      <td>0.903</td>
      <td>...</td>
      <td>0.015</td>
      <td>0.377</td>
      <td>0.479</td>
      <td>0.050</td>
      <td>0.395</td>
      <td>0.123</td>
      <td>0.833</td>
      <td>0.461</td>
      <td>0.990</td>
      <td>0.105</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0.844</td>
      <td>0.813</td>
      <td>0.030</td>
      <td>0.939</td>
      <td>0.721</td>
      <td>...</td>
      <td>0.112</td>
      <td>0.048</td>
      <td>0.088</td>
      <td>0.860</td>
      <td>0.560</td>
      <td>0.346</td>
      <td>0.511</td>
      <td>0.883</td>
      <td>0.858</td>
      <td>0.599</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.560</td>
      <td>0.567</td>
      <td>0.568</td>
      <td>0.434</td>
      <td>0.414</td>
      <td>...</td>
      <td>0.874</td>
      <td>0.236</td>
      <td>0.599</td>
      <td>0.602</td>
      <td>0.005</td>
      <td>0.493</td>
      <td>0.122</td>
      <td>0.395</td>
      <td>0.782</td>
      <td>0.943</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0.681</td>
      <td>0.245</td>
      <td>0.909</td>
      <td>0.785</td>
      <td>0.738</td>
      <td>...</td>
      <td>0.219</td>
      <td>0.691</td>
      <td>0.261</td>
      <td>0.031</td>
      <td>0.968</td>
      <td>0.353</td>
      <td>0.798</td>
      <td>0.104</td>
      <td>0.944</td>
      <td>0.090</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0.846</td>
      <td>0.431</td>
      <td>0.805</td>
      <td>0.237</td>
      <td>0.465</td>
      <td>...</td>
      <td>0.704</td>
      <td>0.242</td>
      <td>0.089</td>
      <td>0.605</td>
      <td>0.577</td>
      <td>0.043</td>
      <td>0.686</td>
      <td>0.070</td>
      <td>0.666</td>
      <td>0.572</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>19995</th>
      <td>19996</td>
      <td>0</td>
      <td>0</td>
      <td>-99</td>
      <td>-99</td>
      <td>0.731</td>
      <td>0.028</td>
      <td>0.758</td>
      <td>0.641</td>
      <td>0.964</td>
      <td>...</td>
      <td>0.161</td>
      <td>0.082</td>
      <td>0.445</td>
      <td>0.413</td>
      <td>0.021</td>
      <td>0.596</td>
      <td>0.861</td>
      <td>0.538</td>
      <td>0.779</td>
      <td>0.174</td>
    </tr>
    <tr>
      <th>19996</th>
      <td>19997</td>
      <td>0</td>
      <td>1</td>
      <td>-99</td>
      <td>-99</td>
      <td>0.825</td>
      <td>0.802</td>
      <td>0.765</td>
      <td>0.133</td>
      <td>0.446</td>
      <td>...</td>
      <td>0.822</td>
      <td>0.479</td>
      <td>0.608</td>
      <td>0.356</td>
      <td>0.397</td>
      <td>0.357</td>
      <td>0.410</td>
      <td>0.894</td>
      <td>0.204</td>
      <td>0.920</td>
    </tr>
    <tr>
      <th>19997</th>
      <td>19998</td>
      <td>0</td>
      <td>0</td>
      <td>-99</td>
      <td>-99</td>
      <td>0.021</td>
      <td>0.412</td>
      <td>0.842</td>
      <td>0.682</td>
      <td>0.958</td>
      <td>...</td>
      <td>0.004</td>
      <td>0.329</td>
      <td>0.369</td>
      <td>0.646</td>
      <td>0.308</td>
      <td>0.782</td>
      <td>0.173</td>
      <td>0.998</td>
      <td>0.212</td>
      <td>0.435</td>
    </tr>
    <tr>
      <th>19998</th>
      <td>19999</td>
      <td>0</td>
      <td>1</td>
      <td>-99</td>
      <td>-99</td>
      <td>0.364</td>
      <td>0.222</td>
      <td>0.397</td>
      <td>0.563</td>
      <td>0.180</td>
      <td>...</td>
      <td>0.422</td>
      <td>0.990</td>
      <td>0.148</td>
      <td>0.523</td>
      <td>0.536</td>
      <td>0.018</td>
      <td>0.203</td>
      <td>0.192</td>
      <td>0.281</td>
      <td>0.781</td>
    </tr>
    <tr>
      <th>19999</th>
      <td>20000</td>
      <td>0</td>
      <td>1</td>
      <td>-99</td>
      <td>-99</td>
      <td>0.165</td>
      <td>0.799</td>
      <td>0.229</td>
      <td>0.878</td>
      <td>0.303</td>
      <td>...</td>
      <td>0.927</td>
      <td>0.401</td>
      <td>0.630</td>
      <td>0.429</td>
      <td>0.256</td>
      <td>0.043</td>
      <td>0.069</td>
      <td>0.267</td>
      <td>0.531</td>
      <td>0.101</td>
    </tr>
  </tbody>
</table>
<p>20000 rows × 205 columns</p>
</div>




```python
train.isna().sum()
```




    case_id               0
    train                 0
    Target_Practice       0
    Target_Leaderboard    0
    Target_Evaluate       0
                         ..
    var_196               0
    var_197               0
    var_198               0
    var_199               0
    var_200               0
    Length: 205, dtype: int64




```python
list(train)
```




    ['case_id',
     'train',
     'Target_Practice',
     'Target_Leaderboard',
     'Target_Evaluate',
     'var_1',
     'var_2',
     'var_3',
     'var_4',
     'var_5',
     'var_6',
     'var_7',
     'var_8',
     'var_9',
     'var_10',
     'var_11',
     'var_12',
     'var_13',
     'var_14',
     'var_15',
     'var_16',
     'var_17',
     'var_18',
     'var_19',
     'var_20',
     'var_21',
     'var_22',
     'var_23',
     'var_24',
     'var_25',
     'var_26',
     'var_27',
     'var_28',
     'var_29',
     'var_30',
     'var_31',
     'var_32',
     'var_33',
     'var_34',
     'var_35',
     'var_36',
     'var_37',
     'var_38',
     'var_39',
     'var_40',
     'var_41',
     'var_42',
     'var_43',
     'var_44',
     'var_45',
     'var_46',
     'var_47',
     'var_48',
     'var_49',
     'var_50',
     'var_51',
     'var_52',
     'var_53',
     'var_54',
     'var_55',
     'var_56',
     'var_57',
     'var_58',
     'var_59',
     'var_60',
     'var_61',
     'var_62',
     'var_63',
     'var_64',
     'var_65',
     'var_66',
     'var_67',
     'var_68',
     'var_69',
     'var_70',
     'var_71',
     'var_72',
     'var_73',
     'var_74',
     'var_75',
     'var_76',
     'var_77',
     'var_78',
     'var_79',
     'var_80',
     'var_81',
     'var_82',
     'var_83',
     'var_84',
     'var_85',
     'var_86',
     'var_87',
     'var_88',
     'var_89',
     'var_90',
     'var_91',
     'var_92',
     'var_93',
     'var_94',
     'var_95',
     'var_96',
     'var_97',
     'var_98',
     'var_99',
     'var_100',
     'var_101',
     'var_102',
     'var_103',
     'var_104',
     'var_105',
     'var_106',
     'var_107',
     'var_108',
     'var_109',
     'var_110',
     'var_111',
     'var_112',
     'var_113',
     'var_114',
     'var_115',
     'var_116',
     'var_117',
     'var_118',
     'var_119',
     'var_120',
     'var_121',
     'var_122',
     'var_123',
     'var_124',
     'var_125',
     'var_126',
     'var_127',
     'var_128',
     'var_129',
     'var_130',
     'var_131',
     'var_132',
     'var_133',
     'var_134',
     'var_135',
     'var_136',
     'var_137',
     'var_138',
     'var_139',
     'var_140',
     'var_141',
     'var_142',
     'var_143',
     'var_144',
     'var_145',
     'var_146',
     'var_147',
     'var_148',
     'var_149',
     'var_150',
     'var_151',
     'var_152',
     'var_153',
     'var_154',
     'var_155',
     'var_156',
     'var_157',
     'var_158',
     'var_159',
     'var_160',
     'var_161',
     'var_162',
     'var_163',
     'var_164',
     'var_165',
     'var_166',
     'var_167',
     'var_168',
     'var_169',
     'var_170',
     'var_171',
     'var_172',
     'var_173',
     'var_174',
     'var_175',
     'var_176',
     'var_177',
     'var_178',
     'var_179',
     'var_180',
     'var_181',
     'var_182',
     'var_183',
     'var_184',
     'var_185',
     'var_186',
     'var_187',
     'var_188',
     'var_189',
     'var_190',
     'var_191',
     'var_192',
     'var_193',
     'var_194',
     'var_195',
     'var_196',
     'var_197',
     'var_198',
     'var_199',
     'var_200']




```python
train['train'].info()
```

    <class 'pandas.core.series.Series'>
    RangeIndex: 20000 entries, 0 to 19999
    Series name: train
    Non-Null Count  Dtype
    --------------  -----
    20000 non-null  int64
    dtypes: int64(1)
    memory usage: 156.4 KB
    


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




    Target_Practice    0.695610
    var_18             0.014434
    var_47             0.013790
    var_27             0.012909
    var_143            0.012330
                         ...   
    var_187            0.000000
    var_192            0.000000
    var_191            0.000000
    var_186            0.000000
    var_194            0.000000
    Length: 204, dtype: float64


