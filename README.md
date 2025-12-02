# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)


### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

df = pd.read_csv("/content/tsla_2014_2023.csv")
data = df["close"].values  

N = len(data)
lags = range(35)
autocorr_values = []
mean_data = np.mean(data)
variance_data = np.var(data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)  # removed use_line_collection
plt.title("Autocorrelation of Tesla Close Prices")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.grid(True)
plt.show()

```
### OUTPUT:
<img width="1698" height="1090" alt="Screenshot 2025-09-02 091026" src="https://github.com/user-attachments/assets/79a106a8-d014-4a8c-92bf-c33412289e57" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
