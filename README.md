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
            import pandas as pd

            df=pd.read_csv("/content/SAMPLEIDS (1).csv")

            df
![image](https://github.com/user-attachments/assets/8d6c773d-7414-48ad-9ff5-9bf49e9d38f8)
            
            df.describe()

![image](https://github.com/user-attachments/assets/c0a550ae-6567-4bfd-ba18-573aa13974c9)


            df.info()

![image](https://github.com/user-attachments/assets/4c04fc71-8fd1-405a-83e8-92441c389de1)

            df.shape[0]

![image](https://github.com/user-attachments/assets/be882a98-02f8-4a05-b55f-4f7d5fb2a0ec)

            df.shape

![image](https://github.com/user-attachments/assets/e66f0d71-da17-40a1-835d-987dded2ba94)

            df.head(10)

![image](https://github.com/user-attachments/assets/9fb52d80-534b-434c-86fb-a8412f2423b8)

            df.tail(10)

![image](https://github.com/user-attachments/assets/2d9ea652-7869-4154-99a5-37dcb5f74a43)

            df.isna().sum()

![image](https://github.com/user-attachments/assets/63c468b6-304c-4966-83de-b026728c65e8)

            df.dropna(how='any').shape

![image](https://github.com/user-attachments/assets/c152e38b-b40d-48c9-9691-0593184ad2ba)

            x=df.dropna(how='any')

            x

![image](https://github.com/user-attachments/assets/102589df-2553-4e93-8d89-1e509701a62e)

            mn=df.TOTAL.mean()

            mn

![image](https://github.com/user-attachments/assets/2a75a558-9ee3-4b56-b095-e70dfd0758c0)

            df.TOTAL.fillna(mn,inplace=True)

            df

![image](https://github.com/user-attachments/assets/5a49ad80-5942-44bb-9e70-0b251a24251f)

![image](https://github.com/user-attachments/assets/824eec8f-24b7-457b-a526-4011f6c75a05)


            df.isnull().sum()

![image](https://github.com/user-attachments/assets/d5c1d669-99ab-4aa7-9b0e-ed868b872edd)

            df.M1.fillna(method='ffill',inplace=True)

            df

![image](https://github.com/user-attachments/assets/15e8bfd7-6f61-40e9-be33-e082ecdc27fb)
![image](https://github.com/user-attachments/assets/b5ca48c2-c8af-4fef-a97f-781cca5256db)


            df.M2.fillna(method='ffill',inplace=True)

            df
![image](https://github.com/user-attachments/assets/623e2531-bcbf-4765-9ad4-ed15252bc1f2)
![image](https://github.com/user-attachments/assets/9813d756-0fed-4abb-aec0-99a355a29436)

            df.isna().sum() 

![image](https://github.com/user-attachments/assets/4f00ee77-9a61-447c-9662-ff4c231abd96)

            df.M3.fillna(method='ffill',inplace=True)

            df

![image](https://github.com/user-attachments/assets/d1f530eb-36d3-450c-8b67-edcdf4f2f2c3)
![image](https://github.com/user-attachments/assets/9defa175-62b7-41af-912f-c1a17ebfe45f)


            df.duplicated()

![image](https://github.com/user-attachments/assets/d80172bd-ba6f-4b52-9a43-9a1b4d9066ef)


            df.drop_duplicates(inplace=True)

            df

![image](https://github.com/user-attachments/assets/fe9d320b-90ec-4021-b7a9-c451199a396a)

            df['DOB'] 

![image](https://github.com/user-attachments/assets/095588a0-16d7-413e-b9a4-d4183ad0a62d)

            import seaborn as sns

            sns.heatmap(df.isnull(),yticklabels=False,annot=True)

![image](https://github.com/user-attachments/assets/042aec94-0cbf-47c4-be71-fea102d44278)

            df.dropna(inplace=True)

            sns.heatmap(df.isnull(),yticklabels=False,annot=True)

![image](https://github.com/user-attachments/assets/21ab8880-7e11-4aea-b415-78436e765f94)


            age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]

            df=pd.DataFrame(age)

            df

![image](https://github.com/user-attachments/assets/f9250b3d-838e-4f85-8597-69e9b73f7bff)

            sns.boxplot(data=df) 

![image](https://github.com/user-attachments/assets/0bec7d18-dd73-4a21-a244-74b7946f450c)

            sns.scatterplot(data=df) 

![image](https://github.com/user-attachments/assets/21cc5362-b35b-4e06-ad5a-10f857c84a71)

            q1=df.quantile(0.25)

            q2=df.quantile(0.5)

            q3=df.quantile(0.75)

            iqr=q3-q1

            iqr

![image](https://github.com/user-attachments/assets/428f7362-9e82-4715-89d8-c5646daecab6)

            import numpy as np

            Q1=np.percentile(df,25)

            Q3=np.percentile(df,75)

            IQR=Q3-Q1

            IQR

![image](https://github.com/user-attachments/assets/b6663c66-6a17-42e6-b9fb-f7a4423adb42)


            lower_bound=Q1-1.5*IQR

            upper_bound=Q3+1.5*IQR

            lower_bound

            upper_bound

![image](https://github.com/user-attachments/assets/61c2ded5-035b-44e0-b962-4c6dfd1167a9)

            outliers=[x for x in age if x<lower_bound or x>upper_bound]

            print("Q1:",Q1)

            print("Q3:",Q3)

            print("IQR:",IQR)

            print("Lower Bound:",lower_bound)

            print("Upper Bound:",upper_bound)

            print("Outliers:",outliers)

![image](https://github.com/user-attachments/assets/5115c014-7084-4ca5-bf88-37fb952f9c1c)

            df=df[((df>=lower_bound)&(df<=upper_bound))]

            df

![image](https://github.com/user-attachments/assets/328b70c4-4e94-45fe-a4ee-63fbaed98d09)

            df=df.dropna()

            df

![image](https://github.com/user-attachments/assets/4ed34b7d-50de-4291-a08a-c6482b24d2c8)

            sns.boxplot(data=df) 

![image](https://github.com/user-attachments/assets/fee1089d-c0ee-4c55-b13c-a420460be0f6)

            sns.scatterplot(data=df)

![image](https://github.com/user-attachments/assets/3eb80c1c-307a-45e2-afe8-46d11606be3f)

            data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]

            mean=np.mean(data)

            std=np.std(data)

            print('mean of the dataset is',mean)

            print('std.deviation is',std)

![image](https://github.com/user-attachments/assets/5105e081-6a27-479d-a1c9-045aa1178083)

            threshold=3

            outlier=[]

            for i in data:

              z=(i-mean)/std
  
              if z>threshold:
  
                outlier.append(i)

            print('outlier in dataset is',outlier)

![image](https://github.com/user-attachments/assets/62009a14-6fad-4c4f-8dcb-0a22be54d290)

            import pandas as pd

            import numpy as np

            import seaborn as sns

            from scipy import stats

            data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}

            df=pd.DataFrame(data)

            df

![image](https://github.com/user-attachments/assets/2f71192b-9204-4bf7-a798-890c1e1b6209)
![image](https://github.com/user-attachments/assets/e49fc7fd-31c7-41f6-a37d-4cd2ddb8c418)

            z=np.abs(stats.zscore(df))

            print(df[z['weight']>3])

![image](https://github.com/user-attachments/assets/0b76270d-123e-40a4-bda1-c90dffa2d241)

# Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score
