# Data-Cleaning-Preprocessing-Elevate-Lab-Task-1
This project involves cleaning and preprocessing the Netflix Movies and TV Shows dataset from Kaggle. It addresses real-world data issues like missing values, duplicates, inconsistent formats, and incorrect types. The result is a clean dataset ready for analysis, visualization, or machine learning tasks in data science workflows.
# 🧹 Data Cleaning and Preprocessing Task

## 📌 Objective

The objective of this task is to clean and prepare a raw dataset by identifying and fixing common data quality issues such as:
- Missing values
- Duplicate rows
- Inconsistent formatting
- Incorrect data types
- Unclean column names

We will use the **Netflix Movies and TV Shows** dataset from Kaggle for this task.

---

## 🛠️ Tools Used

- **Language:** Python 3.x  
- **Library:** `pandas`  
- **IDE:** Jupyter Notebook / VS Code / Google Colab  
- **Optional Tool:** Microsoft Excel (for manual filtering if needed)

---

## 📁 Dataset Used

- Dataset Name: **Netflix Movies and TV Shows**  
- Source: [Kaggle Netflix Dataset](https://www.kaggle.com/datasets/shivamb/netflix-shows)  
- Filename: `netflix_titles.csv`

---

## 🧪 Step-by-Step Cleaning Process

### 1. Load Dataset
```python
import pandas as pd
df = pd.read_csv("netflix_titles.csv")
```

---

### 2. Initial Inspection
```python
df.head()
df.info()
df.isnull().sum()
```

---

### 3. Remove Duplicates
```python
df = df.drop_duplicates()
```

---

### 4. Handle Missing Values
```python
df['director'].fillna('Unknown', inplace=True)
df['cast'].fillna('Unknown', inplace=True)
df['country'].fillna('Unknown', inplace=True)
df.dropna(subset=['date_added', 'rating', 'duration'], inplace=True)
```

---

### 5. Standardize Text Values
```python
df['country'] = df['country'].str.strip().str.title()
df['rating'] = df['rating'].str.strip().str.upper()
```

---

### 6. Convert Date Format
```python
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
```

---

### 7. Rename Columns
```python
df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')
```

---

### 8. Validate Data Types
```python
df.dtypes
```

---

## ✅ Final Summary

| Feature                | Status                         |
|------------------------|---------------------------------|
| Duplicates Removed     | ✅ Yes (none found)            |
| Missing Values Fixed   | ✅ Filled or Dropped           |
| Text Standardized      | ✅ Country, Rating             |
| Date Format Fixed      | ✅ Converted to datetime       |
| Column Names Cleaned   | ✅ Lowercase, underscore format|
| Data Types Checked     | ✅ release_year (int), date_added (datetime) |

---

## 📊 Results

- **Original Rows:** 8807  
- **Cleaned Rows:** 8790  
- **Removed Rows:** 17 (due to missing critical fields)

---

## 📁 Output

- 📂 **Cleaned File**: [`netflix_titles_cleaned.csv`](./netflix_titles_cleaned.csv)  
- 💻 **Code File**: `data_cleaning_netflix.ipynb` (or `.py`)  
- 🖼️ **Screenshots**: *(Optional: null counts, before/after views)*

---
