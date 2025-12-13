# (2) Indexing, Selecting & Assigning

https://www.kaggle.com/code/residentmario/indexing-selecting-assigning

## 1. Introduction
Selecting and modifying subsets of data is fundamental to almost every pandas operation. This lesson introduces the main ways to **access**, **filter**, and **assign data** in pandas efficiently.

## 2. Native accessors
Pandas supports familiar Python-style access:
- Attribute access:
```
reviews.country
```
- Indexing operator (preferred):
```
reviews['country']
```

-Both return a Series, but [] is more flexible (handles special column names).

You can drill down to a single value by chaining indexing:
```
reviews['country'][0]
```
## 3. Indexing in pandas

### a. Index-based selection (`iloc`)
- Uses **numerical positions**, ignoring labels.
- Syntax: `df.iloc[row, column]`
- Supports slicing, lists, and negative indices.

Examples:
- First row: `df.iloc[0]`
- First column: `df.iloc[:, 0]`
- Subset of rows: `df.iloc[1:3, 0]`
- Last rows: `df.iloc[-5:]`

### b. Label-based selection (loc)
- Uses index labels, not positions.
- Syntax: df.loc[row_label, column_label]
- Easier when indices are meaningful.

Example:
```
df.loc[:, ['taster_name', 'points']]
```
Important difference
- `iloc`: end index excluded
- `loc`: end index included

## 4. Manipulating the index
Indexes are mutable and can be changed to improve usability.
- `set_index()` replaces the current index with another column:
```
reviews.set_index('title')
```
This makes label-based selection more intuitive.
## 5. Conditional selection
You can filter rows using boolean conditions.

### a. Basic conditions
```
reviews.loc[reviews.country == 'Italy']
```

### b. Multiple conditions
- AND: `&`
- OR: `|`

```
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
```
### c. Built-in helpers
- `isin()` → match against a list of values
- `isnull()` / `notnull()` → handle missing values (NaN)

## 6. Assigning data
Adding or modifying columns is straightforward.
- Assign a constant:
```
reviews['critic'] = 'everyone'
```
- Assign a sequence:
```
reviews['index_backwards'] = range(len(reviews), 0, -1)
```
## 7. key takeaways 
- Use `[]` or attribute access for simple column selection
- Prefer `loc` and `iloc` for advanced indexing
- `iloc` = position-based, `loc` = label-based
- Boolean filtering enables powerful data selection
- Assigning new columns is fast and flexible