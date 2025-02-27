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
Name: Pranavesh Saikumar
RegNo: 212223040149
```
## Data Cleaning Process
```
import pandas as pd
import numpy as np

df = pd.read_csv("C:/Users/admin/Documents/DS exps/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/4be44419-a186-417a-93ca-eab6fdf0a7c0)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/3870ae66-54fa-4aad-9f8e-8ba32745e0f7)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/ce5885ef-8768-4ac4-b647-6f8e233e81ed)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/21705b9d-2163-428c-b485-6d6a91806434)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/8eb62126-61fa-4603-aca2-a2c072b00db9)

```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/ae23a52b-416b-47c9-9af2-908533efc441)

```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/d723a7d9-16ce-4b66-a6db-930c576a761b)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/919a314a-3cd6-4405-a0d1-db475277b659)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/bb8ec85a-04c3-49b1-9328-bcc77ee2620a)

## Outlier Detection And Removal
## IQR
```
import pandas as pd
import seaborn as sns

ir = pd.read_csv("C:/Users/admin/Documents/DS exps/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/0e974456-5c26-41f3-84ed-94aa7b5bd366)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/2141211f-2167-4674-90e5-a0482eeac525)

```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/9062728b-6260-469f-83da-dbaafcc0c398)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/af121401-f310-49cc-a016-90730dada5fa)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/8dd0dbe8-f769-45a2-bba5-961c55c63004)

```
delid = ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/8d0f3a4d-41d3-4e8f-99f1-01ee2ea0a825)

```
sns.boxplot(x='sepal_width',data=delid)
```

## Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

data = pd.read_csv("C:/Users/admin/Documents/DS exps/heights.csv") 
data
```
![image](https://github.com/user-attachments/assets/9cc848fd-b719-4d1e-9f7d-00739458da66)

```
q1 = data['height'].quantile(0.25)
q2 = data['height'].quantile(0.5)
q3 = data['height'].quantile(0.75)

iqr = q3 - q1
iqr
```
![image](https://github.com/user-attachments/assets/4845b4a0-f94a-4e63-b9bf-a74048a38c05)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/6afdde5d-f9d3-4c83-aa3b-78bf9fed7f52)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/7d0e0983-7ad1-4d6e-a011-9d670d238b33)

```
data1 = data[((data['height'] >=low)& (data['height'] <=high))]
data1
```
![image](https://github.com/user-attachments/assets/b4c78ef3-8d11-48a7-adb7-235c5fdee1d5)

```
z = np.abs(stats.zscore(data['height']))
z
```
![image](https://github.com/user-attachments/assets/b93d8116-97ff-4599-a1b1-c8fb6d398abf)

```
data1 = data[z<3]
data1
```
![image](https://github.com/user-attachments/assets/44a0d4e6-29bc-4f4a-9cc3-6bf2993499ce)



# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
