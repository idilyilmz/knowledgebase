# (1) JOINs and UNIONs
https://www.kaggle.com/code/alexisbcook/joins-and-unions

## Introduction
You already know how to use **INNER JOIN** to combine data from two tables. This lesson introduces additional JOIN types (LEFT, RIGHT, FULL) and shows how **UNION** can vertically combine results from multiple tables.
You’ll work with two example tables: **owners** and **pets**.

## JOINs
- **INNER JOIN** returns only rows where both tables share a matching key.
    - Example: matching `owners.Pet_ID` to `pets.ID`.
    - Non-matching rows (e.g., owners without pets or pets without owners) are excluded.
- **LEFT JOIN** returns:
    - All matching rows, **plus all rows from the left table**, even if they have no match.
    - Missing matches from the right table appear as **NULL**.
- **RIGHT JOIN** returns:
    - All matching rows, **plus all rows from the right table**, even if unmatched.
- **FULL JOIN** returns:
    - **All rows from both tables**, filling in NULLs wherever a match doesn’t exist.

These JOIN types allow you to gather complete or partial information depending on your goal.

## UNIONs
- JOINs combine tables **horizontally**.
- **UNION** combines tables **vertically**, stacking rows on top of each other.
- Requirements:
    - The columns must have the **same data type**.
    - Column names do **not** need to match.
- **UNION ALL** keeps duplicates.
- **UNION DISTINCT** removes duplicates.

## Example
Working with the **Hacker News** dataset:

### JOIN Example

A query uses a **CTE + LEFT JOIN** to list all stories posted on **Jan 1, 2012** along with their number of comments:

- The CTE counts comments per story.
- LEFT JOIN ensures stories with **zero comments** still appear (their comment count is NULL).
- Results are ordered by number of comments.

### UNION Example

A second query finds all **unique users** who posted either stories or comments on **Jan 1, 2014**:
- It uses two SELECT queries combined with **UNION DISTINCT**.
- Each user appears only once.
- The final result contains **2282 unique users**.
