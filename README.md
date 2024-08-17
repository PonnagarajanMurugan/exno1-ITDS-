# Exno:1
Data Cleaning Process

```
NAME : PON NAGARAJAN M
DEPT : CSE
REG NO : 212222040115
```
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
```py
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2024-08-17 140317](https://github.com/user-attachments/assets/74275829-aeb3-4e5b-a015-346843293542)
```py
df.head(5)
```
![Screenshot 2024-08-17 140556](https://github.com/user-attachments/assets/04474ead-e8be-4a23-815d-892d2f57d69a)
```py
df.tail(4)
```
![Screenshot 2024-08-17 140644](https://github.com/user-attachments/assets/a26565e2-61ff-4d8b-a109-345bb8c00215)
```py
df.isnull()
```
![image](https://github.com/user-attachments/assets/4f6b96a1-7008-45b1-b42a-1c45454482b5)
```py
df.notnull()
```
![image](https://github.com/user-attachments/assets/8c946ee2-fb7b-4ff2-94a5-494bdb6dc3e5)
```py
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/d60da26d-27d9-4326-8469-4d1be9a2ab56)
```py
df.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/3c90e592-4111-47cb-9dff-60e7b93bc623)
```py
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/9ebe716e-009b-43e0-9d00-a0374fef287c)
```py
print(df.shape)
```
![image](https://github.com/user-attachments/assets/9723e228-b796-4da7-91a3-83ca849ae192)
```py
df.describe()
```
![image](https://github.com/user-attachments/assets/21b4bc22-31a5-4620-81d0-bd7d9193cc3c)
```py
import pandas as pd
import seaborn as sns
ir=pd.read_csv("iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/a6bcbe03-df82-43ce-885b-c384150ccdb2)
```py
ir.describe()
```
![image](https://github.com/user-attachments/assets/145b75d6-8af8-4b16-8d1b-48c2115c583d)
```py
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/e3e79b37-0844-41e8-ba28-2395e12697b8)
```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/d8f70066-fd91-4b43-b394-c0ea864c3952)
```py
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/786e7d09-01c7-4d58-9c66-7e2f0a75916a)
```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/f3e38d97-659f-4dd7-a51c-b853b177936d)
```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/13eec68a-9bdb-481c-bc59-e706e19a80b2)
```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

ds=pd.read_csv("heights.csv")
ds
```
![image](https://github.com/user-attachments/assets/2fa5e98f-d1e1-4bfb-8005-a96448b0eeb9)
```py
ds=pd.read_csv('/content/heights.csv')
q1=ds['height'].quantile(0.25)
q2=ds['height'].quantile(0.5)
q3=ds['height'].quantile(0.75)

iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/f0232a63-a954-470b-9c84-d5f5c6eafbe3)
```py
low=q1-1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/463a1c8a-f690-4206-aadb-a527d037df67)
```py
high=q3+1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/ed2bf039-447e-45b0-afaa-25727d9832dc)
```py
ds1=ds[((ds['height']>=low)&(ds['height']<=high))]
ds1
```
![image](https://github.com/user-attachments/assets/3c15586c-b595-422c-9a59-594ed826e96a)
```py
z=np.abs(stats.zscore(ds['height']))
z
```
![image](https://github.com/user-attachments/assets/de41bfbc-d798-4db9-8a7b-246e0c1b670b)
```py
ds1=ds[z<3]
ds1
```
![image](https://github.com/user-attachments/assets/237db6e7-7719-41f8-821c-52efb50effb1)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
