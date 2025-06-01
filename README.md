# Exno:1
# Data Cleaning Process
## NAME : L TOM FRANCIES XAVIOUR 
## Reg.No: 212223110060
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
### Reading the data:
```py
import pandas as pd
df=pd.read_csv('Housing.csv')
df.head()
```
### Output:
![image](https://github.com/user-attachments/assets/4bfb6d9e-ae59-4622-bb43-ed6d5422c327)
### Data Info:
```py
df.info()
```
### Output:
![image](https://github.com/user-attachments/assets/7e65b4cd-8941-43f3-8f52-d42c030d86db)
### Removing null values:
```py
df_clean = df.dropna()
df_clean
```
### Output:
![image](https://github.com/user-attachments/assets/e59970b7-d15c-460b-80bd-842113a2d6d8)
### Saving the clean data:
```py
df_clean.to_csv("Housing_clean.csv", index=False)
```
### Removing Outliers using IQR:
```PY
for col in colss:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1

    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    outlier_rows = df[(df[col] < lower_bound) | (df[col] > upper_bound)]
    outliers[col] = outlier_rows.shape[0]
    print(f"{col}: {outlier_rows.shape[0]} outliers found")
```
### Output:
![image](https://github.com/user-attachments/assets/f4efcff7-d600-4a98-ac57-7582baf84839)
### Using Z Score:
```py
import numpy as np
from scipy.stats import zscore
z_scores = np.abs(df[colss].apply(zscore))
outliers_z = (z_scores > 3)
for col in colss:
    print(f"{col}: {outliers_z[col].sum()} outliers found")
```
### Output:
![image](https://github.com/user-attachments/assets/cc2be080-bfc0-4060-9e6d-7cb8c6d09a41)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
