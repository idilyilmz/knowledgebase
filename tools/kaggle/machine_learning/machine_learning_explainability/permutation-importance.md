# (2) Permutation Importance

https://www.kaggle.com/code/dansbecker/permutation-importance

## 1. Introduction
- a key question in model interpretation is identifying which features have the greatest impact on predictions
- This concept is known as **feature importance**
- There are multiple ways to measure feature importance, each answering slightly different questions and having different limitations
- this lesson focuses on **permutation importance**, which is:
    - fast to compute
    - widely used and well understood
    - aligned with desirable properties of feature importance

## 2. How It Works
- permutation importance is calculated after a model is trained and does not change the model itself
- the core idea is:
    - randomly shuffle the values of one feature in the validation dataset
    - measure how much the model’s prediction performance decreases
    - a larger drop in performance indicates a more important feature
- shuffling an important feature breaks meaningful relationships in the data and significantly harms accuracy, while shuffling an unimportant feature has little effect

**Steps**:
1. train a model
2. shuffle one feature column in the validation data
3. measure the change in model performance (loss or accuracy)
4. restore the column and repeat for each feature
5. rank features by how much performance deteriorates

## 3. Code Example (Soccer Dataset)
- a random forest model predicts whether a team has a *Man of the Match* winner based on match statistics
- permutation importance is computed using the **eli5** library
- features such as *Goals Scored* show the largest impact on accuracy, indicating high importance

## 4. Interpreting Permutation Importances
- features at the top are most important; those at the bottom contribute least
- the main value shows the average drop in performance after shuffling
- the ± value represents variability across multiple shuffles
- negative values may appear due to randomness, especially in small datasets, and usually indicate features with little real importance

## 5. Key takeways
permutation importance provides an intuitive and reliable way to understand which features a model relies on most, helping validate whether the model’s behavior aligns with real-world expectations