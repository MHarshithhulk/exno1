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

df.head()
<img width="1474" height="315" alt="Screenshot 2025-08-30 112251" src="https://github.com/user-attachments/assets/e04d1ead-83d8-4d60-b2af-f743df78568c" />

df.tail()

<img width="1439" height="318" alt="Screenshot 2025-08-30 183015" src="https://github.com/user-attachments/assets/27cc3cc1-42b5-4deb-8ce6-bc201de50e31" />


df.isnull()

<img width="872" height="887" alt="image" src="https://github.com/user-attachments/assets/1a58cb96-e6b9-4c4b-a743-ab2d0dbc751c" />

df.isnull().sum()

<img width="343" height="637" alt="image" src="https://github.com/user-attachments/assets/852eda82-9d39-4693-b6e9-756bd7b621c1" />


df.isnull().any()

<img width="391" height="622" alt="image" src="https://github.com/user-attachments/assets/b42c8fd9-63d1-4bda-880a-ef39e0f3d1e4" />


df.dropna(axis=0)

<img width="1175" height="628" alt="image" src="https://github.com/user-attachments/assets/530a6698-2e84-4069-900d-8577a38cfaa9" />


df.dropna(axis=1)

<img width="510" height="888" alt="image" src="https://github.com/user-attachments/assets/fbd0a813-684d-402d-b343-5fa277798fc3" />


df.fillna("empty")

<img width="1170" height="918" alt="image" src="https://github.com/user-attachments/assets/fe4af4b0-9778-4e4e-995f-161d2547f9e0" />


df.fillna(method='ffill')

<img width="1457" height="877" alt="image" src="https://github.com/user-attachments/assets/f4a3f3eb-d28e-49c7-bb2d-322ddcdf4fc7" />

df.fillna(method='bfill')

<img width="1427" height="871" alt="image" src="https://github.com/user-attachments/assets/cacb6d2d-6d4a-41e4-b839-c585d35c5476" />


df.fillna({'NAME':'Harshith M','GENDER':'MALE','ADDRESS':'CHITHUR','M1':90,'M2':90,'M3':89,'M4':87})

<img width="1105" height="893" alt="image" src="https://github.com/user-attachments/assets/1f3a4d5e-f680-4afa-a0d6-7fc94d5f813c" />

ir=pd.read_csv("iris.csv")
ir

<img width="823" height="518" alt="image" src="https://github.com/user-attachments/assets/23d6780f-0bf2-4ec9-8509-884023e123c8" />


ir.describe()

<img width="751" height="381" alt="image" src="https://github.com/user-attachments/assets/d7a7a916-9d0e-4fec-9e14-30518370c2a5" />

import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)

<img width="787" height="593" alt="image" src="https://github.com/user-attachments/assets/f6720148-2e72-4817-9071-8ae5d9b3e73b" />


q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)

<img width="630" height="50" alt="image" src="https://github.com/user-attachments/assets/541d38a8-ff79-4fef-b8df-7d3c66451c33" />

rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']

<img width="1357" height="270" alt="image" src="https://github.com/user-attachments/assets/14355313-96b4-44af-896b-eac90127a689" />


delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid

<img width="1128" height="536" alt="image" src="https://github.com/user-attachments/assets/44b3aedf-ca57-4b2f-a67a-f3839b4e611c" />

sns.boxplot(x='sepal_width',data=delid)

<img width="791" height="598" alt="image" src="https://github.com/user-attachments/assets/22747e2b-0120-44c4-98bf-baf9be2d47ca" />


import numpy as np
from scipy import stats
z = np.abs(stats.zscore(ir['sepal_width']))
z

<img width="1266" height="682" alt="image" src="https://github.com/user-attachments/assets/0be7a3c2-912b-4e56-8481-798a7ba31d36" />


ir1=ir[z<3]
ir1


<img width="1223" height="528" alt="image" src="https://github.com/user-attachments/assets/1223c27b-ce7f-4175-9900-a56977e23947" />



# Result:

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
