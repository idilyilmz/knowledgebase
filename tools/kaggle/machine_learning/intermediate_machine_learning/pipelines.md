# (4) Pipelines

https://www.kaggle.com/code/alexisbcook/pipelines

## 1. Introduction
- **pipelines** bundle data preprocessing and model training into a single, unified workflow
- they allow you to treat multiple steps (imputation, encoding, modeling) as one operation
- kay benefits
    - **cleaner code** by avoiding manual preprocessing steps
    - **fewer bugs** from inconsistent data handling
    - **easier deployment** from experimentation to production
    - **better model validation**, especially when combined with cross-validation

## 2. Example
- applied to the **Melbourne Housing dataset**, which includes both categorical variables and missing values
- data is split into training and validation sets
- preprocessing is handling with a `ColumnTransformer`:
    - numerical features: missing values are imputed
    - categorical features: missing values are imputed and then one-hot encoded
- a **RandomForestRegressor** is used as the model
- the pipeline
    - preprocesses data and fits the model in one step
    - automaticallt applies the same preprocessing to validation data during prediction
- model performance is evaluated using **Mean Absolute Error (MAE)**

## 3. Conclusion
- pipelines simplify machine learning workflows and reduce the risk of preprocessing errors
- they are especially useful when working with mixed data types and complex preprocessing
- using pipelines leads to more maintainable, reproducible and production-ready ML code