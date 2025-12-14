# (2) Mutual Information

https://www.kaggle.com/code/ryanholbrook/mutual-information

## 1. Introduction
- facing a new dataset with many features can be overwhelming
- start by ranking features with a **feature utility metric** to identify the most useful ones
- **Mutual Information (MI)** is a versatile metric for measuring the relationship between a feature and the target
    - detects any kind of relationship (not just linear like correlation)
    - easy to use, cumputationally efficient, theoretically sound, resistant to overfitting

## 2. Mutual Information and What it Measures
- MI quantifies how much knowing a feature reduces uncertainty about the target
- example: Ames Housing - exterior quality (ExterQual) reduces uncertaunty about SalePrice
- MI is based on **entropy** from information theory: more entropy = more uncertainty
- MI of 0 → feature and target are independent.
- High MI → feature reduces a lot of uncertainty in the target

## 3. Interpreting Mutual Information Scores
- MI is a **univariate metric**: meausres each feature individually, not interactions.
- A feature can have high MI but still require transformation for the model to use it effectively.
- Use MI as a guide to prioritize features for development and visualization.

## 4. Example - 1985 Automobiles
- Dataset: 193 cars, 23 features → target: price
- Preprocess categorical features with label encoding for MI calculation.
- Scikit-learn functions:
    - `mutual_info_regression` → real-valued target
    - `mutual_info_classif`→ categorical target
- example MI scores:
    - `curb_weight`: 1.54 → high impact
    - `highway_mpg`: 0.95
    - `fuel_type`: 0.048 → low individually but may show interaction effects
- visualizations help confirm MI insights and reveal interaction effects
    - `curb_weight` strongly correlates with price
    - `fuel_type` seperates price trends within `horsepower`
- conclusion: combine MI scores with domain knowledge and visualization to guide feature engineering