---
title: "Week 1 Assignment – Web Scraping and Data Handling in Python"
date: 2025-09-29 10:00:00 +0300
categories: [Assignments, Data Analysis]
tags: [Python, Web Scraping, BeautifulSoup, Pandas]
---

## Introduction

My first week assignment requirements were based on the extraction of data using web scraping.  
Despite the few challenges that I encountered, I was able to write the code and execute it successfully.  

The process involved creating my Google Colab account and setting up the environment to complete the assignment.  

### Objectives:
1. Practical Python coding on Jupyter Notebooks hosted on Google Colab  
2. Use `requests` and `BeautifulSoup` to extract data from a web page  
3. Parse and clean the extracted data  
4. Store structured data into a Pandas DataFrame  
5. Export the final dataset to a `.csv` file  

---

## Steps Completed

### Step I: Setup
Created my Google Colab account and confirmed the environment worked.

### Step II: Project Definition
Defined the title and brief description of the project.

### Step III: Importing Required Libraries
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
````

### Step IV: Fetching and Loading the URL

```python
url = "https://www.scrapethissite.com/pages/forms/"
response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")
```

### Step V: Parsing HTML Content

```python
table = soup.find("table", class_="table")
```

### Step VI: Extracting Required Data

```python
rows = table.find_all("tr")
print(len(rows))  # check number of rows
```

### Step VII: Extracting Hockey Scores

```python
for row in rows[1:]:
    cols = row.find_all("td")
    data = [col.text.strip() for col in cols]
    print(data)
```

### Step VIII: Extracting Column Headings

```python
headers = [header.text.strip() for header in table.find_all("th")]
print(headers)
```

### Step IX: Creating an Empty DataFrame

```python
df = pd.DataFrame(columns=headers)
```

### Step X: Reading and Cleaning Table Data

```python
for row in rows[1:]:
    cols = row.find_all("td")
    each_row = [col.text.strip() for col in cols]
    df.loc[len(df)] = each_row
```

### Step XI: Previewing the Data

```python
print(df.head())
```

### Final Step: Saving Data to CSV

```python
df.to_csv("Hockey.csv", index=False)

# Reload to confirm
df_check = pd.read_csv("Hockey.csv")
print(df_check.head())
```

---

## Conclusion

During this as I was able to gain insights into:

* Web scraping with Python
* Text cleaning and processing
* Creating and manipulating Pandas DataFrames
* Saving and loading data from CSV

This is a valuable introduction to **data science with Python**, and I look forward to building on these concepts in the coming weeks.

🔗 [View my full code on Google Colab](https://colab.research.google.com/drive/1lhv1h00kDUxZ9th5MSs7uEmhjqpu8D9d?usp=sharing)



