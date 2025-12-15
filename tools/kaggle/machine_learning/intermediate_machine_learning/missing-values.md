# (2) Missing Values

https://www.kaggle.com/code/alexisbcook/missing-values

## 1. Introduction
- real-worls datasets often contain **missing values** (like, unreported features or inapplicable measurements)
- most machine learning models cannot handle missing values directly, so they must be adressed before training
- this lesson compares **three strategies** for handling missing data and evaluates their impact on model performance

## 2. Three Approaches

### a. Drop Columns with Missing Values
- remove any olumn that contains missing data
- simple but risky: can discard large amounts of useful information
- often performs poorly unless most values in those columns are missing

### b. Imputation
- replace missing values with a statistic such as the **mean** of the column
- preserves all features and usually leads to **better model accuracy** than dropping columns
- simple mean imputation often works surprisingly well with modern ML models

### c. Imputation with Missing-Value Indicators
- perform imputation as in Approach 2
- add new binary features indicating whether a value was originally missing
- can help if missingness itself carries information, but doesn't always improve performance

## 3. Example
- tested on the **Melbourne Housing dataset** using a random forets model
- model performance was evaluated using **Mean Absolute Error (MAE)**
- results
    - dropping columns performed the worst
    - mean imputation performed best
    - adding missing-value indicators did not improve results in this case

## 4. Conclusion
- **Imputation** is generally superior to dropping columns when missing values are limited
- adding indicators for missing values may help in some datasets, but not always
- continue summarizing the next lesson so all your notes stay consistent