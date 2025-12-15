# (5) Cross-Validation

https://www.kaggle.com/code/alexisbcook/cross-validation

## 1. Introduction
- ML involves many iterative decisions (features, models, hyperparameters)
- model quality is often evaluated using a single validation (holdout) set
- this approach can be **noisy and unreliable**, since results depend on which data points end up in the validation set
- using a larger validation set reduces randomness but leaves less data for training, which can hurt model performance

## 2. What is cross-validation?
- **cross-validation** evaluates a model by training and validating it multiple times on different subsets of the data
- the dataset is split into *k* equal parts called **folds**
- for each fold:
    - one fold is used as the validation set
    - the remaining folds are used for training
- each data point is used once for validation and multiple times for training
- final model performance is calculated by averaging results across all folds, giving a more reliable estimate

## 3. When should you use cross-validation?
- use cross-validation when:
    - the dataset is **small**
    - you are making many modeling decisions
    - model training is relatively fast
- use a single validation set when
    - the dataset is **large**
    - training is computationally expensive
- if cross-validation scores are similar across folds, a single validation set may be sufficent

## 4. Example
- a **pipeline** is used to combine preprocessing (imputation) and a random forest model
- cross-validation is performed using `cross_val_score()` with 5 folds
- model performance is evaluated using **Mean Absolute Error (MAE)**
- Scikit-learn reports **negative MAE** to follow its convention where higher scores are better
- the final model score is the average MAE across all folds

## 5. Conclusion
- cross-validation provides a **more accurate and stable** measure of model performance
- it removes the need to manuallt manage training and validation splits
- especially for small datasets, cross-validation is a powerful improvement over a single holdout set