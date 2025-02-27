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


# Result
          <<include your Result here>>
