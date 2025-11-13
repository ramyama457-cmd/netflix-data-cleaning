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

## How to Run
```bash
python data_cleaning.py

  
