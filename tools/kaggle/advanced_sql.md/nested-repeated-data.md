# (3) Nested and Repeated Data

https://www.kaggle.com/code/alexisbcook/nested-and-repeated-data

## 1. Introduction
**BigQuery** supports **nested** and **repeated** data types, which allow complex, hierarchical data to be stored efficiently in a single table. These structures help avoid costly joins and improve query performance.

## 2. Nested data
**Nested data** stores related fields inside a single column using the **STRUCT (RECORD)** data type.
- A nested column contains multiple named fields.
- Fields are accessed using dot notation (e.g., `Toy.Name`, `device.browser`).
- Queries work the same as usual, only field references change.

**Benefit**: Keeps related data together and reduces the need for joins.

## 3. Repeated data
**Repeated data** allows a column to contain **multiple values per row**, stored as an **ARRAY**.

- The column’s schema mode is `REPEATED`.
- Each entry is an ordered list of values.
- To query repeated fields, you must use `UNNEST()` to flatten the array into rows.

**Example**: A pet having multiple toys or a website session having multiple hits.

## 4. Nested and repeated data
A column can be **both nested and repeated**, an array of STRUCTs.
- Each element in the array is a STRUCT with multiple fields.
- Use `UNNEST()` to flatten the array.
- Assign an alias to reference nested fields clearly (e.g., `t.Name`, `hits.page.pagePath`).

This is common in real-world datasets like analytics logs.

## 5. Example
### E1: Nested-only fields
Using the Google Analytics dataset:
- `device` and `totals` are STRUCTs.
- Fields are accessed with dot notation (e.g., `device.browser`, `totals.transactions`).
- Aggregations can be performed directly without joins.

**Result**: Fast queries and simpler SQL.

### E2: Nested and repeated fields

The `hits` column:
- Is a repeated STRUCT.
- Contains nested fields like `hitNumber`, `type`, and `page.pagePath`.

Steps:
1. Use `UNNEST(hits)` to flatten the repeated data.
2. Filter to landing page hits (`hitNumber = 1`, `type = 'PAGE'`).
3. Aggregate results.

**Result**: Identifies the most common landing pages (`/home`).

## 6. Key takeaways
- **STRUCT = nested data**
- **ARRAY = repeated data**
- **UNNEST() = flatten repeated data**
- Nested + repeated data enabled efficient, join-free analytics in BigQuery.