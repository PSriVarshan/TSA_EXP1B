### Developed by: Sri Varshan P
### Register Number: 212222240104
### Date :

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on Russian Equipment Losses specificalyy Armored Personnel Carrier [APC]

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.

### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```
```py
file_path = 'russia_losses_equipment.csv'
data = pd.read_csv(file_path)
```

```py
data['date'] = pd.to_datetime(data['date'])  # Convert 'date' to datetime
data.set_index('date', inplace=True)  # Set 'date' as index
data.fillna(method='ffill', inplace=True)  # Forward fill missing values
```

```py
apc_data = data['APC']
```
```py
# Plot Original Data for APC
plt.figure(figsize=(14, 8))
plt.plot(apc_data, label='APC')
plt.title('Original APC Data')
plt.legend()
plt.show()
```
```py
# Regular Differencing for APC
apc_diff = apc_data.diff().dropna()
```
```py
# Plot Differenced Data for APC
plt.figure(figsize=(14, 8))
plt.plot(apc_diff, label='APC (Diff)')
plt.title('Differenced APC Data')
plt.legend()
plt.show()
```
```py
# Log Transformation for APC
apc_log = np.log(apc_data + 1)  # Adding 1 to avoid log(0)
```
```py
# Plot Log-Transformed Data for APC
plt.figure(figsize=(14, 8))
plt.plot(apc_log, label='APC (Log)')
plt.title('Log-Transformed APC Data')
plt.legend()
plt.show()
```
```py
# Seasonal Adjustment (using moving average) for APC
apc_seasonal_adjustment = apc_log - apc_log.rolling(window=7).mean()
apc_seasonal_adjustment.dropna(inplace=True)
```
```py
plt.figure(figsize=(14, 8))
plt.plot(apc_seasonal_adjustment, label='APC (Seasonally Adjusted)')
plt.title('Seasonally Adjusted Log-Transformed APC Data')
plt.legend()
plt.show()
```

### OUTPUT:

![image](https://github.com/user-attachments/assets/e766d30d-0fc3-4870-9e17-cd6f71c8801c)


REGULAR DIFFERENCING:

![image](https://github.com/user-attachments/assets/88676382-a9c9-4cd1-8c8a-34ca6040b385)

SEASONAL ADJUSTMENT:

![image](https://github.com/user-attachments/assets/dbc6ac64-e530-4af5-b6b0-bf5a19900a25)


LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/1df8feac-33ed-4da5-a226-9f32904c2a21)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
