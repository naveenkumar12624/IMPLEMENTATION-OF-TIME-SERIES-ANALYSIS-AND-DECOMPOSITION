# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 
### Name: Naveen Kumar S
### Register Number: 212221240033

## AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

## PROGRAM:
```python
# Step 1: Import the required packages
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import statsmodels.api as sm
from datetime import datetime, timedelta

# Step 2: Read the data using pandas
data = pd.read_csv('C:/Users/lenovo/Downloads/archive (2)/NVIDIA/NvidiaStockPrice.csv', parse_dates=['Date'], index_col='Date')

# Step 3: Perform the decomposition process for the required data
# Resample the data to monthly frequency and take the mean
monthly_data = data['Close'].resample('M').mean()

# Define the start and end date for the plot
start_date = '2019-01-01'  # Start from January 2019 to Show variations
num_years = 5               # Number of years to plot
end_date = (datetime.now() + timedelta(days=365*num_years)).strftime('%Y-%m-%d')

# Filter the data for the specified date range
filtered_data = monthly_data[start_date:end_date]

# Perform seasonal decomposition
decomposition = sm.tsa.seasonal_decompose(filtered_data, model='additive')

# Step 4: Plot the data according to need
plt.figure(figsize=(14, 10))

# Plot the original time series
plt.subplot(411)
plt.plot(filtered_data, label='Monthly Average Close Price', color='blue')
plt.title(f'Monthly Average Close Price of Nvidia Stock ({start_date} to {end_date})')
plt.legend(loc='upper left')

# Plot the trend
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.title('Trend')
plt.legend(loc='upper left')

# Plot the seasonal component
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend(loc='upper left')

# Plot the residuals
plt.subplot(414)
plt.plot(decomposition.resid, label='Residuals', color='red')
plt.title('Residuals')
plt.legend(loc='upper left')

plt.tight_layout()
plt.show()
```

## OUTPUT:
### Original Time Series
![image](https://github.com/user-attachments/assets/6c1145b4-2885-46ce-afec-17309ea9562b)

### Trend Component
![image](https://github.com/user-attachments/assets/bf24754d-6076-4986-a4d1-9e697e41cd20)

### Seasonal Component
![image](https://github.com/user-attachments/assets/6ca85009-4ed9-4f7b-be2e-5d08127968b1)

### Residual Component
![image](https://github.com/user-attachments/assets/49c0e7f0-1209-43c8-8bad-5e159d36e5be)


## RESULT:
Thus, the python code for the time series analysis and decomposition is successful.
