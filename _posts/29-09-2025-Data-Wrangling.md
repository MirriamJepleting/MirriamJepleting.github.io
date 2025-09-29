---
title: Data Wrangling with Python – Netflix Dataset
icon: fa-database
date: 2025-09-29
description: A detailed walkthrough of cleaning and structuring the Netflix dataset using Python on Kaggle.
---
```

# Data Wrangling with Python – Netflix Dataset

## Introduction

This project involved developing hands-on experience automating web data gathering using a Kaggle dataset and publishing the results on Kaggle. I aimed to understand and apply data wrangling concepts to clean up the Netflix dataset available on Kaggle.

**Dataset Link:** [Netflix Shows on Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows)

The objectives of the project were to:

1. Load the Netflix dataset from a CSV file and explore its structure using pandas.
2. Perform data discovery to assess data types, missing values, and quality issues.
3. Clean the dataset by handling duplicates, missing values, and formatting inconsistencies.
4. Transform and enrich the dataset using techniques like filtering, sorting, grouping, and feature extraction.
5. Validate the final dataset by checking consistency, completeness, and logical accuracy.
6. Export the final cleaned dataset to a .csv file ready for analysis or visualization.

---

## Discovery

### Step I: Start of the Project

The first step was defining the title and a brief description of the project that I intended to complete. Secondly, I imported the required libraries to get started.

```python
import pandas as pd
import numpy as np
```

### Step II: Importing the Data and Overview

The third step of the project involved importing the dataset. The Netflix dataset was stored in CSV format. I then displayed the number of rows and columns before showing a quick overview of the data, including data types and non-null values.

```python
df = pd.read_csv("../input/netflix-shows/netflix_titles.csv")
df.info()
df.head()
```

### Step III: Finding Missing Values and Duplicates

Next, I  discovered the missing values per column in the dataset, then output it. After finding the missing values, the second step involved counting the duplicated rows

```python
df.isnull().sum()
df.duplicated().sum()
```

---

## Data Structuring

### Step I: Type Casting, Standardization, and Splitting

The first structuring step involved converting the `release_year` column to integers for consistency. I also standardized the `type` column to avoid mismatches, and split the `listed_in` (genres) column into multiple categories for filtering and counting.

```python
df['release_year'] = df['release_year'].astype(int)
df['listed_in'] = df['listed_in'].str.split(', ')
```

### Step II: Standardization, Replacing Missing Values, and Creating Binary Features

Some rows had multiple countries, such as *United States and India*. To make the dataset more useful, I standardized the country column. Missing values in `cast` and `director` were replaced, and I created a binary column `is_recent` to quickly flag modern content.

```python
df['director'] = df['director'].fillna("Not Given")
df['cast'] = df['cast'].fillna("Not Given")
df['country'] = df['country'].fillna("Not Given")
df['is_recent'] = df['release_year'] > 2015
```

### Step III: Fixing Date Features

I split the countries into lists to handle each separately and ensured the `date_added` column was in proper datetime format. I also created a new column for easier time-based analysis.

```python
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
```

### Step IV: Viewing and Deduplication

After restructuring, I viewed the updated dataset and performed deduplication to remove repeated rows.

```python
df.drop_duplicates(inplace=True)
```

---

## Cleaning

### Step I: Rechecking Duplicates

At this stage, I confirmed that no duplicates remained. I also removed the `description` column since it was unnecessary for my analysis.

```python
df.drop(columns=['description'], inplace=True)
```

### Step II: Handling Missing Directors with Cast

To fill missing directors, I paired `director` and `cast` into a new column, counted their frequencies, and filtered those that appeared three or more times.

```python
df['dir_cast'] = df['director'].fillna('') + " " + df['cast']
dir_cast_counts = df['dir_cast'].value_counts()
```

### Step III: Creating a Dictionary for Missing Directors

I created a dictionary mapping directors to casts and used it to fill missing director values.

```python
director_dict = dict(zip(df['director'], df['cast']))
df['director'] = df['director'].replace('', 'Not Given')
```

### Step IV: Filling Missing Country and Cast Values

All missing country values were reassigned based on director, while any remaining missing fields were filled with “Not Given.”

```python
df['country'] = df['country'].fillna("Not Given")
df['cast'] = df['cast'].fillna("Not Given")
```

### Step V: Handling Nulls in Dates

I dropped rows with null values in `date_added`, `rating`, or `duration`. Then, I coerced `date_added` into a clean datetime format.

```python
df = df.dropna(subset=['date_added', 'rating', 'duration'])
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
```

### Step VI: Consistency Check

Finally, I checked that `date_added` values aligned with `release_year` by ensuring that no show appeared on Netflix before its release.

```python
df = df[df['release_year'] <= df['date_added'].dt.year]
```

---

## Validation

### Step I: Cleanup

Temporary wrangling columns like `dir_cast` were removed. I also used `df.info()` to check the dataset’s accuracy and completeness.

```python
df.drop(columns=['dir_cast'], inplace=True)
df.info()
```

### Step II: Validation Continued

I ensured correct data types by converting `date_added` where necessary. For the `duration` column, I extracted numeric values. Then I applied sanity checks, such as flagging movies released before 1997, the year Netflix began streaming.

```python
df = df[df['release_year'] >= 1997]
```

### Step III: Rechecking Missing Values

After flagging older movies, I rechecked for missing values. Most columns were clean, except `date_added`, which still had nulls. I replaced these nulls with the string `"unknown"`.

```python
df['date_added'] = df['date_added'].fillna("unknown")
```

---

## Saving

The final steps involved resetting the index for a clean dataset and exporting the cleaned data into CSV and JSON formats.

```python
df.reset_index(drop=True, inplace=True)
df.to_csv("netflix_cleaned.csv", index=False)
df.to_json("netflix_cleaned.json", orient="records")
```

The final dataset contained **8,790 rows with 13 columns**.

---

## Conclusion

Data wrangling is time-consuming and requires significant mental energy, but it is also fulfilling. Through this process, I successfully transformed the raw Netflix dataset into a clean, structured, and analysis-ready format. Missing values were addressed, duplicates and inconsistencies were handled, data types were standardized, and validation checks were applied to ensure reliability.

Temporary columns used for cleaning were removed, and the dataset was reindexed for clarity. The final cleaned dataset is now ready for further analysis and visualization.

👉 [View the complete notebook on Kaggle](https://www.kaggle.com/code/mirriamjepleting/mirriam-jepleting-cs-da02-25087)

---
