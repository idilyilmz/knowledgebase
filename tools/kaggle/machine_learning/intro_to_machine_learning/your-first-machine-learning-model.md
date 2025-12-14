# (3) Your First Machine Learning Model

https://www.kaggle.com/code/dansbecker/your-first-machine-learning-model

## 1. Selecting Data for Modeling
- real-world datasets often contain many columns, making them hard to work with all at once
- the first step is to **select a subnet of relevant variables** using intuition
- all column names in a DataFrame can be viewed using `DataFrame.columns()`
- some datasets contain missing values; for now, rows with missing values are dropped using `.dropna()` 
- pandas offers many ways to select data, but this lesson focuses on:
    - **dot notation** (for the target variable)
    - **column lists** (for feature selection)

### a. Selecting The Prediction Target
- the **prediction target** is the value the model is trying to predict.
- by convention, the target variable is names `y`
- dot notation is used to extract a single column as a Series
- example:
```
y = melbourne_data.Price
```

## 2. Choosing "Features"
- **features** are the input variables used to make predictions
- by convention, feature data is named `X`
- features are selected by passing a list of column names to the DataFrame
- using fewer, meaningful features can simplify models and improve understanding
- example features include:
    - rooms
    - bathroom
    - landsize
    - latitude
    - longitude
- `.describe()` and `.head()` are used to visually inspect feature data and check for issues

## 3. Building Your Model
- models are built using the **scikit-learn** library (`sklearn`)
- the standard machine learning workflow includes
    1. **Define** the model
    2. **Fit** the model to training data
    3. **Predict** outcomes
    4. **Evaluation** model accuract
- a **DecisionTreeRegressor** is used for predicting house prices
- setting `random_state` ensures reproducible results
- once trained, the model can make predictions using `.predict()`
- initial predictions are demonstrated using the training data to show how the model works