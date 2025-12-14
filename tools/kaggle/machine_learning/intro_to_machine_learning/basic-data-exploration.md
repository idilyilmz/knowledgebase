# (2) Basic Data Exploration

https://www.kaggle.com/code/dansbecker/basic-data-exploration

## 1. Using Pandas to Get Familiar With Your Data
- the first step in any machine learning project is **exploring and understanding the data**
- **Pandas** is the main Python library used for data exploration and manipulation, commonly imported as `pd`.
- the core Pandas structure is the **DataFrame**, which represents data in a table-like format similar to Excel or SQL tables.
- data is typically loaded from a CSV file using `pd.read_csv()`
- the `.describe()` method provides a quick statistical summary of numerical columns
- example datasets include housing data from Melbourne (for demonstration) and Iowa (for practice)

## 2. Interpreting Data Description
- the `.describe()` output shows ket statistics for each numeric column:
    - **count**: number of non-missing values
    - **mean**: average value
    - **std**: standard deviation, showing data spread
    - **min** and **max**: smallest and largest values
    - **25%**, **50%**, **75%**: precentiles indicating how data is disturbed
- percentiles help understand the range and central tendency of data
- missing values are common in real datasets and occur for practical reasons
- understanding these statistics helps identify patterns, outliers and data quality issues.