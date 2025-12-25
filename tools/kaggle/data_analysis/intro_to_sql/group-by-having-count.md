# (3) Group By, Having & Count

https://www.kaggle.com/code/dansbecker/group-by-having-count

## 1. Introduction
- learn how to group data and count things within groups using `GROUP BY`, `HAVING`, and `COUNT()`
- this helps answer questions like sales per fruit or animals treated per species.

## 2. COUNT()
- Returns the number of entries in a column or rows (e.g., `COUNT(ID)`).
- Example of an aggregate function; others include `SUM()`, `AVG()`, `MIN()`, `MAX()`.
- Aggregate functions may produce default column names like `f0__`.

## 3. GROUP BY
- Groups rows with the same value in one or more columns.
- Used with aggregate functions to summarize data by groups.
- Example: Count animals per type in a pets table.

## 4. GROUP BY ... HAVING
- `HAVING` filters groups based on conditions (like `COUNT() > 1`).
- Returns only groups meeting the specified criteria.

## 5. Example: Which Hacker News comments generated the most discussion?
- Dataset: `hacker_news.full`.
- Use `GROUP BY parent` and `COUNT(id)` to find comments with many replies.
- Use `HAVING COUNT(id) > 10` to return only popular comments.
- Results can be stored in a pandas DataFrame for further analysis.

## 6. Alisasing and other improvements
- Use `AS` to give descriptive names to aggregated columns (e.g., `COUNT(1) AS NumPosts`).
- `COUNT(1)` counts rows efficiently without scanning unnecessary columns.
- Improves readability and reduces data usage.

## 7. Note on using GROUP BY
- Columns in a `GROUP BY` query must either be grouped or aggregated.
- Including non-aggregated, non-grouped columns (like `by`) causes errors.
- Use backticks for reserved keywords and aliases for readability.