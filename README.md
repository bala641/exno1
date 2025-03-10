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
exp=pd.read_csv("/content/SAMPLEIDS.csv")
exp
```
![ia0qkk9q](https://github.com/user-attachments/assets/26f9537a-3229-49a5-8b7a-483650c5c3e1)
```
exp.isnull().sum()
```
![8sdm7p0j](https://github.com/user-attachments/assets/ec9e67e5-0167-43ea-90dc-8eccab7aeaec)
```
exp.isnull().any()
```
![76w7ankh](https://github.com/user-attachments/assets/cd01b3c3-8924-4c63-8fe0-6ad8c1869696)
```
exp.dropna()
```
![gwcocesn](https://github.com/user-attachments/assets/68e1ce81-e717-425d-bcd0-2519753ecaf4)
```
exp.fillna(0)
```
![lcf3co4x](https://github.com/user-attachments/assets/8cfe559c-c12c-4364-9563-d1d251ebda36)
```
exp.fillna(method="ffill")
```
![sem6g1jr](https://github.com/user-attachments/assets/661e742d-e54f-4b0f-b630-863eaf7fd46e)
```
exp.fillna(method="bfill")
```
![2pnbv1i3](https://github.com/user-attachments/assets/9516d1e2-8f00-454e-8854-5ac7a9ca02dd)
```
exp_dropped=exp.dropna()
exp_dropped
```
![gwcocesn](https://github.com/user-attachments/assets/81e5da98-a8fc-4f04-ad80-59c170dc2788)
```
exp.fillna({'NAME':'MOHAN','GENDER':'MALE','ADDRESS':'THIRUVOTTIYUR','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![vg31r4cc](https://github.com/user-attachments/assets/9e1fab29-434b-4f61-a6f5-2041fdca2239)

IQR(Inter Quartile Range)

```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
         
