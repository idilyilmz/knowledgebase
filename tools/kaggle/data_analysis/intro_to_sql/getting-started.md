# (1) Getting Started With SQL and BigQuery

https://www.kaggle.com/code/dansbecker/getting-started-with-sql-and-bigquery

## Introduction
SQL (Structured Query Language) is essential for working with databases. This course teaches SQL using BigQuery, a web service for querying large datasets. The lesson focuses on accessing and examining BigQuery datasets before advancing to SQL queries.

## Your first BigQuery commands
- Import the BigQuery Python package and create a `Client` object to interact with datasets.
- Example dataset: `hacker_news` in the `bigquery-public-data` project.
- Steps to access data:
   1. Construct a dataset reference with `dataset()`.
   2. Fetch the dataset using `get_dataset()`.
   3. List tables with `list_tables()`.
   4. Fetch individual tables using `get_table()`.

## Table schema
- Tables have a schema describing columns (name, type, mode, description).
- Example columns in the `full` table include `title`, `url`, `text`, `by`, `score`, `time`, `type`, `id`, etc.
- Use `list_rows()` to preview table data or specific columns.

## Disclaimer
- Kaggle allows scanning 5TB every 30 days for free.
- Initial commands are lightweight, but large queries may hit limits.