# Week8Assignment
import pandas as pd

# Load Titanic dataset from web
url = "https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"
df = pd.read_csv(url)

# Display first 5 rows
print("First 5 rows:")
print(df.head())

# Check data types
print("\nData Types:")
print(df.dtypes)

# Check missing values
print("\nMissing Values:")
print(df.isnull().sum())

# Handle missing values
df['Age'] = df['Age'].fillna(df['Age'].median())  # Fill missing ages with median
df = df.dropna(subset=['Embarked'])  # Drop rows with missing Embarked values

print("\nBasic Statistics:")
print(df.describe())

print("\nMean Age by Passenger Class:")
print(df.groupby('Pclass')['Age'].mean())

import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(12, 5))
plt.plot(df['PassengerId'], df['Age'], color='blue', alpha=0.5)
plt.title("Age Distribution Across Passengers")
plt.xlabel("Passenger ID")
plt.ylabel("Age")
plt.grid(True)
plt.show()


plt.figure(figsize=(8, 5))
sns.barplot(x='Pclass', y='Survived', data=df, palette='viridis')
plt.title("Survival Rate by Passenger Class")
plt.xlabel("Passenger Class")
plt.ylabel("Survival Rate")
plt.show()


plt.figure(figsize=(8, 5))
sns.histplot(df['Age'], bins=20, kde=True, color='green')
plt.title("Age Distribution of Passengers")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()

plt.figure(figsize=(8, 5))
sns.scatterplot(x='Age', y='Fare', hue='Survived', data=df, palette='coolwarm')
plt.title("Age vs. Fare Paid (Colored by Survival)")
plt.xlabel("Age")
plt.ylabel("Fare ($)")
plt.legend(title='Survived')
plt.show()

try:
    df = pd.read_csv("titanic.csv")
except FileNotFoundError:
    print("Local file not found. Loading from web...")
    df = pd.read_csv("https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv")




