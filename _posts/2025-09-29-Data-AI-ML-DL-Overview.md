---
title: "Web Scraping and Data Handling in Python"
date: 2025-09-29 10:00:00 +0300
categories: [Projects, Data Analysis]
tags: [Python, Web Scraping, BeautifulSoup, Pandas]
---

## Introduction

This project focused on extracting structured data from a webpage through **web scraping techniques**.  
The goal was to demonstrate how Python can be used to collect, process, and store real-world data.  

The process involved using **Google Colab** to set up the environment and execute the workflow end-to-end.  

### Key Objectives
1. Write Python code in a Jupyter Notebook hosted on Google Colab  
2. Use `requests` and `BeautifulSoup` to extract data from a webpage  
3. Parse and clean the extracted HTML content  
4. Store structured data in a Pandas DataFrame  
5. Export the dataset into a `.csv` file for reuse  

---

## Project Workflow

### Step I: Setup
Configured Google Colab and ensured the environment was ready.

### Step II: Project Definition
Outlined the scope and objectives of the web scraping task.

---

### Step III: Importing Required Libraries
We import the necessary Python libraries:  
- **requests** for fetching webpages,  
- **BeautifulSoup** for HTML parsing,  
- **pandas** for data handling.  

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
````

---

### Step IV: Fetching and Loading the URL

Fetch the webpage and load it into BeautifulSoup for parsing.

```python
url = "https://www.scrapethissite.com/pages/forms/"
response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")
```

---

### Step V: Parsing HTML Content

Identify the HTML `<table>` containing the hockey data.

```python
table = soup.find("table", class_="table")
```

---

### Step VI: Extracting Table Rows

Extract all table rows (`<tr>`) for further processing.

```python
rows = table.find_all("tr")
print(len(rows))  # number of rows
```

---

### Step VII: Extracting Hockey Scores

Loop through rows to extract and clean the cell values.

```python
for row in rows[1:]:
    cols = row.find_all("td")
    data = [col.text.strip() for col in cols]
    print(data)
```

---

### Step VIII: Extracting Column Headings

Retrieve table headers (`<th>`) to use as DataFrame columns.

```python
headers = [header.text.strip() for header in table.find_all("th")]
print(headers)
```

---

### Step IX: Creating a DataFrame

Initialize a Pandas DataFrame with the extracted headers.

```python
df = pd.DataFrame(columns=headers)
```

---

### Step X: Populating the DataFrame

Clean each row and insert it into the DataFrame.

```python
for row in rows[1:]:
    cols = row.find_all("td")
    each_row = [col.text.strip() for col in cols]
    df.loc[len(df)] = each_row
```

---

### Step XI: Previewing the Data

Inspect the first rows of the DataFrame to confirm data integrity.

```python
print(df.head())
```

---

### Final Step: Exporting Data to CSV

Save the DataFrame to a CSV file and reload it to confirm.

```python
df.to_csv("Hockey.csv", index=False)

# Reload to verify
df_check = pd.read_csv("Hockey.csv")
print(df_check.head())
```

---

## Conclusion

This project provided practical experience with:

* **Web scraping in Python** using `requests` and `BeautifulSoup`
* **Parsing and cleaning HTML** for structured use
* **Working with Pandas DataFrames** to organize tabular data
* **Exporting datasets** to CSV for future analysis

The workflow demonstrates how raw webpage data can be transformed into a clean, reusable dataset using Python.

🔗 [View the full project on Google Colab](https://colab.research.google.com/drive/1lhv1h00kDUxZ9th5MSs7uEmhjqpu8D9d?usp=sharing)

```



