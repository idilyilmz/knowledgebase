# (3) Categorical Variables

https://www.kaggle.com/code/alexisbcook/categorical-variables

## 1. Introduction
- **categorical variables** on a limited set of values (like, colors, brands, survey responses)
- most machine learning models cannot work with categorical data directly and require preprocessing
- this lesson compares **three common approaches** for handling categorical variables before modeling

## 2. Three Approaches 

### a. drop categorical variables
- remove all categorical columns from the dataset
- simple, but often discards valuable information
- works only if categorical features are not informative

### b. ordinal encoding
- assigns each category a unique integer
- assumes an **ordering** among categories
- works well for **ordinal variables** and tree-based models (like, decision trees, random forests)
- not ideal for categories without a natural ranking

### c. one-hot encoding
- creates a new binary column for each category
- does **not assume ordering**, making it ideal for **nominal variables**
- commonly performs well, but can be inefficient for features with many unique values

## 3. Example
- applied to the **Melbourne Housing dataset** using a random foretc model
- categorical variables were identified by `object` data types
- model performance was evaluated using **Mean Absolute Error (MAE)**
- results
    - dropping categorical variables performed the worst
    - ordinal and one-hot encoding performed similarity in this case

## 4. Which approach is the best
- **Dropping categorical variables** usually performs worst
- **One-hot encoding** generally performs best, especially for nominal variables
- **Ordinal encoding** is effective when categories have a meaningful order
- Best choice depends on the dataset and the nature of the categorical features

## 5. Conclusion
- categorical data is extremely common in real-world datasets
- choosing the right encoding method can significantly improve model performance
- understanding when to use ordinal vs. one-hot encoding is a key machine learning skill