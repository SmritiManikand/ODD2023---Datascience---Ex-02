# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of bangalore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# AIM
To read the given csv file and perform set of operations after removing outliers.


# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file

# CODE 

```
import pandas as pd
import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af

sns.boxplot(data=af)

sns.scatterplot(data=af)

q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

aq=af[((af>=low)&(af<=high))]
aq.dropna()

af=af[((af>=low)&(af<=high))]
af.dropna()

sns.boxplot(data=af)

data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,148]
df=pd.DataFrame(data)
sns.scatterplot(data=af)

sns.boxplot(data=df)

z=np.abs(stats.zscore(df))
z

df=df[z[0]<3]
df

sns.scatterplot(data=df)

ed=df.quantile(0.5)
ed

q1=df.quantile(0.25)
q1

q3=df.quantile(0.75)
q3

iqr=q3-q1
iqr

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

dq=df[((df>=low)&(df<=high))]
dq

import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
df=pd.read_csv("/content/heights.csv")

df

sns.boxplot(data=df)

sns.scatterplot(data=df)

max=df['height'].quantile(0.90)
min=df['height'].quantile(0.15)
max

min

dq=df[(df['height']>=min)&(df['height']<=max)]
dq

import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,148]}
df=pd.DataFrame(data)
df

sns.boxplot(data=df)

z=np.abs(stats.zscore(df))
df=df[z['weight']<2.8]
df

val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,148]

out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out

op=d_o(val)
op

val

id=pd.read_csv("/content/iris.csv")
id

id.describe()

sns.boxplot(x='sepal_width',data=id)

c1=id.sepal_width.quantile(0.25)
c3=id.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)

rid=id[((id.sepal_width>(c1-1.5*iq))|(id.sepal_width<(c3+1.5*iq)))]
rid['sepal_width']

delid=id[~((id.sepal_width<(c1-1.5*iq))|(id.sepal_width<(c3+1.5*iq)))]
delid

sns.boxplot(x='sepal_width',data=delid)

```

# OUTPUT
