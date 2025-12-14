# (6) Target Encoding

https://www.kaggle.com/code/ryanholbrook/target-encoding

## 1. Introduction
- **target encoding** is a supervised feature engineering technique for **categorical features**
- unlike one-hor or label encoding, it uses information form the **target variable**
- categories are replaced with numeric values derived from their relationship to the target

## 2. Target Encoding
- a target encoding replaces each category with a statistic computed from the target
- the most common form is **mean encoding**, where each category is encoded as the average target value for that category
- for binary targets, this is also known as **bin counting**
- other names include likelihood encoding, impact encoding and leave-one-out encoding
- target encoding can capture how strongly a category relates to the target using a sungle numeric feature

## 3. Smoothing
- target encoding can easily **overfit**, especially with rare categories or small datasets
- two main issues:
    - **unknown categories** in future data result in missing values
    - **rare categories** produce unreliable estimates
- **smoothing** addresses this by blending
    - the category's target mean
    - the overall target mean
- m-estimate formula
    - `encoding = weight × category_mean + (1 − weight) × overall_mean`
    - `weight = n / (n + m)`
- rare categories receive more weight from the overall mean.
- the smoothing parameter m controls how conservative the encoding is:
    - larger m → more smoothing, less noise
    - smaller m → category mean dominates

## 4. Example - MovieLens1M
- MovieLens1M contains over **1 million ratings** and thousands of categories per feature.
- **zipcode** (3439 unique values) is a strong candidate for target encoding.
- a separate **encoding split** (25%) is used to train the encoder to avoid leakage.
- an **m-estimate encoder** converts Zipcode into a numeric feature using rating information.
- the encoded Zipcode distribution closely matches the rating distribution.
- this shows that target encoding successfully captured meaningful differences in user behavior across zipcodes.