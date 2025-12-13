# (3) Summary, Functiosn and Maps

https://www.kaggle.com/code/residentmario/summary-functions-and-maps

## 1. Introduction
After learning how to select data, this tutorial focuses on **transforming and summarizing data** so it’s in the right format for analysis.

## 2. Summary functions
Pandas provides built-in functions to quickly understand your data:

- `describe()`
    Gives a high-level statistical summary.
    - Numeric data: count, mean, std, min/max, quartiles
    - Categorical data: count, unique values, most frequent value
- **Common summary methods**:
    - `mean()` → average value
    - `unique()` → list of unique values
    - `value_counts()` → frequency of each unique value

These functions are type-aware and adapt to the data being analyzed.

## 3. Maps (Transforming Data)
Maps are used to **transform existing data into new values**.

`map()`
- Works on a **Series**
- Applies a function to **each individual value**
- Returns a new Series
- Example use: re-centering scores around the mean

`apply()`
- Works on a **DataFrame**
- Applies a function to **each row or column**
- `axis='columns'` → row-wise
- `axis='index'` → column-wise
- More flexible, but slower than built-in operations

Neither `map()` nor `apply()` modifies the original data unless you assign the result back.

## 4. Vectorized Operations (Preferred When Possible)
Pandas supports fast, element-wise operations:
- Arithmetic with scalars:
    - `reviews.points - reviews.points.mean()`
- Operations between Series of equal length:
    - `reviews.country + " - " + reviews.region_1`
- Logical comparisons (`>`, `<`, `==`, etc.)

These are faster and more efficient than `map()` or `apply()`.

## 5. Key Takeaways
- Use **summary functions** to quickly understand your data.
- Use **vectorized operations** whenever possible for speed.
- Use `map()` for simple value-by-value transformations.
- Use `apply()` for more complex, row- or column-level logic.