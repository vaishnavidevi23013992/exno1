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
REGISTRATION NUMBER:212223040230
NAME: VAISHNAVIDEVI V
```
```            
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/457ca89c-9e58-4cc5-a255-a316927a5d73)
```
df.head(6)
```
![image](https://github.com/user-attachments/assets/d4420534-59d3-4db1-914b-f861273bfab4)
```
df.tail(6)
```
![image](https://github.com/user-attachments/assets/fb737648-f211-4b6a-a463-a2117da7ef3c)
```
df.isnull()
```
![image](https://github.com/user-attachments/assets/42a6ff19-7522-4e3a-b93f-270d67433c30)
```
df.notnull()
```
![image](https://github.com/user-attachments/assets/ade91f92-d1df-4813-ad2a-1f7a211cfaf5)
```
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/f2b8d7fa-564b-428c-a732-b2420cb9151f)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/26621a97-7b9f-4270-bace-0870a0012d73)
```
print(df.shape)
```
![image](https://github.com/user-attachments/assets/21b81666-68a5-4550-bdf5-3e376e8017af)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/feabec9b-69e1-4e4d-acd6-5aa21496bc8f)
## IQR
```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/d381e863-bb1b-4a55-8ad5-747255f69cc6)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/98ce0397-908f-4211-a5f7-45c1c5499ab9)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/22ef03d3-dd5b-4fb6-94ad-e43e68755394)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/7a4e3e74-4968-4c51-afad-83b931ff4f3a)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/2344d369-f25c-4cf0-b5ef-230b0dfeb3cb)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/236f51e9-85d8-4338-a1b0-7b83161b318a)
## Z-SCORE
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv('/content/heights.csv')
dataset
```
![image](https://github.com/user-attachments/assets/b613f432-2538-475a-ace1-5e7b78a583f2)
```
df=pd.read_csv('/content/heights.csv')
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)

iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/028417b2-6e46-4f54-ab91-54f30c875cf7)
```
low=q1-1.4*iqr
low
```
![image](https://github.com/user-attachments/assets/c4839b50-13ad-42a0-b093-120b943fe7d8)
```
high=q3+1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/d835c43f-fca7-4585-bd11-0b9b335ee879)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/790397b6-701c-410b-8d47-8cfb8bfe425c)
```
z=np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/a5b7ac34-3654-43cf-ba42-471ee862918b)
```
df1=df[z<3]
df
```

![image](https://github.com/user-attachments/assets/b87be80a-3045-4401-b84c-3a1cd7d915dc)


# Result
   Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.       
