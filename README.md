
### Name: PAKANATI MONISH
### RegNo: 212224240109
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
```
import numpy as np
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data
```

# Output:

![WhatsApp Image 2025-09-17 at 15 27 09_d27bac56](https://github.com/user-attachments/assets/a4f56043-b7cf-4406-a224-52e86def41dc)




```
data.head(4)

```
# Output:

![WhatsApp Image 2025-09-17 at 15 28 09_671e8205](https://github.com/user-attachments/assets/2b40192d-e6a0-4af7-88b7-258b38d35d25)



```
data.tail(7)
```


# Output:
![WhatsApp Image 2025-09-17 at 15 28 47_5528b807](https://github.com/user-attachments/assets/6a95bdb6-fe69-40a5-8689-c14aba65dabd)




```
data.isnull()
```


# Output:
![WhatsApp Image 2025-09-17 at 15 29 57_4c215c97](https://github.com/user-attachments/assets/4855310a-73f0-4ff1-a90e-eb64103d4aa7)



```
data.notnull()
```



# Output:

![WhatsApp Image 2025-09-17 at 15 32 50_87b9b4ec](https://github.com/user-attachments/assets/fd481736-8aa0-4d79-a2b9-0c645689896e)




```
data.isnull().sum()

```


# Output:
![WhatsApp Image 2025-09-17 at 15 33 32_0d8ee07f](https://github.com/user-attachments/assets/9702cdc4-2235-462d-8823-5471d5880d48)




```
data.isnull().any()
```


# Output:
![WhatsApp Image 2025-09-17 at 15 34 17_a1ed4047](https://github.com/user-attachments/assets/a2d4cd94-d762-43d2-bcb7-1d2ffee0566b)



```
data.dropna(axis=1)

```


# Output:
![WhatsApp Image 2025-09-17 at 15 35 37_32a48a18](https://github.com/user-attachments/assets/ee5b45f1-e639-4730-ba24-17d3dd0cb26e)




```
data.dropna(axis=0)
```



# Output:
![WhatsApp Image 2025-09-17 at 15 36 20_bbb6feb9](https://github.com/user-attachments/assets/ec201545-d10b-4dd3-9821-8e5d75535b36)





```
data.fillna(0)
```



# Output:
![WhatsApp Image 2025-09-17 at 15 37 11_4cd15068](https://github.com/user-attachments/assets/bb73d599-ca9c-419f-9a83-aa78a0f51f87)




```
data.fillna(method="ffill")
```


# Output:
![WhatsApp Image 2025-09-17 at 15 37 49_20432b2c](https://github.com/user-attachments/assets/d88fe5e1-26a4-4908-82ab-f967c23cfa85)




```
data.bfill()
```



# Output:
![WhatsApp Image 2025-09-17 at 15 38 36_161310d8](https://github.com/user-attachments/assets/13c4ca04-1371-4c52-bed1-3dac949304b8)


```

data.fillna({'REGNO':0,	'NAME':'PRAVEEN'})
```



# Output:




```
ir=pd.read_csv("/content/iris.csv")
ir
```



# Output:
![WhatsApp Image 2025-09-17 at 15 40 26_3cd114ae](https://github.com/user-attachments/assets/f7cdefc6-f7f0-4960-8f87-5044dfd1a942)





```
ir.describe()

```



# Output:
![WhatsApp Image 2025-09-17 at 15 41 10_e0e8afdf](https://github.com/user-attachments/assets/3baec901-6e61-4982-ab6a-e5b86bb86d62)




```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)

```



# Output:
![WhatsApp Image 2025-09-17 at 15 41 49_6f86b49b](https://github.com/user-attachments/assets/edeb1529-a558-4e13-995e-63b1ae64d5ed)





```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```



# Output:
![WhatsApp Image 2025-09-17 at 15 42 29_99fc68be](https://github.com/user-attachments/assets/de47eb2a-d458-4f47-b33e-c1ea681169ab)




```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```




# Output:
![WhatsApp Image 2025-09-17 at 15 43 06_876da5e7](https://github.com/user-attachments/assets/fd5a13e5-da12-4095-9d63-ba0817f0afcc)




```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid

```



# Output:
![WhatsApp Image 2025-09-17 at 15 45 21_595cf120](https://github.com/user-attachments/assets/c13eae86-52fc-45ba-950c-d450b0f99573)




```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']

```


# Output:
![WhatsApp Image 2025-09-17 at 15 48 49_86c36fd7](https://github.com/user-attachments/assets/cc839f87-9c48-4dd7-bc79-8cc90613f1cc)




```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```



# Output:
![WhatsApp Image 2025-09-17 at 15 49 23_75a0a198](https://github.com/user-attachments/assets/1fd6a7ff-5d4d-4836-bce0-74a9217be9f8)




# Result:

Thus the programs are executed successfully.
