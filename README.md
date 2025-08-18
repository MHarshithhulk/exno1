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

# Coding and Output:
NAME : HARSHITH M
REG NO : 212224040206


import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
print(df)
![image](https://github.com/user-attachments/assets/d2f1a436-66c8-4128-8c89-6a41dff6c306)

![image](https://github.com/user-attachments/assets/ed136448-80c3-43b6-a19e-12ba2d8e7a02)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/3be521c4-3d3d-4ab0-8827-454050c2d7da)

df.isnull().any()

![image](https://github.com/user-attachments/assets/75105c83-dd70-434b-bf01-9163f5b9f9a4)

df.dropna()

![image](https://github.com/user-attachments/assets/a37bf9ef-6d18-4e26-8cf4-c6a3d9e85c20)

df.fillna(0)

![image](https://github.com/user-attachments/assets/20038ff3-8965-4877-815d-fcbe7ea22c4a)

df.fillna(method = 'ffill')

![image](https://github.com/user-attachments/assets/4975d77d-2425-440a-8465-c67b11ca2175)

df.fillna(method = 'bfill')

![image](https://github.com/user-attachments/assets/9485c4d3-ef99-426d-8fdb-01fb0bc55cef)

df_dropped = df.dropna()

df_dropped

![image](https://github.com/user-attachments/assets/d096a5f2-89cb-4c10-98bc-480d68150ebc)

df.fillna({'GENDER':'MALE','NAME':'HARSHITH M','ADDRESS':'RAJAMUNDRY','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

![image](https://github.com/user-attachments/assets/5683420d-8ef4-49bd-ae7d-055e5946a726)

ir=pd.read_csv('/content/iris (1).csv')
ir

![image](https://github.com/user-attachments/assets/cecef106-4291-4497-803a-33fdac38add7)

ir.describe()

![image](https://github.com/user-attachments/assets/4a65cb4d-a1b7-4f4f-94aa-c8d5098d6cc3)

import seaborn as sns

sns.boxplot(x='sepal_width',data=ir)

![image](https://github.com/user-attachments/assets/4c355ce0-db5f-4965-8d4d-74b14187aff1)

c1=ir.sepal_width.quantile(0.25)

c3=ir.sepal_width.quantile(0.75)

iq=c3-c1

print(c3)

![image](https://github.com/user-attachments/assets/cb80d3f8-3267-4748-8743-00a30060f0fe)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]

rid['sepal_width']

![image](https://github.com/user-attachments/assets/5a991ac8-fb5b-42c0-b720-08a5d360093c)

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]

delid

![image](https://github.com/user-attachments/assets/f49fdfbc-b4e5-4458-ae65-7a11b3beff12)

sns.boxplot(x='sepal_width',data=delid)

![image](https://github.com/user-attachments/assets/5f37fac6-bbc4-40ad-98fd-300f1ae27731)

import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset

![image](https://github.com/user-attachments/assets/9faf1aad-93bf-421d-9e98-65b50a62837c)

df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr

![image](https://github.com/user-attachments/assets/0956caf0-38e7-4958-8eff-8e96e08314ee)

low = q1 - 1.5*iqr
low

![image](https://github.com/user-attachments/assets/98e89809-574b-45ed-81de-ee1725227dee)

high = q3 + 1.5*iqr
high

![image](https://github.com/user-attachments/assets/c7e79f12-432d-4e52-bb23-20beed0fe4e7)

df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1

![image](https://github.com/user-attachments/assets/c4e3f839-3e41-4720-83ba-fc0c8e47c7e8)

z = np.abs(stats.zscore(df['height']))
z

![image](https://github.com/user-attachments/assets/fd4ae98b-2bbe-44b4-9ed8-2478c19bdffa)

df1 = df[z<3]
df1

![image](https://github.com/user-attachments/assets/75123137-9c54-44ec-ba93-00e2a676d3a6)





# Result:

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
