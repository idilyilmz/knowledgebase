# (1) How Models Work

https://www.kaggle.com/code/dansbecker/how-models-work

## 1. Introduction
- machine learning models learn patterns from past data to make predictions on new data
- in this course, models are used to predict **house prices** based on historical real estate data
- this mirrors how humans make predictions using experience and intuition
- the first model introduced is the **Decision Tree**, chosen because it's simple and easy to understand
- models are **trained (fit)** using training data, where patterns and relationships are learned
- once trained, the model can be used to make predictions on new, unseen data

## 2. Improving the Decision Tree
- a basic decision tree splits data into groups and predicts values using historical averages
- early trees mat consider only one feature (like, number of bedrooms)
- deeper decision trees include more features and splits (like, lot size, bathrooms)
- each split improves the model's ability to capture factors affecting house prices
- predictions are made by following decision rules to a **leaf**, which contains the predicted value
- more complex trees can model reality better but require careful design and data