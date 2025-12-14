# (2) Analytic Functions

https://www.kaggle.com/code/alexisbcook/analytic-functions/tutorial

## 1. Introduction
**Analytic Functions** are functions that allow you to perform complex calculations with relativity straightforward syntax.

They perform 
- calculations **across sets of rows**, similar to aggregate functions
- **but return a value for every row** instead of collapsing rows into one.

They are useful for tasks like **moving averages, running totals, ranking**, and more.
## 2. Syntax

Analytic functions use an **OVER** clause to define *how* the calculation is applied.
The OVER clause can include three optional parts:

1. **PARTITION BY** – divides rows into groups.
2. **ORDER BY** – sets order within each partition.
3. **Window frame clause** (e.g., `ROWS BETWEEN ...`) – defines which rows around the current row are used in the calculation.

Example: computing a moving average for each runner uses:

- `PARTITION BY id`
- `ORDER BY date`
- `ROWS BETWEEN 1 PRECEDING AND CURRENT ROW`

## 3. (More on) window frame clauses
The window frame defines *which* surrounding rows are included.

Common examples:
- `ROWS BETWEEN 1 PRECEDING AND CURRENT ROW` → previous row + current row
- `ROWS BETWEEN 3 PRECEDING AND 1 FOLLOWING` → wider moving window
- `ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING` → entire partition

(Window frames allow moving averages, cumulative calculations, etc.)

## 4. Three types of analyic functions

### a. Analytic aggregate functions
These apply aggregate functions over the window:

- `MIN()`, `MAX()`
- `AVG()`, `SUM()`
- `COUNT()`

Example use: cumulative sums, rolling averages.

### b. Analytic navigation functions
These return values from other rows within the window:

- `FIRST_VALUE()` / `LAST_VALUE()`
- `LEAD()` / `LAG()`

Example use: compare current row to previous row, find first/last station, etc.

### c. Analytic numbering functions
These assign numbers based on row order:
- `ROW_NUMBER()`
- `RANK()`

Used for ranking, de-duplication, etc.

## 5. Example

### E1: Cumulative trips per day (2015)
- A CTE calculates daily trip counts.
- `SUM(num_trips) OVER (ORDER BY trip_date)` computes the cumulative total.
- No `PARTITION BY`, so all rows form one partition.
- Window frame: from the start to the current row.

### E2: First and last station per bike (on a specific date)
- Uses `FIRST_VALUE()` and `LAST_VALUE()`.
- Partitioned by `bike_number` so each bike’s trips are grouped.
- Ordered by `start_date` to track a bike’s trip sequence.
- Window frame includes the entire partition, so every row shows the same first/last station for that bike.