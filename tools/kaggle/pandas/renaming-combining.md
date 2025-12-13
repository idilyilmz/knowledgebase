# (6) Renaming and Combining

https://www.kaggle.com/code/residentmario/renaming-and-combining

## 1. Introduction
This tutorial covers:
- **Renaming** columns, index values, and axis labels to make data clearer.
- **Combining** multiple Dataframes or Series into one dataset

## 2. Renaming
`rename()`
- used to rename **columns** or **index values**
- commonly applied to columns
- accepts a dictionary mapping old names → new names

Examples:
- rename a column (`points` → `score`)
- rename specific index entries

Renaming index values is rare; `set_index()` is usually more practical.

## 3. Combining
pandas provides three main combining tools (from simple to complex):
1. `concat()`
2. `join()`
3. `merge()` (not covered)

### a. `concat()`
- stacks DataFrames **along rows or columns**
- best when DataFrames share the same columns
- common use case: combining datasets split by country, time, or source.

### b. `join()`
- combines DataFrames using a **shared index**
- similar to SQL joins
- handles overlapping column names using suffixes (`lsuffix`, `rsuffix`)

use case:
- matching records from different datasets based on common index values

## 4. Key takeaways
- use `rename()` to clean up column and index names
- use `rename_axis()` to label rows and columns
- use `concat()` to stack similar datasets.
- use `join()` when datasets share an index and need to be matched
- choose the simplest combining method that gets the job done
