# (3) Creating Features

https://www.kaggle.com/code/ryanholbrook/creating-features

## 1. Introduction
- after identifying useful features, develop them using transformations in Pandas.
- explore datasets with diverse feature types: US Traffic Accidents, 1985 Automobiles, Concrete Formulations, Customer Lifetime Value
- tips for discovering features
    - understand the data and problem domain
    - research previous work and Kaggle solutions
    - use data visualization to reveal distributions and relationships

## 2. Mathematical Transforms
- apply arithmetic or domain-inspired formulas to numerical features.
- examples:
    - **stroke ratio**: `stroke/ bore` → engine efficiency
    - **displacement**: `π * (0.5 * bore)^2 * stroke * num_of_cylinders` → engine power
- use powers or logarithms to reshape sjewed distributions (like, log-tranform WindSpeed)

## 3. Counts
- aggregate sets of binary/boolean features into counts
- examples:
    - **RoadwayFeatures** = sum of boolean columns for roadway objects in Traffic Accidents dataset
    - **components** = count of nonzero ingredients in Concrete dataset

## 4. Building-Up and Breaking-Down Features
- **split complex strings** into simpler components:
    - policy → type of level (`str.split`)
    - phone numbers, dates, product codes, addresses
- **combine simple features** if interactions are meaningful:
    - `make_and_style = make + "_" + body_style`

## 5. Group Transforms
- aggregate information accross rows grouped by categorical features
- examples: 
    - average income by state → `groupby("State")["Income"].transform("mean")`
    - frequency encoding of categories → proportion of occurrences
- for train/validation splits, compute grouped features on training set and merge to validation set to avoid leakage.

## 6. Tips on creating features
- consider model type and learning capacity:
    - linear models: sums/differences
    - ratios: often effective
    - normalization: helps neural nets and sometimes tree models
    - tree models: can learn complex combinations, but explicit features help when data is limited
    - counts: especially useful for tree models
