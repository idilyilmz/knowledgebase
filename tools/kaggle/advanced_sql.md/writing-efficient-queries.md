# (4) Writing Efficient Queries

https://www.kaggle.com/code/alexisbcook/writing-efficient-queries

## 1. Introduction
Query efficiency matters when:
- Queries run **frequently** (powering a website)
- Datasets are **very large**
- Poor queries increase **latency and cost**

Although databases have optimizers, **how you write queries still has a major impact** on performance and cost in BigQuery.

## 2. Some useful functions
Two helper functions are used to measure efficiency:
- `show_amount_of_data_scanned()` – shows how much data a query reads
- `show_time_to_run()` – measures query execution time

These help compare different query approaches.

## 3. Strategies

### a. Only select the columns you need
Avoid `SELECT *`.
- Selecting unnecessary columns (especially large text fields) greatly increases data scanned.
- Explicitly choosing columns can reduce scanned data by **orders of magnitude**.

**Key idea**: Less data read = faster and cheaper queries.

### b. Read less data
Use columns that minimize data access.
- Avoid redundant columns when there is a **1:1 relationship** between fields.
- Filter and group using only what’s necessary.
**Result**: Lower data scanned with identical results.

### c. Avoid N:N (Many-to-Many) JOINs
JOIN types:
- **1:1 JOIN** – most efficient
- **N:1 JOIN** – manageable
- **N:N JOIN** – expensive and slow (explodes row counts)

**Optimization strategy**:
- Aggregate data before joining
- Reduce table sizes using CTEs
- Join smaller, summarized tables instead of raw data

**Outcome**: Dramatically faster execution times.

## 4. Learn more
BigQuery performance can be improved using many additional techniques.
For deeper optimization strategies and best practices, consult the **Google BigQuery efficiency guide** linked in the tutorial.

## 5. Key Takeaways
- Avoid SELECT *
- Minimize scanned data
- Reduce JOIN sizes
- Optimize queries to save time, cost, and resources