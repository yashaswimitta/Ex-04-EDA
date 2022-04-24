### Ex-04-EDA
### AIM
To perform EDA on the given data set.
### Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
### ALGORITHM
# STEP 1
Import the required packages(pandas,numpy,seaborn).
# STEP 2
Read and Load the Dataset.
# STEP 3
Remove the null values from the data and remove the outliers.
# STEP 4
Remove the non numerical data columns using drop() method.
# STEP 5:
returns object containing counts of unique values using (value_counts()).
# STEP 6:
Plot the counts in the form of Histogram or Bar Graph.
# STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).
# STEP 8:
Save the final data set into the file.
### CODE
~~~
Program 
Developed by:Yashaswi.Mitta
Register no:212221230062

import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("supermarket.csv")
df

# cleaning dataset
#checking for null values
df.isnull().sum()

#data is cleaned, proceed to remove outliers
#checking for outliers
df.boxplot()

#removing outliers
cols = ['Unit price','Quantity','Tax 5%','Total','cogs','gross margin percentage','gross income','Rating']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df
df.boxplot()

#outliers removed
# performing data analysis
# performing data analysis
#statistical analysis for single data group
df['Branch'].value_counts()
df['City'].value_counts()
df['Customer type'].value_counts()
df['Gender'].value_counts()
df['Product line'].value_counts()
df['Quantity'].value_counts()
df['Payment'].value_counts()

#statistical analysis for two data groups
pd.crosstab(df["Customer type"],df["Branch"])
pd.crosstab(df["Customer type"],df["City"])
pd.crosstab(df["Customer type"],df["Gender"])
pd.crosstab(df["Customer type"],df["Payment"])
pd.crosstab(df["Product line"],df["Quantity"])

#statistical analysis for multiple data groups
#analysing pairwise correlation of columns in dataset
df.corr()

#graphical analysis of categorical data--univariate
sns.countplot(x="Branch",data=df)
sns.countplot(x="City",data=df)
sns.countplot(x="Customer type",data=df)
sns.countplot(x="Payment",data=df)
sns.countplot(x="Gender",data=df)
sns.countplot(y="Product line",data=df)
sns.countplot(x="Quantity",data=df)

#graphical analysis of non-categorical data or data with multiple categories--univariate
sns.displot(df["Unit price"])
sns.displot(df["Tax 5%"])
sns.displot(df["cogs"])
sns.displot(df["gross income"])

#graphical analysis of categorical data--bivariate
sns.countplot(x="City",hue="Customer type",data=df)
sns.countplot(x="Branch",hue="Customer type",data=df)
sns.countplot(x="Gender",hue="Customer type",data=df)
sns.countplot(x="Payment",hue="Customer type",data=df)
sns.countplot(y="Product line",hue="Quantity",data=df)

#graphical analysis of non-categorical data or data with multiple categories--bivariate
sns.displot(df[df["City"]=='Yangon']["cogs"])
sns.displot(df[df["City"]=='Mandalay']["cogs"])
sns.displot(df[df["City"]=='Naypyitaw']["cogs"])

sns.displot(df[df["Product line"]=='Health and beauty']["Gender"])
sns.displot(df[df["Product line"]=='Electronic accessories']["Gender"])
sns.displot(df[df["Product line"]=='Home and lifestyle']["Gender"])
sns.displot(df[df["Product line"]=='Sports and travel']["Gender"])
sns.displot(df[df["Product line"]=='Food and beverages']["Gender"])
sns.displot(df[df["Product line"]=='Fashion accessories']["Gender"])

sns.displot(df[df["Gender"]=='Male']["gross income"])
sns.displot(df[df["Gender"]=='Female']["gross income"])

#Graphical representation of data--multivariate 
df.drop('gross margin percentage',axis=1,inplace=True)
sns.heatmap(df.corr(),annot=True)
~~~
### OUPUT
# Original Data
![image](https://user-images.githubusercontent.com/94619247/164976428-69234b52-76b3-47f4-a574-fa58f503444c.png)
# Data Cleaning Process
![image](https://user-images.githubusercontent.com/94619247/164976484-6a45428d-5788-4539-bd89-6e8d31379cad.png)
# Removing Outliers Process
![image](https://user-images.githubusercontent.com/94619247/164976508-411919ab-c618-45c8-aacc-dfdc1c80a40b.png)
![image](https://user-images.githubusercontent.com/94619247/164976522-92a0a08d-d73e-48b7-b557-fb80ddacffdf.png)
![image](https://user-images.githubusercontent.com/94619247/164976535-9c7fea35-0bbb-44aa-864e-ef4a67a8ff34.png)
# performing data analysis
# statistical analysis for single data group
![image](https://user-images.githubusercontent.com/94619247/164976564-e7c9183d-ef28-48b8-a722-a90ab6ea5fb4.png)
![image](https://user-images.githubusercontent.com/94619247/164976578-37f9ea7f-07ad-445b-94fc-d281f55e7a02.png)
![image](https://user-images.githubusercontent.com/94619247/164976588-97c26d88-e21e-4cb8-b2ba-3fd496a88838.png)
![image](https://user-images.githubusercontent.com/94619247/164976605-d5cc5538-7cb5-40d4-b640-643acf8a50a8.png)
![image](https://user-images.githubusercontent.com/94619247/164976611-ffe92550-b671-4775-8994-c1bab43ba836.png)
![image](https://user-images.githubusercontent.com/94619247/164976623-53b7333a-6ae0-427a-a297-fe3548ed8006.png)
![image](https://user-images.githubusercontent.com/94619247/164976638-1f0b7e24-fe7e-4ec3-b854-fc62a1cc8c69.png)
# statistical analysis for two data groups
![image](https://user-images.githubusercontent.com/94619247/164976656-0a52b5d8-5dc6-4705-9a2f-61a520f9c5bb.png)
![image](https://user-images.githubusercontent.com/94619247/164976662-ce70e877-da72-4bfc-8bb4-0b0b877a2b11.png)
![image](https://user-images.githubusercontent.com/94619247/164976668-7e6c0044-10c5-4b69-b31f-26c6cff3e91e.png)
![image](https://user-images.githubusercontent.com/94619247/164976674-4ecbc23f-d513-4f51-abb5-93ddb3e6f17e.png)
![image](https://user-images.githubusercontent.com/94619247/164976676-9a5e3d11-bda6-4089-9653-5c561001c402.png)
# pairwise correlation of columns in dataset
 
# graphical analysis of categorical data--univariate
![image](https://user-images.githubusercontent.com/94619247/164976696-2f35cf40-6751-4675-a93e-ec844f289aa5.png)
![image](https://user-images.githubusercontent.com/94619247/164976703-4209bc80-b122-4836-95a8-f107d87a55ff.png)
![image](https://user-images.githubusercontent.com/94619247/164976710-5b6fbcd5-a24d-4c56-a470-195e2ca7ac2a.png)
![image](https://user-images.githubusercontent.com/94619247/164976716-45f74979-6c8a-49a2-a57f-8e909e73bd97.png)
![image](https://user-images.githubusercontent.com/94619247/164976718-836493be-261d-44fe-8f23-e1db15731bfc.png)
![image](https://user-images.githubusercontent.com/94619247/164976727-4355b0bb-84fd-4580-9420-93d86dc440b5.png)
![image](https://user-images.githubusercontent.com/94619247/164976738-a99838e2-e6fd-48ef-9b49-b96bc29e9f29.png)
# graphical analysis of non-categorical data or data with multiple categories--univariate
       
# graphical analysis of categorical data--bivariate
![image](https://user-images.githubusercontent.com/94619247/164976769-35eb9bb9-71f7-4c0a-89ff-a6f27e45d48b.png)
![image](https://user-images.githubusercontent.com/94619247/164976790-942955ab-978e-42e4-904e-11d9ed817491.png)
![image](https://user-images.githubusercontent.com/94619247/164976795-f731d467-85fb-468d-b4d4-69d355627b3f.png)
![image](https://user-images.githubusercontent.com/94619247/164976804-42a4c7f9-9946-4a98-a91e-ba6a38027f2f.png)
![image](https://user-images.githubusercontent.com/94619247/164976807-68b7d4c3-46ef-4985-9f07-3812913c4441.png)
# graphical analysis of non-categorical data or data with multiple categories--bivariate
![image](https://user-images.githubusercontent.com/94619247/164976838-fb069208-50ac-4ac9-9fd5-bf8ae4d7a0a2.png)
![image](https://user-images.githubusercontent.com/94619247/164976849-cf9be33b-7936-4139-bd67-e0938ac6126b.png)
![image](https://user-images.githubusercontent.com/94619247/164976859-7c61fcc5-61a6-49d3-bae9-e961c2dbfb78.png)
![image](https://user-images.githubusercontent.com/94619247/164976871-9681944b-542f-4b8c-ba3d-edd3cd1db207.png)
![image](https://user-images.githubusercontent.com/94619247/164976894-f4300b82-504c-4fe5-b2f2-186560913e33.png)
![image](https://user-images.githubusercontent.com/94619247/164976910-31ff124c-4010-4b9f-af4f-a29acfab38e9.png)
![image](https://user-images.githubusercontent.com/94619247/164976926-d56b22db-ef1e-4a9d-835d-13c129b18f52.png)
![image](https://user-images.githubusercontent.com/94619247/164976941-62239982-55bf-44c5-9b72-1260e2a8dbcc.png)
# graphical representation of data--multivariate
![image](https://user-images.githubusercontent.com/94619247/164976975-cc7f766a-0a98-4db1-adea-b681e2a8c076.png)
# RESULT
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.

