# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 18/08/25

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
### Name : Rehan Jeyan
### Regno: 212223040167
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Group dataset into time series (average price per year)
yearly_prices = df.groupby('year')['price'].mean()

# Convert to DataFrame with proper index
ts = pd.DataFrame(yearly_prices)
ts.index = pd.to_datetime(ts.index, format='%Y')  # convert year to datetime
ts.rename(columns={'price': 'Average Price'}, inplace=True)

# 1. Regular differencing
ts['Regular Difference'] = ts['Average Price'].diff()

# 2. Seasonal decomposition
result = seasonal_decompose(ts['Average Price'], model='additive', period=1)
ts['Seasonal Adjustment'] = ts['Average Price'] - result.seasonal

# 3. Log transformation
ts['Log Transformation'] = np.log(ts['Average Price'])

# --- Plot each separately ---

# Original
plt.figure(figsize=(10, 5))
plt.plot(ts['Average Price'], marker='o')
plt.title('Original Data (Average Price per Year)')
plt.xlabel('Year')
plt.ylabel('Price')
plt.show()

# Differencing
plt.figure(figsize=(10, 5))
plt.plot(ts['Regular Difference'], color='orange', marker='o')
plt.title('Regular Differencing')
plt.xlabel('Year')
plt.ylabel('Price Difference')
plt.show()

# Seasonal Adjustment
plt.figure(figsize=(10, 5))
plt.plot(ts['Seasonal Adjustment'], color='green', marker='o')
plt.title('Seasonal Adjustment')
plt.xlabel('Year')
plt.ylabel('Adjusted Price')
plt.show()

# Log Transformation
plt.figure(figsize=(10, 5))
plt.plot(ts['Log Transformation'], color='red', marker='o')
plt.title('Log Transformation')
plt.xlabel('Year')
plt.ylabel('Log(Price)')
plt.show()

```
### OUTPUT:

#### ORIGINAL DATA:
<img width="868" height="470" alt="image" src="https://github.com/user-attachments/assets/2f90f68c-b0e8-40bb-a3b9-d9a58fe51d06" />



#### REGULAR DIFFERENCING:
<img width="859" height="470" alt="image" src="https://github.com/user-attachments/assets/a8a3496c-8118-40a5-a6c0-075e4b573ff1" />


#### SEASONAL ADJUSTMENT:
<img width="868" height="470" alt="image" src="https://github.com/user-attachments/assets/ee9331e5-a607-459b-ad8f-68f080e8d193" />



#### LOG TRANSFORMATION:
<img width="855" height="470" alt="image" src="https://github.com/user-attachments/assets/8b8bde72-4b76-4405-b8b4-c1778444e3b0" />




### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
