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
***

          import pandas as pd
          import numpy as np
          import seaborn as sns
          import os 
          df=pd.read_csv("SAMPLEIDS.csv")
          df
***          

![image](https://github.com/user-attachments/assets/576e57cf-9e95-46cc-be07-63e29b939266)

~~~
 df.isnull().sum()
~~~
![image](https://github.com/user-attachments/assets/a950a4db-bea4-4234-8f7d-d9a6e9686e6d)
~~~
df.isnull().any()
~~~
![image](https://github.com/user-attachments/assets/8760f567-7e1d-434f-9eb7-935b9a5fc8d9)
~~~
df.dropna()
~~~
![image](https://github.com/user-attachments/assets/7234e8a4-a937-401b-a945-99fa9adddf7b)
~~~
  df.fillna(0)
~~~
![image](https://github.com/user-attachments/assets/f5fd038d-d5f1-4ddd-a137-71038292d318)
~~~
df.fillna(method = 'ffill')
~~~
![image](https://github.com/user-attachments/assets/b01b8f83-4e2c-48cb-889e-63ba70e060b0)
~~~
 df.fillna(method = 'bfill')
~~~
![image](https://github.com/user-attachments/assets/981efe8b-daee-4ce6-88cd-46ddbb44c574)
~~~
 df_dropped = df.dropna()
           df_dropped
~~~
![image](https://github.com/user-attachments/assets/a25f5286-0134-4943-962e-83c7d3435a61)
~~~
 df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
~~~
![image](https://github.com/user-attachments/assets/cbb68bfd-9005-46d7-8529-aec7d5c447b5)
~~~
 import pandas as pd
         
         ir=pd.read_csv('iris.csv')
         ir
~~~
![image](https://github.com/user-attachments/assets/d11500b0-33c0-4dbb-a834-7856ceb733d8)
~~~
  ir.describe()
~~~
![image](https://github.com/user-attachments/assets/9e938759-235c-40f6-8d92-f56fa07fe3a1)
~~~
import seaborn as sns
         
         sns.boxplot(x='sepal_width',data=ir)
~~~
![image](https://github.com/user-attachments/assets/3628c50c-43cc-4260-a01b-edcb70da1ba0)
~~~
c1=ir.sepal_width.quantile(0.25)
           c3=ir.sepal_width.quantile(0.75)
           iq=c3-c1
           print(c3)
~~~
3.3
~~~
 rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            rid['sepal_width']
~~~
![image](https://github.com/user-attachments/assets/31588303-c802-47f6-8056-ccebb651d63f)
~~~
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            delid
~~~
![image](https://github.com/user-attachments/assets/0658eb79-bb76-4f5a-858c-b8864c1a543d)
~~~
   sns.boxplot(x='sepal_width',data=delid)
~~~
![image](https://github.com/user-attachments/assets/d438fd66-472c-4dce-a1d2-e6f432fcb6fb)
~~~
   import matplotlib.pyplot as plt
            import pandas as pd
            import numpy as np
            import scipy.stats as stats

            dataset=pd.read_csv("heights.csv")
            dataset
~~~
![image](https://github.com/user-attachments/assets/2a198c89-3ca1-43e2-b06e-c6ca572a2b0d)
~~~
 df = pd.read_csv("heights.csv")
            q1 = df['height'].quantile(0.25)
            q2 = df['height'].quantile(0.5)
            q3 = df['height'].quantile(0.75)
            
            iqr = q3-q1
            iqr
~~~
0.9249999999999998
~~~
  low = q1 - 1.5*iqr
        low
~~~
3.8625000000000003
~~~
high = q3 + 1.5*iqr
        high
~~~
7.5625
~~~
 df1 = df[((df['height'] >=low)& (df['height'] <=high))]
        df1

~~~
![image](https://github.com/user-attachments/assets/ea3f40f7-7087-45a9-ab51-476b90830c9e)
~~~
z = np.abs(stats.zscore(df['height']))
        z
~~~
![image](https://github.com/user-attachments/assets/f435bb6c-eab0-4d94-8dd3-416b46fc37b0)
~~~
df1 = df[z<3]
        df1
~~~
![image](https://github.com/user-attachments/assets/b131530e-9177-4615-8781-92a2adf9f79e)

# Result
        Thus the given data successfully performed data cleaning and saved the cleaned data to a file.

