### Name: Deepika p
### Register No: 212223240024

# Ex.No: 1B CONVERSION OF NON STATIONARY TO STATIONARY DATA

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international DelhiDelhi climate test.
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('delhi_climate_test.csv', index_col='Date', parse_dates=True)

# Plot the original data
df['Temperature'].plot(figsize=(10,6))
plt.title('Original Daily Delhi Climate Data')
plt.show()
from statsmodels.tsa.seasonal import seasonal_decompose

# Perform seasonal decomposition (assuming daily data with yearly seasonality: period=365)
decomposition = seasonal_decompose(df['Log_Temperature'], model='additive', period=365)

# Extract and plot the seasonal component
decomposition.seasonal.plot(figsize=(10,6))
plt.title('Seasonal Component')
plt.show()

# Remove the seasonal component to get seasonally adjusted data
df['Seasonally_Adjusted_Temperature'] = df['Log_Temperature'] - decomposition.seasonal

# Plot the seasonally adjusted data
df['Seasonally_Adjusted_Temperature'].plot(figsize=(10,6))
plt.title('Seasonally Adjusted and Log-Transformed Data')
plt.show()
from statsmodels.tsa.stattools import adfuller

# Perform ADF test on the seasonally adjusted data
adf_result = adfuller(df['Seasonally_Adjusted_Temperature'].dropna())
print(f'ADF Statistic: {adf_result[0]}')
print(f'p-value: {adf_result[1]}')

# Interpretation:
# p-value < 0.05 indicates the time series is stationary
                            
```
### OUTPUT:

### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/5adb711c-fed8-47f9-8734-08d7aed40d3b)

### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/4c7d73c2-e1d3-4fd5-8d5c-aceb91490ef7)

### LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/c05b0246-e203-4888-a127-a61bd1d8ca93)

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on DailyDelhi climate test.
