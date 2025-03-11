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

# IQR(Inter Quartile Range)

```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```
![ofailk6e](https://github.com/user-attachments/assets/533c65c6-02d8-4e09-85e7-feb262c45fd8)
```
ir.describe()
```
![t73zf0nh](https://github.com/user-attachments/assets/d200cdae-73ff-43e9-97bd-35975b44baa8)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![lb0k2gkp](https://github.com/user-attachments/assets/dae2a729-ea35-42c5-8411-eb02df8ba1f5)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
![Screenshot 2025-03-11 193055](https://github.com/user-attachments/assets/91ba6240-b272-43c0-8544-ed59270ea7c7)
```
outlier=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
outlier['sepal_width']
```
![Screenshot 2025-03-11 193103](https://github.com/user-attachments/assets/9d9a60b6-0358-4cc5-a23e-6619889d08f0)
```
o=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
print(o)
```
![Screenshot 2025-03-11 193136](https://github.com/user-attachments/assets/8aabd3ff-1b79-4a2c-8f03-3e948c1b4865)
```
sns.boxplot(x='sepal_width',data=o)
```
![Screenshot 2025-03-11 193152](https://github.com/user-attachments/assets/5785adcc-ed35-4842-a40a-b37faa904b69)

# Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
data_set=pd.read_csv("/content/heights.csv")
data_set
```
![Screenshot 2025-03-11 193203](https://github.com/user-attachments/assets/8d675f84-938d-437a-88cc-8b1ed7fb2a6f)
```
z=pd.read_csv("/content/heights.csv")
q1=z['height'].quantile(0.25)
q2=z['height'].quantile(0.50)
q3=z['height'].quantile(0.75)
iqr=q3-q1
print(iqr)
```
![Screenshot 2025-03-11 193211](https://github.com/user-attachments/assets/cae9563c-cd34-4aae-9a39-f11418ba6b4b)
```
low = q1-1.5*iqr
print(low)
```
![Screenshot 2025-03-11 193221](https://github.com/user-attachments/assets/b5f1e06b-c2e5-45f6-b1be-55a9d885c97b)
```
high = q3+1.5*iqr
print(high)
```
![Screenshot 2025-03-11 193232](https://github.com/user-attachments/assets/dae3ea24-f5d6-4312-95f2-3185e3f739ab)
```
z1=z[((z['height']>=low)&(z['height']<=high))]
z1
```
![Screenshot 2025-03-11 193302](https://github.com/user-attachments/assets/bf5b4250-a528-4bfe-a0e7-0ee1fd5788ee)

```
z=np.abs(stats.zscore(z['height']))
z
```
![Screenshot 2025-03-11 193321](https://github.com/user-attachments/assets/5149c272-a474-45dd-93fa-f568e66f7e51)
```
z1=z[z<3]
z1
```
![Screenshot 2025-03-11 193339](https://github.com/user-attachments/assets/6567774f-93ab-4e82-bc9f-36dfbb0f5b0d)

# Resuls
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
         
