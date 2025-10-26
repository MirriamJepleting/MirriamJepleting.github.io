---
layout: post
title: "Exploratory Data Analysis (EDA) on the Titanic Dataset"
categories: [Projects, Data Analysis,EDA]
author: "Mirriam Jepleting"
---

## Introduction  
This project focused on performing **Exploratory Data Analysis (EDA)** using a Kaggle dataset to gain hands-on experience in Python data analytics.  
The goal was to understand data patterns, clean and preprocess the dataset, and uncover meaningful insights through data exploration and visualization.  

**Kaggle Notebook:** [Mirriam Jepleting EDA Analysis](https://www.kaggle.com/code/mirriamjepleting/mirriam-jepleting-ed-analysis)

---

## Tools and Libraries Used  
- **Python**  
- **Pandas** – Data manipulation and analysis  
- **NumPy** – Numerical computation  
- **Matplotlib** and **Seaborn** – Data visualization  

---

## Key Steps in the Analysis  

### 1. Data Loading and Preview  
- Loaded the dataset (`train.csv`) from Kaggle.  
- Previewed the first few rows to understand the dataset structure and variables.

### 2. Data Exploration  
- Examined dataset shape, information, and summary statistics.  
- Found **891 passenger records** with a **38% survival rate**, indicating class imbalance.  
- Identified missing values in `Age`, `Cabin`, and `Embarked`.

### 3. Handling Missing Values  
- Replaced missing values in `Age` with the **median**.  
- Filled missing `Embarked` entries with the **mode**.  
- Dropped the `Cabin` column due to excessive missing data.  
- Verified that no null values remained.

### 4. Outlier Detection and Treatment  
- Detected outliers in the `Fare` variable using boxplots.  
- Applied a **log transformation** to normalize the distribution and reduce skewness.

### 5. Univariate Analysis  
- **Age:** Most passengers were between 28–32 years.  
- **Fare:** Distribution was highly right-skewed; most fares were low.  
- **Gender and Embarked:** More male passengers than female; most embarked from 'S'.

### 6. Bivariate Analysis  
- **Fare vs. Pclass:** Higher class corresponded to higher fare.  
- **Age vs. Survival:** Children had higher survival rates.  
- **Gender vs. Survival:** Females survived more than males.  
- **Embarked vs. Survival:** Passengers from 'C' had slightly better survival chances.

### 7. Multivariate Analysis  
- Combined `Age`, `Fare`, `Pclass`, and `Embarked` with `Survival`.  
- Found that **female passengers in higher classes** and **young children** had the highest survival probabilities.

### 8. Target Variable Exploration  
- Non-survivors: approximately **550**  
- Survivors: approximately **340**  
- Females consistently showed higher survival rates across all classes.

---

## Key Insights  
- **Sex and Passenger Class** were the most significant survival determinants.  
- **Fare** was closely related to both **Pclass** and **Survival**.  
- Effective **outlier handling** and **data cleaning** improved data clarity and interpretation.

---

## Conclusion  
This Exploratory Data Analysis provided valuable insights into the Titanic dataset and demonstrated the importance of thorough data cleaning and visualization.  
Through this project, I gained practical skills in exploring, interpreting, and communicating data insights effectively using Python and Kaggle.  

---

**Kaggle Notebook:** [Mirriam Jepleting EDA Analysis](https://www.kaggle.com/code/mirriamjepleting/mirriam-jepleting-ed-analysis)  
**Prepared by:** *Mirriam Jepleting*
