# Ex.No: 1B - CONVERSION OF NON STATIONARY TO STATIONARY DATA->
# Date: 08-03-2024

## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
## ALGORITHM:
1. Import the required packages like pandas and numpy.
2. Read the data using the pandas.
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
   
## PROGRAM:
### REGULAR DIFFERENCING:
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data=pd.read_csv("/content/AirPassengers.csv",parse_dates=['Month'],index_col='Month')
data.head()
passengers['shifted_value']=passengers['#Passengers'].shift(1)
passengers['difference_value']=passengers['#Passengers']-passengers['shifted_value']
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### SEASONAL ADJUSTMENT:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv("/content/AirPassengers.csv",parse_dates=['Month'],index_col='Month')
passengers=pd.DataFrame(data)
result=seasonal_decompose(passengers['#Passengers'],model='additive',period=1)
seasonal=result.seasonal
passengers['Seasonal_value']=passengers['#Passengers']-seasonal
passengers.dropna(inplace=True)
print(passengers)
passengers.plot(kind='line')
```
### LOG TRANSFORMATION:
```
import numpy as np
import pandas as pd
data= pd.read_csv('AirPassengers.csv')
data.head()
data.dropna(inplace=True)
x=data['Month']
y=data['#Passengers']
data_log=np.log(data['#Passengers'])
X=data['Month']
Y=data_log
import matplotlib.pyplot as plt
plt.plot(x,y)
plt.xlabel('Original Data')
plt.plot(X,Y)
plt.xlabel('Log- Transformed data')
```
## OUTPUT:

### REGULAR DIFFERENCING:
![image](https://github.com/Pradeeppachiyappan/TSA_EXP1B/assets/118707347/a6913ccd-6af3-4bde-936e-7db8dafcf4ee)

### SEASONAL ADJUSTMENT:
![image](https://github.com/Pradeeppachiyappan/TSA_EXP1B/assets/118707347/55f6aa76-413a-4c93-a6bc-cf3e6d701ef9)

### LOG TRANSFORMATION:
![image](https://github.com/Pradeeppachiyappan/TSA_EXP1B/assets/118707347/94653b8a-83b3-4a58-b436-f111428e891e)

![image](https://github.com/Pradeeppachiyappan/TSA_EXP1B/assets/118707347/5dfe701a-c483-4140-8aa4-71ad6c081955)

## RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
