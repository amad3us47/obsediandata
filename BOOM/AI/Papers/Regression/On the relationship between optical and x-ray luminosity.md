Link to paper -> https://arxiv.org/pdf/astro-ph/9412029

The paper is all about In the context of the paper **"The Cosmological Constant is Probably Zero"**, linear regression is employed as a statistical tool to analyze relationships between observational data and theoretical predictions, specifically in assessing cosmological parameters.


``` python 
import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import curve_fit
```

numpy (np) is a library used to work with arrays
metplotlib (plt)  is a library used to create plot and visualization
scipy.optimize (curve_fit)  is a tool to fit a curve (or a mathematical model) to your data. It finds the best parameters for your model.

``` python
redshift = np.array([0.01, 0.1, 0.2, 0.3, 0.4, 0.5]) distance_modulus = np.array([33.1, 38.5, 40.2, 41.5, 42.6, 43.4])
```

