# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on DailyDelhiClimateTest.csv

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
## import pandas as pd\

Load the dataset\
data = pd.read_csv('DailyDelhiClimateTest.csv', parse_dates=['date'], index_col='date')\
Inspect the first few rows\
print(data.head())\
import matplotlib.pyplot as plt\

## Plot the temperature over time\
plt.figure(figsize=(10, 6))\
plt.plot(data['meantemp'], label='Mean Temperature')\
plt.title('Daily Mean Temperature in Delhi')\
plt.xlabel('Date')\
plt.ylabel('Temperature (°C)')\
plt.legend()\
plt.show()\
from statsmodels.tsa.seasonal import seasonal_decompose\

## Perform additive decomposition (can also try 'multiplicative' based on the nature of the data)\
decomposition = seasonal_decompose(data['meantemp'], model='additive', period=365)\

## Plot the decomposition\
decomposition.plot()\
plt.show()\
Calculate the 30-day moving average\
data['mean_temp_30d_ma'] = data['meantemp'].rolling(window=30).mean()\

## Plot the moving average along with the original data\
plt.figure(figsize=(10, 6))\
plt.plot(data['meantemp'], label='Mean Temperature')\
plt.plot(data['mean_temp_30d_ma'], label='30-day Moving Average', color='red')\
plt.title('Mean Temperature with 30-Day Moving Average')\
plt.xlabel('Date')\
plt.ylabel('Temperature (°C)')\
plt.legend()\
plt.show()\

### OUTPUT:
![Screenshot 2024-10-16 091515](https://github.com/user-attachments/assets/72973807-41b0-4225-8ff9-1d343d893cab)

TREND PLOT REPRESENTATION :
![Screenshot 2024-10-16 091250](https://github.com/user-attachments/assets/68f52cf5-3919-4b39-8abe-616fafdca0a1)


PLOTTING THE DATA:

![Screenshot 2024-10-16 091214](https://github.com/user-attachments/assets/6e353a29-343c-4a51-adfe-2d7df2242ee2)

SEASONAL PLOT REPRESENTATION :


![Screenshot 2024-10-16 091204](https://github.com/user-attachments/assets/d9b92603-1e7d-4e5f-a270-61d37d7cc038)

### RESULT:
Thus we have created the python code for the time series analysis and decomposition on DailyDelhiClimateTest.csv.
