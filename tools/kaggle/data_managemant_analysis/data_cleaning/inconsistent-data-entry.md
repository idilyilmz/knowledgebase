# (5) Inconsistent Data Entry

https://www.kaggle.com/code/alexisbcook/inconsistent-data-entry

## 1. Get our environment set up
- import libraries
    - `pandas`, `numpy` for data handling
    - `fuzzywuzzy` for fuzzy string matching
    - `charset_normalizer` (used in earlier text-cleaning steps)
- load a dataset containing professor information
- set a random seed for reproducibility

## 2. Do some preliminary text pre-processing
- inspect the dataset using `head()`
- focus on a text column with inconsistencies (like, **country**)
- identify issues by checking unique values with `.unique()`
    - incositent capitalization (`Germany` vs `germany`)
    - leading/training spaces (` " New Zealand" `)
    - slight spelling variations

### a. Basic cleaning steps
- convert text to lowercase
```
df[column] = df[column].str.lower()
```
- remove leading and trailing whitespace
```
df[column] = df[column].str.strip()
```
- these two steps alond can fix **most text incosistencies**

## 3. Use fuzzy matching to correct incosistent data entry
- some incosistencies remain after basic cleaning (like, `southkorea` vs `south korea`)
- **Fuzzy matching** finds strings that are similar based on edit distance.
- FuzzyWuzzy returns a similarity score (0-100):
    - higher score → more similar strings

### a. Workflow
1. choose a correct reference string (like, `"south korea"`)
2. use fuzzy matching to find similar values.
3. replace values with simialrity above a chosen threshold

### b. Automation
- write a reusable function to:
    - identify close matches
    - replace them with a standard value
- this approach scales well for large datasets and reduces manual work

## 4. Key takeaways
- text data often contains hidden inconsistencies
- start with simple fixes (lowercase + trim)
- use **fuzzy matching** for harder cases
- automating text cleaning saves time and prevents errors