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
     
  #Code:
  ```
 import pandas as pd
df=pd.read_csv('/content/height_weight (1).csv')
df
df=df.drop("gender",axis=1)
print('After removing Non numeric columns:')
df
df.boxplot()
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1
df1.boxplot()
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new
df_new.boxplot()
df_new
df.to_csv('heights.csv', index=False)

```

# OUTPUT:

###
Read the CSV file:





