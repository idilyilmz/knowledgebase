# (1) Creating, Reading and Writing

https://www.kaggle.com/code/residentmario/creating-reading-and-writing

## 1. Introduction
This micro-course introduces **pandas**, the most widely used Python library for data analysis.
You’ll learn how to **create your own data** and **work with existing datasets**, using hands-on, real-world examples.

## 2. Getting started
To begin using pandas, import it with the standard convention:
```
import pandas as pd
```
## 3. Creating data
Pandas has two core data structures:

## a. DataFrame
- A **table** of data organized into rows and columns.
- Created using `pd.DataFrame()` with a dictionary:
    - Keys → column names
    - Values → lists of column entries
- Rows are labeled by an **Index**, which defaults to numbers but can be customized.

**Key idea**: A DataFrame is ideal for structured, tabular data.

## b. Series
- A **one-dimensional list** of values.
- Created using `pd.Series()`.
- Has:
    - An index (row labels)
    - A single name (but no column labels)

**Relationship**: A DataFrame is essentially multiple Series combined together.

## 4. Reading data files
Most real-world data comes from files rather than being created by hand.

### a. CSV Files
- CSV (Comma-Separated Values) files store tabular data.
- Read into pandas using:
```
pd.read_csv()
```
### b. Exploring Imported Data
- `.shape` shows the size of the DataFrame (rows, columns).
- `.head()` displays the first few rows.
- Optional parameters (like `index_col`) let you customize how data is read, such as setting an existing column as the index.

**Benefit**: Pandas makes it easy to load, inspect, and work with large datasets efficiently.

## 5. Key takeaways
- `DataFrame` = table, `Series` = single column
- Indexes label rows and can be customized
- `pd.read_csv()` is essential for loading real datasets
- Pandas scales easily from small examples to large, real-world data