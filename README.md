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
