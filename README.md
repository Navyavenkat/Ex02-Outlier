# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
   
   
   # Aim:
    
    To detect and remove the outlier in the given dataset and save the final.
    
   # Algorithm:
   
   Step 1
     Import the required packages(pandas,numpy,scipy)

  Step 2
    Read the given csv file

  Step 3
    Convert the file into a dataframe and get information of the data.

  Step 4
    Remove the non numerical data columns using drop() method.

  Step 5
    Detect the outliers in the data set using z scores method.

  Step 6
    Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

  Step 7
     Check if the outliersare removed from data set using graphical methods.

  Step 8
     Save the final data set into the file.
     
  # Code:
  
  ### (1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe
  ```
  import pandas as pd
import numpy as np
import seaborn as sns

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/bhp.csv")
df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_Aper_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
```


### (3) Examine price_per_sqft column and use zscore of 3 to remove outliers.

```
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)

```
### (4)(i) For the data set height_weight.csv detect weight outliers using IQR method
```
df3 = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/height_weight.csv")
df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))]
df4

df4.shape

sns.boxplot(x="weight",data=df4)
```
###(4)(ii) For the data set height_weight.csv detect height outliers using IQR method
```
sns.boxplot(x="height",data=df3)

q1 = df3['height'].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))]
df5

df5.shape

sns.boxplot(x="height",data=df5)
```

# OUTPUT:


![image](https://user-images.githubusercontent.com/94165327/191453831-f79c22de-80da-4e9f-99d1-a579d99bf125.png)

![image](https://user-images.githubusercontent.com/94165327/191453926-acf551eb-b132-4ac5-b064-be7490ea577f.png)

![image](https://user-images.githubusercontent.com/94165327/191454023-543d78de-bc8c-461a-a8af-758cd84d74c2.png)

![image](https://user-images.githubusercontent.com/94165327/191454096-290eab73-3fee-41bb-8078-c1576df4954d.png)

![image](https://user-images.githubusercontent.com/94165327/191454247-13ef8aea-1a56-45fd-b152-24d730ac3383.png)

![image](https://user-images.githubusercontent.com/94165327/191454321-1cd028bb-4f03-4dc0-bdf7-855ec2993e3b.png)

![image](https://user-images.githubusercontent.com/94165327/191454379-bbb14b32-5d2b-4c7e-a1ad-c84662996458.png)

![image](https://user-images.githubusercontent.com/94165327/191454518-25db25e9-a966-4a66-8d7c-21ccf291c741.png)

![image](https://user-images.githubusercontent.com/94165327/191454573-9ffae1d0-f3ec-4303-a100-329854db7839.png)

![image](https://user-images.githubusercontent.com/94165327/191454633-311ac4b9-f5c9-42b0-997f-f4ebbcd41ca4.png)

![image](https://user-images.githubusercontent.com/94165327/191454699-13221bb1-cf45-46ef-acda-98feb099c311.png)

![image](https://user-images.githubusercontent.com/94165327/191454847-00841e17-9a54-4837-a78b-cbd500ba6ca2.png)

![image](https://user-images.githubusercontent.com/94165327/191454931-c38fb5c6-c8ad-455f-b1ee-11c3a0748b1b.png)

![image](https://user-images.githubusercontent.com/94165327/191454991-06effb74-ac4d-4c55-8e8f-70dd628eed81.png)

![image](https://user-images.githubusercontent.com/94165327/191455051-94a62e28-f766-41b1-95fa-5a470237c309.png)




###
#
Result:

To detect and remove the outlier in the given dataset and save the finalised


