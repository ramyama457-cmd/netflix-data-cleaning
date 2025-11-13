# 🎬 Netflix Data Cleaning Project

## 📄 Project Overview
This project focuses on cleaning and preparing the *Netflix Titles Dataset* for further data analysis or visualization.  
The dataset contains information about movies and TV shows available on Netflix, including their cast, country, director, release year, and more.

---

## 🧹 Objectives
The main goal of this task is to clean the raw dataset by:
- Handling missing values
- Removing duplicate entries
- Correcting inconsistent data types
- Saving a cleaned version of the dataset for analysis

---

## 🧠 Steps Performed
1. *Loaded the Dataset*  
   Imported the raw Netflix dataset (netflix_titles.csv) using pandas.

2. *Checked for Missing Values*  
   Identified columns with missing data such as director, cast, and country.

3. *Handled Missing Values*  
   - Filled missing categorical fields with 'Unknown' or mode values.  
   - Dropped unnecessary empty rows if required.  

4. *Removed Duplicates*  
   Ensured unique entries using drop_duplicates().

5. *Verified Data Types*  
   Checked and corrected data types for columns such as date_added and release_year.

6. *Exported the Clean Dataset*  
   Saved the cleaned dataset as fully_cleaned_netflix_titles.csv.

---

## 🧰 Tools & Libraries Used
- *Python 3.x*
- *Pandas*
- *NumPy*
- *Jupyter Notebook / VS Code*

---
## Source code
import pandas as pd

# 1️⃣ Load the dataset
df = pd.read_csv("netflix_titles.csv")

# 2️⃣ Identify missing values
print("Missing values before cleaning:\n", df.isnull().sum())

# 3️⃣ Handle missing values
df.fillna({
    'director': 'Unknown',
    'cast': 'Not available',
    'country': 'Unknown',
    'rating': df['rating'].mode()[0],
    'duration': '0 min',
    'date_added': 'Unknown'
}, inplace=True)

# 4️⃣ Remove duplicate rows
df.drop_duplicates(inplace=True)

# 5️⃣ Standardize text values (example)
# Convert text columns to lowercase and strip spaces
text_columns = ['type', 'country', 'rating']
for col in text_columns:
    df[col] = df[col].astype(str).str.strip().str.lower()

# Example: Standardize country names
df['country'] = df['country'].replace({
    'united states': 'usa',
    'united kingdom': 'uk',
    'south korea': 'korea'
})



# Convert and clean 'date_added'
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
df['date_added'] = df['date_added'].dt.strftime('%d-%m-%Y')
df['date_added'] = df['date_added'].fillna('Unknown')


# 7️⃣ Rename columns to be uniform (lowercase, no spaces)
df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')

# 8️⃣ Check and fix data types
# Example: ensure release_year is int
df['release_year'] = df['release_year'].astype(int)

# 9️⃣ Save cleaned dataset
df.to_csv("fully_cleaned_netflix_titles.csv", index=False)

print("\n✅ Data cleaning complete! Saved as 'fully_cleaned_netflix_titles.csv'")
print("\nMissing values after cleaning:\n", df.isnull().sum())
print("\nData types:\n", df.dtypes)

## How to Run
```bash
python data_cleaning.py

##output
Missing values before cleaning:
 show_id            0
type               0
title              0
director        2634
cast             825
country          831
date_added        10
release_year       0
rating             4
duration           3
listed_in          0
description        0
dtype: int64

✅ Data cleaning complete! Saved as 'fully_cleaned_netflix_titles.csv'

Missing values after cleaning:
 show_id         0
type            0
title           0
director        0
cast            0
country         0
date_added      0
release_year    0
rating          0
duration        0
listed_in       0
description     0
dtype: int64

Data types:
 show_id         object
type            object
title           object
director        object
cast            object
country         object
date_added      object
release_year     int64
rating          object
duration        object
listed_in       object
description     object
dtype: object  
