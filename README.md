# Exno:1
Data Cleaning Process

```
NAME : PARANTHAMAN S
REG_NO : 212224040232
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

```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="1147" height="840" alt="Screenshot 2025-08-26 195056" src="https://github.com/user-attachments/assets/16c2c1b4-d989-45e7-a88f-b7b7a68c9c27" />

```
df.head()
```
<img width="1135" height="308" alt="Screenshot 2025-08-26 195622" src="https://github.com/user-attachments/assets/3d97fc19-2c55-4ac9-8411-ebe39ccdb50b" />

```
df.isnull()
```
<img width="752" height="739" alt="image" src="https://github.com/user-attachments/assets/6eecc746-d050-4798-9b17-057c97297a42" />

```
df.dropna(axis=0)
```
<img width="1099" height="497" alt="image" src="https://github.com/user-attachments/assets/8c0bc64d-c37c-4d6c-ad97-20a1e965d07f" />

```
df.dropna(axis=1)
```
<img width="614" height="728" alt="image" src="https://github.com/user-attachments/assets/4c20a59d-b9e6-4537-94a3-940020bd5857" />

```
dff=df.fillna(0)
dff
```
<img width="963" height="761" alt="image" src="https://github.com/user-attachments/assets/6bce8db4-2200-473f-a185-8a6fec37b768" />

```
df.fillna(method="ffill")
```
<img width="1388" height="763" alt="image" src="https://github.com/user-attachments/assets/0edd91ab-4e93-42d0-a7ac-3e96e6807da3" />

```
df.fillna(method="bfill")
```
<img width="1389" height="775" alt="image" src="https://github.com/user-attachments/assets/7bc8fa1f-75b4-4a4c-b9f7-c613d6d84815" />

```
import pandas as pd
import seaborn as sns
id=pd.read_csv("iris.csv")
id
```
<img width="802" height="519" alt="image" src="https://github.com/user-attachments/assets/aa29f677-98e3-431d-9945-b44184606064" />

```
sns.boxplot(x='sepal_width', data=id)
```
<img width="751" height="499" alt="image" src="https://github.com/user-attachments/assets/8dcbffdd-1d24-4b83-a6e0-990f17edc7ca" />

```
q1=id.sepal_width.quantile(0.25)
q3=id.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="616" height="115" alt="image" src="https://github.com/user-attachments/assets/9fde0f97-8001-4268-a40d-9b75fb230247" />

```
rid=id[((id.sepal_width<(q1-1.5*iqr))|(id.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="660" height="297" alt="image" src="https://github.com/user-attachments/assets/3fd43e45-d7ea-40f4-b0d3-8a0a0218ea90" />

```
delid=id[~((id.sepal_width<(q1-1.5*iqr))|(id.sepal_width>(q3+1.5*iqr)))]
delid['sepal_width']
```
<img width="669" height="550" alt="image" src="https://github.com/user-attachments/assets/669baf44-6837-48e6-9478-77fed0d5a233" />

```
sns.boxplot(x='sepal_width', data=id[delid[0]])
```
<img width="747" height="506" alt="image" src="https://github.com/user-attachments/assets/696e2914-50cf-4f60-ac57-eaf27e110f64" />

```
ZSCORE METHOD
```

```
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
<img width="982" height="839" alt="image" src="https://github.com/user-attachments/assets/728296f0-81d5-455a-8288-15b46cee4a74" />

```
z=np.abs(stats.zscore(df['weight']))
print(df[z>3])
```
<img width="381" height="120" alt="image" src="https://github.com/user-attachments/assets/a9f1880f-4892-4be9-be9c-eaeddb26ab95" />

```
val = [12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]
```
```
out = []
def d_o(val):
    ts = 3
    m = np.mean(val)
    sd = np.std(val)
    for i in val:
        z = (i - m) / sd
        if np.abs(z) > ts:
            out.append(i)
    return out
```
```
op = d_o(val)
op
```
<img width="1201" height="460" alt="image" src="https://github.com/user-attachments/assets/e6d1be16-fc57-4491-b4c3-4b9ddada44ad" />


# Result
```
      Thus, we have carried out data cleansing and removed the outliers by detection using IQR and Z-Score methods. The cleaned data has been successfully prepared for further analysis.
```

