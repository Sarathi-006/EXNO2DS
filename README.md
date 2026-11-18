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
<img width="1300" height="510" alt="Screenshot 2026-11-18 153657" src="https://github.com/user-attachments/assets/0b64dc30-8f73-45e3-97ac-3e67869858c1" />
<img width="515" height="470" alt="Screenshot 2026-11-18 154514" src="https://github.com/user-attachments/assets/578d6ede-d93e-4347-87f6-71f61c0129eb" />
<img width="735" height="298" alt="Screenshot 2026-11-18 154606" src="https://github.com/user-attachments/assets/cd85634f-73c9-47b8-b5de-1bde245e1a75" />

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
<img width="571" height="717" alt="Screenshot 2026-11-18 154716" src="https://github.com/user-attachments/assets/846f2305-6050-4b67-9c17-fa24f379a948" />

```
plt.figure(figsize=(6, 4))

sns.countplot(data=dt, x="Survived")

plt.title("Survival Count")
plt.xlabel("Survived")
plt.ylabel("Count")

plt.show()
```
<img width="677" height="492" alt="Screenshot 2026-11-18 154749" src="https://github.com/user-attachments/assets/06416e08-0253-4d1b-8932-6fb438eea00b" />

```
dt.rename(columns={"Sex": "Gender"}, inplace=True)

dt
```
<img width="1360" height="446" alt="Screenshot 2026-11-18 154921" src="https://github.com/user-attachments/assets/0f9d02d9-0302-4d4c-965f-e21966282eb3" />

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
<img width="721" height="633" alt="Screenshot 2026-11-18 154952" src="https://github.com/user-attachments/assets/88a0755d-ec0f-4eba-abeb-026ebe8ec9cb" />

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
<img width="860" height="582" alt="image" src="https://github.com/user-attachments/assets/29b1817a-8992-470f-974d-895af513738a" />

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
<img width="855" height="582" alt="image" src="https://github.com/user-attachments/assets/9b00a4df-0bee-4479-a7ad-6cdaeaf8204a" />

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
<img width="1046" height="677" alt="image" src="https://github.com/user-attachments/assets/7e6360c0-1715-4faf-96e7-74f6cdfac5ed" />

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
<img width="1037" height="636" alt="image" src="https://github.com/user-attachments/assets/c63f00c4-db14-471e-8f94-083c5f211635" />

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

<img width="1122" height="840" alt="image" src="https://github.com/user-attachments/assets/9c3ba9f0-68b8-454b-b5e6-e278d8523269" />



# RESULT
        <<INCLUDE YOUR RESULT HERE>>
