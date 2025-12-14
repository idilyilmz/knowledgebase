# (1) Handling Missing Values

https://www.kaggle.com/code/alexisbcook/handling-missing-values

## 1. Take a first look at the data
- always inspect a new dataset first using functions like `head()`
- missing values appear as **NaN** or **None**
- early inspection helps confirm the data loaded correctly and reveals obvious issues.

## 2. How many missing data points do we have?
- use `isnull().sum()` to count missing values per column
- calculate the **percentage of missing data** to understand the scale of the problem
- in the NFL dataset, **~25% of all cells were missing**, which is significant

## 3. Figure out why the data is missing
- use **data intuition** to understand missing values
- ask: **is the value missing because it wasn't recorded, or because it doesn't exist?**
    - *doesn't exist*: Leave as NaN (for example, penalized team when no penalty occurred)
    - *wasn't recorded*: Consider estimating it using other data (imputation)
- dataset documentation is very helpful at this stage.

## 4. Drop missing values
- optionally remove missing data using `dropna()`
    - dropping rows can remove **all data** if every row has at least one missing value
    - dropping columns removes all columns that contain any missing values
- this approach is **quick but risky** because it can discard large amounts of useful data
- in the example, columns dropped from **102** → **41**

## 5. Filling in missing values automatically
- use `fillna()` to replace missing values
- common strategies
    - replace NaN with a fixed value (`0`)
    - use forward or backward filling (`ffill`, `bfill`) when data has a logical order
- these methods are fast but may introduce **noise or bias**, so use with caution.

## 6. Key takeaways
Handling missing values is a balance between **speed and accuracy**. Understanding *why* data is missing leads to better decisions than blindly dropping or filling values.