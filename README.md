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
            df = pd.read_csv("SAMPLEIDS (1).csv")
            df.describe()
![image](https://github.com/user-attachments/assets/9070c361-ba2f-4936-b956-6b9fe5a6135d)

            df.info()
![image](https://github.com/user-attachments/assets/8e74942e-d4e0-4fd0-b96e-a33e23ef5065)     
            
            df.shape
![image](https://github.com/user-attachments/assets/bd09d35b-5572-48a0-a3fb-f36aaf8266db)
            
            df.isnull()
![image](https://github.com/user-attachments/assets/a467b1d3-faca-4c36-87ff-a49109d0d830)
            
            df.isna()
![image](https://github.com/user-attachments/assets/457c395d-9ee5-43be-9740-2eb22798c9d8)

            df.isnull().sum()
![image](https://github.com/user-attachments/assets/f8305b97-86d0-4f79-8755-c86bd4c3f43a)

            df.dropna()
![image](https://github.com/user-attachments/assets/f9b00f2c-7924-41fe-bbf1-bf63eed3396d)

            dt = df[df["NAME"].str.startswith(("S")) & (df['AVG']>100)]
            dt
![image](https://github.com/user-attachments/assets/68506727-c407-4841-ae94-8e71c9f4f5b1)

            a = df.TOTAL.mean()
            df.TOTAL.fillna(a,inplace=True)
            df
![image](https://github.com/user-attachments/assets/5bd59082-2fdd-4724-bae6-5d738600ab90)
            
            a = df.drop_duplicates(inplace=False)
            a
![image](https://github.com/user-attachments/assets/45047cea-507b-49a4-b673-03b94beb3f17)

            import pandas as pd
            import seaborn as sns
            import numpy as np
            age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
            dt = pd.DataFrame(age)
            dt
![image](https://github.com/user-attachments/assets/f865fc1a-2890-4d96-a289-b6a59d99a092)

     sns.boxplot(data = dt)
![image](https://github.com/user-attachments/assets/0afdc92b-6704-4b1c-bd0d-c4a5531acf70)

            sns.scatterplot(data = dt)
![image](https://github.com/user-attachments/assets/8366d6a2-5130-495d-9786-c438c8ffd9e0)

            q1= dt.quantile(0.25)
            q3= dt.quantile(0.75)
            iqr = q3-q1
            iqr
![image](https://github.com/user-attachments/assets/b31da7e4-6754-425a-8561-b19eb0a3ac11)
          
            Q1=np.percentile(dt,25)
            Q3=np.percentile(dt,75)
            IQR=Q3-Q1
            IQR
![image](https://github.com/user-attachments/assets/58ad230b-5f91-45b4-b981-b3247ca510a9)

            lb = Q1-1.5*IQR
            lb
![image](https://github.com/user-attachments/assets/633c7141-eb26-441b-8b65-2edecc4830bd)

            ub = Q3 +1.5 *IQR
            ub
![image](https://github.com/user-attachments/assets/5b5834be-3b39-4b5b-950f-19b6488cbd0c)

            outliers=[x for x in age if xub]
            print("Q1:",Q1)
            print("Q3:",Q3)
            print("IQR:",IQR)
            print("Lower Bound:",lb)
            print("Upper Bound:",ub)
            print("Outliers:",outliers)
![image](https://github.com/user-attachments/assets/3c897401-f5a9-4c27-8ee6-fc116066f47c)

            dt = dt[((dt>=lb)&(dt<=ub))]
            dt
![image](https://github.com/user-attachments/assets/92ca220c-8306-4c13-a795-0037fc7938ac)

            dt.dropna()
![image](https://github.com/user-attachments/assets/944c6bde-0449-4158-ab89-79f6afdb088f)

            sns.boxplot(data=dt)
![image](https://github.com/user-attachments/assets/8eeacbe4-92b0-487e-ba2b-73f7ad5b72c2)

# Result
          <<include your Result here>>
