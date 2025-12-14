# (5) As & With
https://www.kaggle.com/code/dansbecker/as-with

## 1. Introduction
As SQL queries grow longer, they become harder to read and debug. This section shows how **AS** and **WITH** can simplify and organize your queries using aliases and common table expressions (CTEs).

## 2. AS
- **AS** renames (aliases) columns in your SELECT statements.
- This makes results clearer, for example, renaming a `COUNT()` output from an unreadable default label to something meaningful.
- Aliasing works similarly to Python’s `import pandas as pd`.

## 3. WITH ... AS
- **WITH ... AS** creates a **common table expression (CTE)**, a temporary, named table defined at the start of a query.
- CTEs help break complex queries into readable sections.
- They only exist for the duration of the query.
- Example: Create a CTE called `Seniors` containing only pets older than 5, then query from that CTE.

## 4. Example: How many Bitcoin transactions are made per month?
- Using the Bitcoin `transactions` table, a CTE converts `block_timestamp`(DATETIME) into a DATE field.
- The main query then groups by date, counts the number of transactions per day, and sorts results by earliest date first.
- This shows how CTEs help clean and prepare data directly in SQL, useful in BigQuery where SQL operations are faster than using Pandas.