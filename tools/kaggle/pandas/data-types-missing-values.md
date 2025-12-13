# (5) Data Types and Missing Values

https://www.kaggle.com/code/residentmario/data-types-and-missing-values

## 1. Introduction
This tutorial explains how to:
- Inspect and change **data types (dtypes)** in pandas
- Detect, replace, and handle **missing data (NaN)**

## 2. dtypes (data types)
- Every pandas **Series and DataFrame column** has a dtype that defines how data is stored.
- Use:
    - `series.dtype` → dtype of one column
    - `df.dtypes` → dtypes of all columns

#### Common dtypes:
- `int64` → integers
- `float64` → decimals (and all NaN values)
- `object` → strings (pandas does not have a dedicated string dtype by default)

#### Type conversion:
- Use `astype()` to convert a column to another compatible type.
- Indexes also have their own dtype (`df.index.dtype`).

## 3. Missing data (NaN)
- Missing values are represented as **NaN** (“Not a Number”).
- NaN values are always stored as `float64`.

#### Detecting missing data:
- `pd.isnull()` → select missing values
- `pd.notnull()` → select non-missing values

## 4. Replacing missing data
`fillna()`
- Replaces NaN values using different strategies:
    - Constant value (`"Unknown"`)
    - Forward fill or backward fill (using nearby non-null values)

`replace()`
- Replaces specific existing values (not just NaN)
- Useful for cleaning placeholder values like `"Unknown"` or outdated entries

## 5. Key Takeaways
- Always check dtypes before analysis, storage affects behavior.
- Strings are stored as `object` dtype.
- NaN values require special handling.
- Use `fillna()` for missing values and `replace()` for cleaning incorrect or placeholder data.