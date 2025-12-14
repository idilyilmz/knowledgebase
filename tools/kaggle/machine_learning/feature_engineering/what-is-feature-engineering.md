# (1) What Is Feature Engineering

https://www.kaggle.com/code/ryanholbrook/what-is-feature-engineering

## 1. Welcome to Feature Engineering!
- feature engineering is a key step in building strong machine learning models
- skills covered include
    - identifying important features (like, using mutual information)
    - creating new features from real-world data
    - encoding high-cardinality categoricals (target encoding)
    - segmenting data (k-means clustering)
    - decomposing variation (PCA)
- hands-on exercises culminate in a House Prices competition submission

## 2. The Goal of Feature Engineering
- aim: make data more suitable for the problem
- example: "Apparent temperature" (heat index/wind chill) combines measures features to reflext what actually matters
- benefits
    - improve predictive performance
    - reduce computational/data requirements
    - increase interpretability

## 3. A Guiding Principle of Feature Engineering
- features must have a relationship with the target that the model can learn
- example: linear models can only learn linear relationships. Transform features to match model capabilities
    - predicting land price from side length: use **Area = Length²** to create a linear relationship for the model
- feature transformations effectively become part of the model
- investing in feature engineering can yield high performance gains

## 4. Example - Concrete Formulations
- dataset: concrete ingredients → CompressiveStrength
- baseline model (Random Forest) MAE: 8.232
- insight: ratios of ingredients are better predictors than absolute amounts
- added synthetic features:
    - `FCRatio = FineAggregate / CoarseAggregate`
    - `AggCmtRatio = (CoarseAggrehate + FineAggregate) / Cement`
    - `WtrCmtRatio = Water / Cement`
- model with ratio features MAE improved to 7.948
- conclusion: new features revealed important relationships the model couldn't detect before