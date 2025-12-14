# (4) Grouping and Sorting

https://www.kaggle.com/code/residentmario/grouping-and-sorting

## 1. Introduction
While maps transform data **value by value**, many analyses require working with **groups of data**. Pandas provides the `groupby()` operation for group-level analysis, along with tools for handling multi-indexes and sorting results.

## 2. Groupwise analysis (`groupby`)
- `groupby()` splits data into groups based on one or more columns.
- You can then apply **summary functions** (count, min, max, mean, etc.) to each group.

**Key ideas**:
- `value_counts()` is a shortcut for a `groupby()` + `count()`.
- Grouped data behaves like a smaller DataFrame per group.

**Examples of common uses**:
- Count wines by score
- Find the cheapest wine per score
- Select a specific row from each group using `apply()`
- Group by multiple columns (country + province)

`agg()`
- Allows running multiple summary functions at once:
    - Example: count, min price, and max price per country

## 3. Multi-indexes
- Grouping by multiple columns often produces a **MultiIndex** (hierarchical index).
- A MultiIndex has multiple levels (e.g., country → province).
- Accessing data requires multiple index labels.

Important tool:
- `reset_index()` flattens a MultiIndex back into normal columns
(often used after `groupby()`).

## 4. Sorting
Grouping does not sort by values automatically—results are ordered by index.

**Sorting methods**:
- `sort_values()` → sort by column values
    - Default: ascending
    - Use `ascending=False` for descending order
- `sort_index()` → sort by index values
- Sort by multiple columns by passing a list to `by=[...]`

## 5. Key Takeaways
- Use `groupby()` for powerful, group-level analysis.
- Use `apply()` for custom group logic; use `agg()` for multiple summaries.
- Expect MultiIndexes when grouping by multiple columns, use `reset_index()` to simplify.
- Always sort explicitly if order matters.