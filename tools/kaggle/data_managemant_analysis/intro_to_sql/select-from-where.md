# (2) Select, From & Where

https://www.kaggle.com/code/dansbecker/select-from-where

## 1. Introduction
Now that you can access datasets, you’re ready to write SQL queries. SQL lets you filter and retrieve only the data you need. This lesson covers basic keywords: `SELECT`, `FROM`, and `WHERE`.

## 2. SELECT ... FROM
- Basic queries select specific columns from a table.
- Syntax: `SELECT column_name FROM table_name`.
- Use backticks (`) around table names in BigQuery.

## 3. WHERE ...
- The `WHERE` clause filters rows based on conditions.
- Example: Select names where `Animal = 'Cat'`.

## 4. Example: What are all the U.S. cities ...
- Dataset: `global_air_quality` table in OpenAQ.
- Query example: Select all `city` entries where `country = 'US'`.
- Result can be converted into a pandas DataFrame for analysis.
- Example output: Top cities with the most measurements include - Phoenix, Los Angeles, and New York.

## 5. Submitting the query to the dataset
- Create a BigQuery `Client` object.
- Use `client.query()` to run queries and convert results to a DataFrame.

## 6. More queries
- Select multiple columns: `SELECT city, country`.
- Select all columns: `SELECT *`.

## 7. Q&A: Notes from formatting
- Triple quotes `""" """` allow multi-line strings in Python.
- SQL commands do not require capitalization, but it’s customary.

## 8. Working with big datasets
- Kaggle free tier: 5TB per 30 days.
- Use `QueryJobConfig(dry_run=True)` to estimate query size without running it.
- Use `maximum_bytes_billed` to prevent exceeding limits.
- Example: Limiting query to 1 MB may cancel it; increasing to 1 GB allows the query to run successfully.
- Calculations like average scores can then be performed on the results.