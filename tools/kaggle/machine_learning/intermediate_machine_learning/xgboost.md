# (6) XGBoost

https://www.kaggle.com/code/alexisbcook/xgboost

## 1. Introduction
- random forests are **ensemble method** that average predictions from many decision trees
- **ensemble methods** combine multiple models to improve performance
- **gradient boosting** is another powerful ensemble technique that build models sequentially to correct previous errors
- XGBoost (Extreme Gradient Boosting) is a fast, optimized implementation of gradient boosting widely used in practice and competitions

## 2. Gradient Boosting
- gradient boosting builds and ensemble **iteratievly**, adding one model at a time
- the process
    1. start with a simple initial model
    2. generate predictions using the current ensemble
    3. compute a loss function (like, mean squared error)
    4. fit a new model to reduce this loss using gradient descent
    5. add the new model to the ensemble and repeat
- each new model model focuses on correcting the mistakes made by earlier models

## 3. Example
- the XGBoost model is trained using `XGBRegressor`
- the model is fit on training data and evaluated on validation data
- model performance is measured using **Mean Absolute Error (MAE)**
- XGBoost integrates smoothly with scikit-learn workflows 

## 4. Parameter Tuning
key parameters that strongly affect performance

- **n_estimators**
    - number of trees (models) in the ensemble
    - too few → underfitting; too many → overfitting
    - typically ranges from 100-1000
- **early_stopping_rounds**
    - stops training when validation performance stops improving
    - helps automatically find the optimal number of estimators
    - requires a validation set (`eval_set`)
- **learning_rate**
    - scales each tree's contribution to the ensemble
    - smaller values improve accuracy but require more trees
    - default is 0.1
- **n_jobs**
    - enables parallel training using mutliple CPU cores
    - speeds up training on large datasets without affecting model quality

## 5. Conclusion
- XGBoost is one of the most effective algorithms for **tabular data**
- it combines strong predictive power with flexibikity and speed
- with proper parameter tuning, XGBoost can produce highly accurate models and is a staple in competitive ML

