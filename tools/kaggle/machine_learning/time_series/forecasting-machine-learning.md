# (6) Forecasting With Machine Learning

https://www.kaggle.com/code/ryanholbrook/forecasting-with-machine-learning

## 1. Introduction
- early forecasting lessons treated time series prediction as a standard regression problem using only deterministic features derived from the time index, such as trend and seasonality
- these features can be generated for any future time, making long-range forecasting straightforward
- when **lag features** are introduced, forecasting becomes more complex
- lag features require past target values to be known at prediction time, which limits how far ahead a model can forecast directly
- while one-step-ahead forecasting is simple, real-world applications often require forecasts over multiple future steps
- this lesson addresses how to design and evaluate **multistep forecasts** under these constraints

## 2. Defining the Forecasting Task
- before building a forecasting model, two aspects must be clearly defined:
    - **features**: the information available at the time the forecast is made.
    - **target**: the future time period over which predictions are required.
- key concepts:
    - **forecast origin**: the time at which the forecast is issued; all data up to this point can be used to create features.
    - **forecast horizon**: the future time span being predicted, often described by the number of steps (like, 1-step, 8-step).
    - **lead time**: the gap between the forecast origin and the start of the forecast horizon, which may exist due to data delays or processing time
- these definitions determine which lagged values can be used and how the dataset must be structured

## 3. Preparing Data for Forecasting
- machine learning models require time series data to be converted into a tabular format:
    - **lag features** are created by shifting the target series backward in time
    - **multistep targets** are created by shifting the target series forward, with each column representing a future step
- each row of the dataset corresponds to a **single forecast**, containing:
    - feature values available at the forecast origin
    - target values for every step in the forecast horizon
- for multistep forecasting, the target becomes multi-dimensional, requiring the model to produce multiple outputs simultaneously or through reduction strategies

## 4. Multistep Forecasting Strategies
- several strategies are commonly used to generate multistep forecasts:
    - **multioutput strategy**
        - Use a model that naturally supports multiple outputs (like, linear regression, neural networks)
        - This approach is simple and efficient but limited to compatible algorithms
    - **direct strategy**
        - train a separate model for each step in the forecast horizon
        - each model specializes in a specific lead time, improving flexibility at the cost of increased computation
    - **recursive strategy**
        - train a single one-step-ahead model and iteratively feed its predictions back as lag features
        - this requires only one model but can suffer from accumulating errors over long horizons
    - **DirRec strategy**
        - A hybrid of Direct and Recursive approaches: 
            - train a model for each step while also incorporating predictions from previous steps as features
            - this captures serial dependence better but still risks error propagation
- Each strategy involves trade-offs between accuracy, complexity, and computational cost

## 5. Example - Flu Trends
- the Flu Trends dataset is used to demonstrate true multistep forecasting beyond the training period. 
- the task is defined as:
    - **forecast horizon**: 8 weeks
    - **lead time**: 1 week
- **Multioutput model (Linear Regression)**:
    - Uses four weeks of lag features.
    - Produces all eight forecast steps simultaneously.
    - Provides stable but limited forecasts due to its linear structure.
- **Direct strategy (XGBoost)**:
    - Uses a separate XGBoost model for each forecast step via `MultiOutputRegressor`.
    - Overfits the training data but captures nonlinear seasonal dynamics better on the test set.
    - Demonstrates the advantage of nonlinear models for complex temporal patterns.

## 6. Key takeaways
- multistep forecasting requires careful definition of the forecasting task and deliberate choice of strategy
- no single approach is best for all situations—effective forecasting balances horizon length, model complexity, and the risk of error propagation