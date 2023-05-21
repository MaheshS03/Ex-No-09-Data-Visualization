# Ex-No-09-Data-Visualization
# AIM:
  To Perform Data Visualization on a complex dataset and save the data to a file.
# EXPLANATION:
  Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.
# ALGORITHM:
## STEP-1:
  Read the given Data.
## STEP-2:
  Clean the Data Set using Data Cleaning Process.
## STEP-3:
  Apply Feature generation and selection techniques to all the features of the data set.
## STEP-4:
  Apply data visualization techniques to identify the patterns of the data.
# CODE:
import seaborn as sns

import pandas as pd

import matplotlib.pyplot as plt

tips = sns.load_dataset('tips')

tips

## Data Cleaning Process:
tips.describe()

tips.info()

tips.isnull().sum()

~tips.duplicated()

df1=tips[~tips.duplicated()]

df1

sns.boxplot(x="day", y="total_bill", hue="smoker", data=tips, linewidth=2, width=0.6, boxprops={"facecolor": "lightblue", "edgecolor": "darkblue"},
            whiskerprops={"color": "black", "linestyle": "--", "linewidth": 1.5 },
            capprops={"color": "black", "linestyle": "--", "linewidth": 1.5})

## Day of the week has the highest total bill amount:
sns.barplot(x=tips['day'], y=tips['total_bill'],hue=tips['sex'])

plt.xlabel('Day of the Week')

plt.ylabel('Total Bill')

plt.show()

## Average tip amount given by smokers and non-smokers:
avg_tip = tips.groupby('smoker')['tip'].mean()

p1= plt.bar(avg_tip.index, avg_tip, label='Tip', width=0.4)

plt.title('Average tip amount given by smokers and non-smokers')

plt.show()

## Tip percentage vary based on the size of the dining party:
tips["tip_per"] = tips["tip"] / tips["total_bill"]

sns.scatterplot(x="size", y="tip_per", data=tips)

plt.title("Tip Percentage by Dining Party Size")

plt.show()

## Gender tends to leave higher tips:
states=tips.loc[:,["sex","tip"]]

states=states.groupby(by=["sex"]).sum().sort_values(by="tip")

sns.barplot(x=states.index,y="tip",data=states)

plt.xlabel=("Sex")

plt.ylabel=("Tips")

plt.show()

## Relationship between the total bill amount and the day of the week:
sns.histplot(data=tips, x="total_bill", hue="time", element="step", stat="density")

plt.title("Distribution of Total Bill Amounts by Time of Day")

plt.show()

## Distribution of total bill amounts vary across different time periods:
sns.relplot(data=tips,x=tips["time"],y=tips["total_bill"],hue="time")

## Dining party size group tends to have the highest average total bill amount:
avg_total_bill = tips.groupby('size')['total_bill'].mean()

p1 = plt.bar(avg_total_bill.index, avg_total_bill, label='Total Bill', width=0.4)

plt.title('Average Total bill amount given by Dining Party Size')

plt.show()

## Distribution of tip amounts for each day of the week:
sns.relplot(data=tips,x="day",y="tip",hue="day")

## Tip amount vary based on the type of service:
sns.barplot(x=tips['time'], y=tips['tip'])

plt.xlabel=("Service")

plt.ylabel=("Tips")

plt.show()

## Correlation between the total bill amount and the tip amount:
tips.corr()

sns.heatmap(tips.corr(),annot=True)

sns.scatterplot(x="total_bill", y="tip", data=tips)

plt.title("Correlation between Tip Amount and Total Bill Amount")

plt.show()

# OUTPUT:
![Screenshot (73)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/0d91bfdb-5ffa-4d67-861e-1ea1d94427a5)

## Data Cleaning Process:
![Screenshot (74)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/de28d1d5-e17d-4df1-a319-18645a5b66b4)

![Screenshot (75)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/b7af63fd-b60b-453b-90a0-5fe91588bb5f)

![Screenshot (76)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/1ddab71c-a9ba-4f45-8961-02dfd17c5d8b)

![Screenshot (77)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/f1412644-6b14-4ad4-bd0c-bb1ce720f62d)

![Screenshot (78)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/db1e16fa-21bb-4e3e-880e-57d92bc48f94)

## Day of the week has the highest total bill amount:
![Screenshot (79)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/2f1d3140-acf2-4fa7-870b-95a382be7a75)

## Average tip amount given by smokers and non-smokers:
![Screenshot (80)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/574d1346-938d-42f4-89a0-e02254e75bb7)

## Tip percentage vary based on the size of the dining party:
![Screenshot (81)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/487b5d32-4c98-4340-a324-c261abe3b258)

## Gender tends to leave higher tips:
![Screenshot (82)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/08d4f728-c17c-4dc4-95fc-83dde2495788)

## Relationship between the total bill amount and the day of the week:
![Screenshot (83)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/fd7b6ca7-c95c-4358-84d4-ad57a17a9d03)

## Distribution of total bill amounts vary across different time periods:
![Screenshot (84)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/43db86d9-d801-4bcc-8a6a-72de36cd5385)

## Dining party size group tends to have the highest average total bill amount:
![Screenshot (85)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/81954653-9abb-45b1-9d5b-6da302c473d1)

## Distribution of tip amounts for each day of the week:
![Screenshot (86)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/8dfd692d-5360-4dd8-9dbf-ca593d1d0f02)

## Tip amount vary based on the type of service:
![Screenshot (87)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/1382c973-cac0-44b3-a998-4304ebdb00fe)

## Correlation between the total bill amount and the tip amount:
![Screenshot (88)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/2046f352-fd5c-4d33-bbcc-c20aa5010891)

![Screenshot (89)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/810d5ae6-bffc-4119-997e-2b92b810df33)

![Screenshot (90)](https://github.com/MaheshS03/Ex-No-09-Data-Visualization/assets/128498431/e9967699-a7fa-4b21-a42f-4d60f0192f21)

# RESULT:
 Thus the Data Visualization techniques were performed for the given dataset and output was verified successfully.
