# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt = pd.read_csv("titanic_dataset.csv")
dt
dt.info()
print("Number of rows and columns:", dt.shape)
dt.set_index("PassengerId", inplace=True)
dt.describe()
```
<img width="931" height="267" alt="image" src="https://github.com/user-attachments/assets/027aad83-062d-4e37-a8c0-6f755ec7053c" />
<img width="627" height="263" alt="image" src="https://github.com/user-attachments/assets/f706824d-f454-4661-b7ed-210b6707f11c" />
<img width="667" height="185" alt="image" src="https://github.com/user-attachments/assets/1dd5b40c-c9da-47c6-9ea1-61cd341987bf" />


```
print("Survived:")
print(dt["Survived"].value_counts())

print("\nPassenger Class:")
print(dt["Pclass"].value_counts())

print("\nGender:")
print(dt["Sex"].value_counts())

print("\nEmbarked:")
print(dt["Embarked"].value_counts())

print("\nSibSp:")
print(dt["SibSp"].value_counts())

print("\nParch:")
print(dt["Parch"].value_counts())
```
<img width="800" height="417" alt="image" src="https://github.com/user-attachments/assets/2f99bb8b-59af-4613-b28c-cbfe4f553dfd" />


```
plt.figure(figsize=(6, 4))

sns.countplot(data=dt, x="Survived")

plt.title("Survival Count")
plt.xlabel("Survived")
plt.ylabel("Count")

plt.show()
```
<img width="965" height="282" alt="image" src="https://github.com/user-attachments/assets/c27c8013-9c81-44e2-9716-4e56dfadb6d1" />


```
dt.rename(columns={"Sex": "Gender"}, inplace=True)

dt
```
<img width="1152" height="270" alt="image" src="https://github.com/user-attachments/assets/ba968301-cf8a-4faa-acf1-1286c901e87b" />

```
sns.catplot(
    data=dt,
    x="Pclass",
    y="Survived",
    hue="Gender",
    kind="bar"
)

plt.title("Pclass vs Survived by Gender")
plt.show()
```
<img width="1106" height="367" alt="image" src="https://github.com/user-attachments/assets/a9e8fe4a-3547-4862-be34-ae36d35748cc" />

```
fig, ax1 = plt.subplots(figsize=(8, 5))

graph = sns.countplot(
    data=dt,
    x="Pclass",
    hue="Survived",
    ax=ax1
)

for p in graph.patches:
    height = p.get_height()

    graph.text(
        p.get_x() + p.get_width()/2,
        height + 5,
        int(height),
        ha="center"
    )

plt.title("Passenger Class and Survival Count")
plt.xlabel("Passenger Class")
plt.ylabel("Count")

plt.show()
```

<img width="1150" height="340" alt="image" src="https://github.com/user-attachments/assets/2858404d-d078-46aa-af6d-510c4d03968f" />

```
plt.figure(figsize=(8, 5))

sns.boxplot(
    data=dt,
    x="Survived",
    y="Age"
)

plt.title("Age vs Survived")
plt.xlabel("Survived")
plt.ylabel("Age")

plt.show()
```

<img width="1036" height="336" alt="image" src="https://github.com/user-attachments/assets/588c5d41-fcd5-4b02-bf3a-997b3b793c35" />


```
plt.figure(figsize=(10, 6))

sns.boxplot(
    data=dt,
    x="Pclass",
    y="Age",
    hue="Gender"
)

plt.title("Pclass vs Age by Gender")
plt.xlabel("Passenger Class")
plt.ylabel("Age")

plt.show()
```

<img width="1288" height="396" alt="image" src="https://github.com/user-attachments/assets/a626fe82-0172-497c-b8a8-064680e3be2b" />

```
sns.catplot(
    data=dt,
    x="Pclass",
    y="Survived",
    hue="Gender",
    kind="bar",
    height=5,
    aspect=1.5
)

plt.title("Pclass vs Survived by Gender")

plt.show()
```
<img width="1158" height="367" alt="image" src="https://github.com/user-attachments/assets/e179037c-bf37-4a0a-a118-a1d5d5cff0dc" />

```
plt.figure(figsize=(12, 8))

sns.heatmap(
    dt.select_dtypes(include=np.number).corr(),
    annot=True,
    cmap="coolwarm",
    linewidths=0.5
)

plt.title("Correlation Heatmap")

plt.show()
```


<img width="1380" height="492" alt="image" src="https://github.com/user-attachments/assets/3c86734c-2725-476e-bd82-1b77109504d9" />



# RESULT
Thus, Exploratory Data Analysis for the given dataset is done successfully.
