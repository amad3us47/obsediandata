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

```

```python
data=pd.read_csv("RTAData.csv",low_memory=False)
data.head()
```

```python
data.info
```

```python
historical_data=pd.read_csv("RTAHistorical.csv")
historical_data.describe()
```

```python
error_data=pd.read_csv("RTAError.csv",low_memory=False)
error_data.head()
```

```python
route_data=pd.read_csv("RouteLengthApprox.csv")
route_data.head()
```

```python
route_data['Approximate length'].hist(bins=50)
```

```python
route_id=40015
data[str(route_id)]=pd.to_numeric(data[str(route_id)],errors='coerce')
plt.figure(figsize=(12,6))
plt.plot(data[str(route_id)],label=f'Route{route_id}')
plt.xlabel('Time Interval')
plt.ylabel('Travel Time (in deciseconds)')
plt.title(f'Travel Time for Route {route_id}')
plt.legend()
plt.show()
```
