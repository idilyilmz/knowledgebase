# (4) Order By
https://www.kaggle.com/code/dansbecker/order-by

## 1. Introduction
You’ve learned how to filter rows (**WHERE**), select specific columns (**SELECT**), and aggregate data (**COUNT**, **GROUP BY**). This section introduces how to sort query results with ORDER BY, including sorting dates.

## 2. ORDER BY
- **ORDER BY** is typically the last clause in a SQL query.
- It sorts your result set by one or more columns.
- Works on numbers, text (alphabetical order), and dates.
- Add **DESC** to reverse the sort (descending order instead of ascending).

## 3. Dates
- BigQuery stores dates as **DATE** (YYYY-MM-DD) or **DATETIME** (includes time).
- DATE example: `2019-01-10` → January 10, 2019.
- DATETIME includes both date and time in one field.

## 4. EXTRACT
- **EXTRACT** retrieves specific parts of a date or datetime (e.g., year, day, week).
- Useful for analyzing trends by day, week, month, etc.
- Example: `EXTRACT(DAY FROM date_column)` returns the day of the month.

## 5. Example: Which day of the week has the most fatal motor accidents?
- Dataset: US Traffic Fatality Records (`accident_2015` table).
- Approach:
   - Use **EXTRACT(DAYOFWEEK FROM `timestamp_of_crash`**) to get the weekday (1 = Sunday, 7 = Saturday).
   - **COUNT(`consecutive_number`)** counts accidents per day.
   - **GROUP BY** the extracted weekday.
   - **ORDER BY `num_accidents` DESC** shows days with the most accidents first.
- Result:
   - Highest accidents occurred on **Sunday (7)** and **Saturday (1)**.
   - Lowest on **Tuesday (3)**.