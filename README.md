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

![s1](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/5c16bdf0-7b0c-4306-a3e4-69d08cfa4850)
![s2](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/a414b119-674e-4524-b7a4-78456fe742f1)
![s3](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/53e3932a-0691-4ec5-ad2e-60f5e5fc6414)
![s4](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/ad15a542-ce60-44f7-a43a-3c82e7c50d29)
![s5](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/579a2ce5-9336-4a60-8a6b-ba6fc5771091)
![s6](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/87aae5b3-3ca8-4587-88f2-22dd4f6a57af)
![s7](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/43a13a0d-3ff0-4d75-9ece-e74c6815f012)
![s8](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/31be7b61-03fd-4514-904e-29b112d60535)
![s9](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/e7c0625a-bb9d-4bbb-8d52-f6f9bcbe615c)
![s10](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/e7076619-02ba-4598-b13c-e91136a43d06)
![s11](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/c02e76bd-cdbd-4d47-9f0e-1fe6874e1dd5)
![s12](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/1e2fde88-151d-4465-a8b5-d0d589364af1)
![s13](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/3be6591c-11ef-4ac4-80b7-7178dbe9ebed)
![s14](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/0507b4ae-6fd9-40d5-9a2c-96bbc2e0b731)
![s15](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/2be11898-af55-4f6e-947d-fb6d9fed9109)
![s16](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/2c5fb280-0e1e-4b4d-bd81-c156be1eeac7)
![s17](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/29b2b1ea-705a-4f45-985e-29cfb76852a7)
![s18](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/131f8c43-d142-44cd-b0ee-caf6ca577c0e)
![s19](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/6e0a033a-b94e-442b-b274-ea59db1ddcab)
![s20](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/014d637c-c6a0-437d-80c4-a0bd014f9cd0)
![s21](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/e5016f64-d167-457e-a5c3-557ec9ff805f)
![s22](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/f11bafd1-8e02-474d-80ad-052a9a3aa2ae)
![s23](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/c8c5b813-261c-48cb-9631-95f3974a4612)
![s24](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/4e50be19-ef5b-45c0-bd63-9f2124bce46e)
![s25](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/7948d391-39cd-4492-8b55-56ddb90e75e7)
![s26](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/b324ba90-04b4-4909-ac12-f4931184c9c4)
![s27](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/b333eb1c-7d77-460c-8b96-5090a900ca92)
![s28](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/830002c6-843e-45d1-9a32-4905bc36a709)
![s29](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/c0208dc9-368d-4670-9a36-766702667dc9)
![s30](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/88e69895-6595-4baf-8bfe-e791beb263f7)
![s31](https://github.com/SmritiManikand/ODD2023---Datascience---Ex-02/assets/113674204/0d7cb2b6-cff2-4afd-bbe7-ffcad5ed75c3)


# RESULT

