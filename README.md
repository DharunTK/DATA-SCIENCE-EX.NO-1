#EX.NO:1
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
NAME:VISHNU PRIYA A K
REG NO:212225230309
```
import pandas as pd
data=pd.read_csv("sampleids.csv")
data
```
<img width="819" height="627" alt="image" src="https://github.com/user-attachments/assets/c7901f1f-a5c7-4895-8caa-096f16b8dcd2" />

```
data.info()
```
<img width="633" height="649" alt="image" src="https://github.com/user-attachments/assets/ed5b2017-23ef-4ade-a33e-bb9bd6aa8b8a" />

```
print(data.head())
print(data.tail())
```

<img width="789" height="583" alt="image" src="https://github.com/user-attachments/assets/ecc7dfef-fcbe-4d33-82fc-39c18568edb7" />

```
data.isnull()
```

<img width="804" height="743" alt="image" src="https://github.com/user-attachments/assets/d99295ff-a582-45e6-bb0b-9da33ecad466" />

```
data.isnull().sum()
```

<img width="284" height="472" alt="image" src="https://github.com/user-attachments/assets/739a83ee-f92f-4177-a8ec-cdc30a0c0481" />

```
data.dropna()
```

<img width="804" height="432" alt="image" src="https://github.com/user-attachments/assets/560bdc47-7cb3-4ea3-b914-a007e39a604a" />

```
data.fillna(method='ffill')
```

<img width="801" height="629" alt="image" src="https://github.com/user-attachments/assets/1eb4248a-35d0-43cf-b5ee-454379d23015" />

```
data.fillna(method='bfill')
```

<img width="806" height="633" alt="image" src="https://github.com/user-attachments/assets/a7036c7f-b45f-4e11-9430-a6ce2f0684cb" />

```
data.fillna({'NAME':'RIYA','GENDER':'FEMALE','ADDRESS':'CHENNAI','M1':90,'M2':90,'M3':89,'M4':87})
```

<img width="869" height="683" alt="image" src="https://github.com/user-attachments/assets/374c3d22-21c8-432b-89c9-3b9c3a01d6c1" />

```
import numpy as np
from scipy import stats
ir=pd.read_csv("iris.csv")
ir
```

<img width="521" height="418" alt="image" src="https://github.com/user-attachments/assets/32eadbd7-e4d4-4477-a9d1-c6bece28c0db" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="673" height="572" alt="image" src="https://github.com/user-attachments/assets/1366be68-7d10-4811-a690-e2016e35a858" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
print()
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
print(rid['sepal_width'])
```

<img width="332" height="155" alt="image" src="https://github.com/user-attachments/assets/bd4c669b-a915-4937-aca8-1e77db46b40e" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```

<img width="531" height="420" alt="image" src="https://github.com/user-attachments/assets/08b7b4e4-5603-43d2-aa73-dd61d20036c6" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="674" height="584" alt="image" src="https://github.com/user-attachments/assets/08827bd2-d8cf-499e-83f3-0b52809a1ca7" />

```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```

<img width="457" height="260" alt="image" src="https://github.com/user-attachments/assets/22e99863-c2bd-42ef-8692-a31deb76b207" />

```
ir1=ir[z<3]
ir1
```

<img width="533" height="424" alt="image" src="https://github.com/user-attachments/assets/56e0a4de-1b76-45ae-bd9a-d5dc1e2eeb05" />



















# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
