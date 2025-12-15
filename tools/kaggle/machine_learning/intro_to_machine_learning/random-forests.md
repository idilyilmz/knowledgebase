# (6) Random Forests

https://www.kaggle.com/code/dansbecker/random-forests

## 1. Introduction
- decision trees face a tradeoff between **overfitting** (too deep) and **underfitting** (too shallow)
- **random forests** address this problem by combining many decision trees into one model
- each tree makes its own prediction and the final result is the **average** of all trees
- random forests usually achieve **higher accuracy** than a single decision tree
- they work well with default settings and are less sensitive to parameter tuning

## 2. Example
- the dataset is split into training and validation sets
- a `RandomFprestRegressor` is trained using the same features as before
- predictions are evaluated using **Mean Absolute Error (MAE)**
- the random forest significantly reduces error compared to a single decision tree

## 3. Conclusion
- random forests provide strong improvement over decision trees by reducing overfitting
- while firsther tuning can improve resultts, random forests perform well even without it
- they are a reliable and powerful model choice for many machine learning problems
