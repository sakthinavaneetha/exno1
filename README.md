# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/b58e04b8-f3c6-4a1b-8397-a8f7fdf3e07e)

```
df.isnull()
```

![image](https://github.com/user-attachments/assets/f4fb5518-6013-424e-8cc0-4bee230e0e03)

```
df.isnull().any()
```

![image](https://github.com/user-attachments/assets/3b63ae4c-b8f6-4ef7-86b1-816c4065acb6)

```
df.dropna()
```

![image](https://github.com/user-attachments/assets/d4166224-d8da-43ca-b1ec-32f9552d3b9c)

```
df.fillna(0)
```

![image](https://github.com/user-attachments/assets/ef05d0a7-6523-4eb1-bd32-16f6e94ffa16)

```
df.fillna(method = 'ffill')
```

![image](https://github.com/user-attachments/assets/e2531b27-15d1-48c5-838c-ac2884b56abf)

```
df.fillna(method = 'bfill')
```

![image](https://github.com/user-attachments/assets/b33b60ea-ac89-4111-b311-3e7dbec4f5a0)

```
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/36f837a2-65ec-4cee-9549-c52cce979b8b)


                           Z-Score
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv("heights.csv")
dataset

![image](https://github.com/user-attachments/assets/bea615d0-c852-46ee-ba47-2f13ed2795a9)

df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)

iqr = q3-q1
iqr

0.9249999999999998

low = q1 - 1.5*iqr
low

3.8625000000000003

high = q3 + 1.5*iqr
high

7.5625

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1

![image](https://github.com/user-attachments/assets/4fe360ae-d925-467f-a906-73022cbba142)

z = np.abs(stats.zscore(df['height']))
z

![image](https://github.com/user-attachments/assets/0ec709aa-f9e4-47f5-a8b4-927c21c483e1)

df1 = df[z<3]
df1

![image](https://github.com/user-attachments/assets/0611ef15-972b-47a4-8b73-32ae0dd36e85)
      
            
IQR(Inter Quartile Range)

import pandas as pd
import seaborn as sns
ir=pd.read_csv('iris.csv')
ir
![image](https://github.com/user-attachments/assets/88823b30-bd8d-43cd-8748-b7693f5eb18e)

ir.describe()

![image](https://github.com/user-attachments/assets/c3d69d84-3e8c-4d50-88c0-3995fafc2441)

sns.boxplot(x='sepal_width',data=ir)

![image](https://github.com/user-attachments/assets/62c76153-0237-48ef-8de9-bbeceadc59eb)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

3.3

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

![image](https://github.com/user-attachments/assets/6f9dbc48-7f4a-45ec-9449-637e220e1a70)

sns.boxplot(x='sepal_width',data=delid)


![image](https://github.com/user-attachments/assets/077fb837-9746-452b-baf6-d937b0c4ce75)


                                                
# Result
          Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method
