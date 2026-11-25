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

# EXPLORATORY DATA ANALYSIS ON TITANIC DATASET

# 1. Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from google.colab import files

# 2. Upload Dataset
uploaded = files.upload()
df = pd.read_csv('titanic_dataset.csv')

print("TITANIC DATASET LOADED SUCCESSFULLY")

# 3. Display Dataset
print("\nFIRST FIVE ROWS")
display(df.head())

print("\nLAST FIVE ROWS")
display(df.tail())

print("\nDATASET SHAPE")
print(df.shape)

# 4. Dataset Information
print("\nDATASET INFORMATION")
df.info()

print("\nCOLUMN NAMES")
print(df.columns)

print("\nDATA TYPES")
print(df.dtypes)

# 5. Missing Value Analysis
print("\nMISSING VALUES")
print(df.isnull().sum())

print("\nMISSING VALUE PERCENTAGE")
print((df.isnull().sum() / len(df)) * 100)

# Visualize Missing Values
plt.figure(figsize=(10, 5))
sns.heatmap(df.isnull(), cbar=False, cmap='viridis')
plt.title("Missing Values Heatmap")
plt.show()

# 6. Duplicate Value Analysis
print("\nDUPLICATE ROWS")
print(df.duplicated().sum())

df = df.drop_duplicates()
print("Shape after removing duplicates:", df.shape)

# 7. Statistical Analysis
print("\nSTATISTICAL SUMMARY")
display(df.describe(include='all'))

# 8. Survival Count
plt.figure(figsize=(6, 4))
sns.countplot(x='Survived', data=df)
plt.title("Survival Count")
plt.xlabel("Survived (0 = No, 1 = Yes)")
plt.ylabel("Number of Passengers")
plt.show()

# 9. Gender Distribution
plt.figure(figsize=(6, 4))
sns.countplot(x='Sex', data=df)
plt.title("Gender Distribution")
plt.show()

# 10. Passenger Class Distribution
plt.figure(figsize=(6, 4))
sns.countplot(x='Pclass', data=df)
plt.title("Passenger Class Distribution")
plt.show()

# 11. Age Distribution
plt.figure(figsize=(7, 4))
sns.histplot(df['Age'].dropna(), kde=True)
plt.title("Age Distribution")
plt.xlabel("Age")
plt.show()

# 12. Survival by Gender
plt.figure(figsize=(6, 4))
sns.countplot(x='Sex', hue='Survived', data=df)
plt.title("Survival by Gender")
plt.show()

# 13. Survival by Passenger Class
plt.figure(figsize=(6, 4))
sns.countplot(x='Pclass', hue='Survived', data=df)
plt.title("Survival by Passenger Class")
plt.show()

# 14. Correlation Analysis
numeric_df = df.select_dtypes(include=np.number)

plt.figure(figsize=(10, 6))
sns.heatmap(numeric_df.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()

# 15. Outlier Detection using Boxplot - Age
plt.figure(figsize=(7, 4))
sns.boxplot(x=df['Age'])
plt.title("Age Outlier Detection")
plt.show()

# 16. Outlier Detection using Boxplot - Fare
plt.figure(figsize=(7, 4))
sns.boxplot(x=df['Fare'])
plt.title("Fare Outlier Detection")
plt.show()

# 17. Final EDA Summary
print("\n========== EDA SUMMARY ==========")

print("Total Rows:", df.shape[0])
print("Total Columns:", df.shape[1])

print("\nMissing Values:")
print(df.isnull().sum())

print("\nSurvival Count:")
print(df['Survived'].value_counts())

print("\nAverage Age:", df['Age'].mean())
print("Average Fare:", df['Fare'].mean())

print("\nEDA COMPLETED SUCCESSFULLY!")

```
<img width="1727" height="842" alt="image" src="https://github.com/user-attachments/assets/0c1b0633-237f-4dcf-a35b-ed9b5170f7e9" />
<img width="803" height="816" alt="image" src="https://github.com/user-attachments/assets/96ae71c4-6ce0-4ed4-81e0-e155e3784d97" />
<img width="513" height="632" alt="image" src="https://github.com/user-attachments/assets/ae817381-0b7d-4a8d-8fa0-542cf7310422" />
<img width="1216" height="773" alt="image" src="https://github.com/user-attachments/assets/6e37b8ad-eae2-441c-ac1f-9fde97ab9b16" />
<img width="1380" height="582" alt="image" src="https://github.com/user-attachments/assets/7aac64cb-f5a6-45bb-a838-e111f4bf0567" />
<img width="687" height="493" alt="image" src="https://github.com/user-attachments/assets/d1250ff7-fd49-4207-bb58-e18347423047" />
<img width="680" height="483" alt="image" src="https://github.com/user-attachments/assets/40a9be87-5444-4af6-8798-ede14be8c32e" />
<img width="665" height="501" alt="image" src="https://github.com/user-attachments/assets/ee7ccded-94f2-4c08-9e5c-8766ce34d322" />
<img width="772" height="486" alt="image" src="https://github.com/user-attachments/assets/5a2a94e0-d4a8-4ae9-84f1-df434a11d480" />
<img width="675" height="487" alt="image" src="https://github.com/user-attachments/assets/7a76261b-d447-456b-95a4-fb761db33f7b" />
<img width="670" height="506" alt="image" src="https://github.com/user-attachments/assets/2f61ad18-c05d-49b8-ac8a-46be5169d859" />
<img width="1046" height="681" alt="image" src="https://github.com/user-attachments/assets/6776f188-2ef2-4e46-a4a9-8ff6d35d052e" />
<img width="757" height="491" alt="image" src="https://github.com/user-attachments/assets/f4de7bc8-8a24-4085-96ee-d82df8781ce1" />
<img width="712" height="515" alt="image" src="https://github.com/user-attachments/assets/24844da9-a79e-4e73-9203-01754cc4243f" />
<img width="361" height="628" alt="image" src="https://github.com/user-attachments/assets/a9592cea-3422-43ff-a11e-5c7cf7169b04" />


# RESULT

The Titanic dataset was successfully analysed using EDA techniques to identify missing values, duplicates, statistical summaries, patterns and outliers.
Visualizations helped understand passenger survival, gender distribution, age distribution and correlations between numerical features.

# SUMMARY
The Titanic dataset is analyzed using Python libraries such as Pandas, NumPy, Matplotlib, and Seaborn.
1. Data Loading: Imported the Titanic dataset and displayed its information, rows, columns, and statistical summary.
2. Categorical Analysis: Used value_counts() to analyze categorical columns.
3. Univariate Analysis: Used countplot to analyze passenger survival and identified unique passenger classes.
4. Column Renaming: Renamed the Sex column to Gender.
5. Bivariate Analysis: Used catplot and boxplot to study relationships between passenger class, age, gender, and survival.
6. Multivariate Analysis: Used boxplot and catplot to analyze multiple columns together.
7. Heatmap: Identified correlations between numerical variables.
8. Pairplot: Visualized relationships between different numerical columns.
