```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
train_data=pd.read_csv("RTAData.csv",low_memory=False)
length=pd.read_csv("RouteLengthApprox.csv")
hist=pd.read_csv("RTAHistorical.csv")
error=pd.read_csv("RTAError.csv",low_memory=False)
sample=pd.read_csv("sampleEntry.csv")
```


```python
train_data.head()
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
      <th>Unnamed: 0</th>
      <th>40010</th>
      <th>40015</th>
      <th>40020</th>
      <th>40025</th>
      <th>40030</th>
      <th>40035</th>
      <th>40040</th>
      <th>40045</th>
      <th>40050</th>
      <th>...</th>
      <th>41120</th>
      <th>41125</th>
      <th>41130</th>
      <th>41135</th>
      <th>41140</th>
      <th>41145</th>
      <th>41150</th>
      <th>41155</th>
      <th>41160</th>
      <th>Unnamed: 62</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2010-03-01 14:58</td>
      <td>821</td>
      <td>209</td>
      <td>828</td>
      <td>258</td>
      <td>246</td>
      <td>167</td>
      <td>925</td>
      <td>1800</td>
      <td>548</td>
      <td>...</td>
      <td>329</td>
      <td>1020</td>
      <td>471</td>
      <td>440</td>
      <td>226</td>
      <td>262</td>
      <td>756</td>
      <td>206</td>
      <td>793</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2010-03-01 15:01</td>
      <td>804</td>
      <td>209</td>
      <td>804</td>
      <td>248</td>
      <td>246</td>
      <td>174</td>
      <td>1200</td>
      <td>1872</td>
      <td>565</td>
      <td>...</td>
      <td>329</td>
      <td>1032</td>
      <td>471</td>
      <td>440</td>
      <td>226</td>
      <td>264</td>
      <td>743</td>
      <td>204</td>
      <td>786</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2010-03-01 15:04</td>
      <td>892</td>
      <td>212</td>
      <td>801</td>
      <td>237</td>
      <td>235</td>
      <td>180</td>
      <td>1296</td>
      <td>1672</td>
      <td>543</td>
      <td>...</td>
      <td>329</td>
      <td>1009</td>
      <td>471</td>
      <td>426</td>
      <td>219</td>
      <td>264</td>
      <td>781</td>
      <td>213</td>
      <td>781</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2010-03-01 15:07</td>
      <td>857</td>
      <td>214</td>
      <td>821</td>
      <td>243</td>
      <td>237</td>
      <td>180</td>
      <td>1293</td>
      <td>1612</td>
      <td>545</td>
      <td>...</td>
      <td>329</td>
      <td>1009</td>
      <td>466</td>
      <td>445</td>
      <td>229</td>
      <td>274</td>
      <td>766</td>
      <td>218</td>
      <td>788</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2010-03-01 15:10</td>
      <td>849</td>
      <td>222</td>
      <td>834</td>
      <td>252</td>
      <td>243</td>
      <td>174</td>
      <td>1143</td>
      <td>1612</td>
      <td>517</td>
      <td>...</td>
      <td>329</td>
      <td>1020</td>
      <td>483</td>
      <td>440</td>
      <td>226</td>
      <td>267</td>
      <td>782</td>
      <td>213</td>
      <td>791</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 63 columns</p>
</div>




```python
train_data.shape
```




    (120822, 63)


