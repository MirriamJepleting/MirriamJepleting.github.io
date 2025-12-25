---
layout: post
title: Linear Regression for Housing Price Prediction
categories: [Projects, Data Analysis, Machine Learning, Regression]
author: Mirriam Jepleting
---

## Introduction

This project focuses on building a **Linear Regression model** using Python to predict **house prices based on house area**.  
The goal was to gain hands-on experience in data exploration, preparation, model training, evaluation, and visualization using a simple real-world dataset.

This project was completed as part of **Week 7 of the Cyber Shujaa Program – Data & Artificial Intelligence track**.

---

## Dataset Description

The dataset contains two numerical variables:

- **area**: House size in square feet (independent variable)
- **price**: House price (dependent variable)

The simplicity of the dataset makes it ideal for understanding the fundamentals of regression modeling.

---

## Tools and Libraries Used

- Python  
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- Google Colab  

---

## Importing Required Libraries

The following libraries were used for data manipulation, visualization, and machine learning:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
Data Loading and Exploration

The dataset was loaded into a pandas DataFrame and inspected to understand its structure and data types.

df = pd.read_csv("data/housing_prices.csv")

df.head()
df.shape
df.info()


This confirmed that the dataset was clean, well-structured, and suitable for regression analysis.

Descriptive Statistics

Descriptive statistics were generated to understand the distribution and spread of the data.

df.describe()


This helped identify average values, variability, and potential outliers before modeling.

Data Visualization

A scatter plot was used to examine the relationship between house area and price.

plt.figure(figsize=(6, 4))
plt.scatter(df["area"], df["price"], color="blue")
plt.xlabel("Area (sq ft)")
plt.ylabel("Price")
plt.title("Scatter Plot of Area vs Price")
plt.show()


The visualization shows a positive linear relationship, suggesting that a linear regression model is appropriate.

Data Preparation

Missing values were checked, and the feature and target variables were defined.

df.isnull().sum()

X = df[["area"]]
y = df["price"]


No missing values were found, so no additional cleaning was required.

###Model Training

The dataset was split into training and testing sets, and a Linear Regression model was trained.

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

model = LinearRegression()
model.fit(X_train, y_train)


This allows the model to learn patterns from training data and generalize to unseen data.

###Model Evaluation

The model was evaluated using Mean Squared Error (MSE) and R-squared (R²).

y_pred = model.predict(X_test)

mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"Mean Squared Error (MSE): {mse:.2f}")
print(f"R-squared (R²): {r2:.2f}")


A low MSE indicates small prediction errors

A high R² shows that the model explains most of the variance in house prices

Results Visualization

The regression line was plotted alongside the actual data points.

plt.figure(figsize=(6, 4))
plt.scatter(X, y, color="blue", label="Actual Data")
plt.plot(X, model.preict(X), color="red", label="Regression Line")
plt.xlabel("Area (sq ft)")
plt.ylabel("Price")
plt.title("Linear Regression: Area vs Price")
plt.legend()
plt.show()


The regression line closely fits the data points, confirming good model performance.

##Conclusion

Despite the small dataset size, this project provided valuable hands-on experience in building and evaluating a regression model.
It strengthened my understanding of:

Feature–target relationships

##Model evaluation metrics

##Visual interpretation of regression results

This project demonstrates how linear regression can be applied to make meaningful predictions from real-world data.

Notebook Link https://colab.research.google.com/drive/1E2qVhchYP2Ve7yaOHs3R2MSKgzMkFgD_?usp=sharing


