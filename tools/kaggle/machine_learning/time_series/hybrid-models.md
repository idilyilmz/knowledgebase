# (5) Hybrid Models

https://www.kaggle.com/code/ryanholbrook/hybrid-models

## 1. Introduction
- different forecasting algorithms have complementary strengths and weaknesses
    - **linear regression** is good at extrapolating trends but cannor learn complex nonlinear interactions
    - **XGBoost (GBDTs)** excels at learning nonlinear relationships and interactions but cannot extrapolate trends beyond the training range
- **hybrid models** combine multiple algorithms so that the strengths of one compensate for the weaknesses of another
- in time series forecasting, this ofter means using a simple model to learn global structure (like trend) and a more flexible model to learn remaining patterns

## 2. Components and Residuals
- a time series can often be described using an **addictive component model**
```
series = trend + seasons + cycles + error
```
- each term is a **component** of the series
- when a model is fit, the difference between the observed values and the model's predictions is called the **residual**
- residuals represent what the model failed to learn
- learning components can be viewed as an **iterative subtraction process**:
    1. learn the trend and subtract it
    2. learn seasonality from the detrended series and subtract it
    3. learn cycles from the remaining residuals
    4. what remains is mostly random error
- if all components are modeled together (as in linear regression with full features), the final prediction is simply the sum of the learned components

## 3. Hybrid Forecasting with Residuals
- instead of learning all components with one algorithm, hybrids split the work:
    - **Model 1** learns some components (usually trend)
    - **Model 2** learns the residuals left begind by Model 1
- the process:
    1. train the first model on the original series and generate predictions
    2. subtract those predictions from the target to obtain residuals
    3. train a second model on the residuals
    4. add both predictions together for the final forecast
- this approach allows each model to focus on what it does best
- in practice, hybrids usually consist of:
    - a **simple, extrapolating model** (like, linear regression)
    - followed by a **powerful nonlinear model** (like, XGBoost)
- this residual-based approach is called **boosted hybrid**
- an alternative approach, where predictions from one model are used as features for another, is known as **stacking**.
- the motivation comes from how models work:
    - **feature-transforming models** (linear regression, neural networks) can extrapolate
    - **target-transforming models** (decision trees, random forests, XGBoost) cannot extrapolate and are limited to the range of the training data

## 4. Example - US Retail Sales
- the US retail sales dataset contains monthly sales data for multiple industries from 1992-2019
- the task is to forecast sales from 2016-2019

### step 1: learn the trend
- a quadratic linear regression model is trained using deterministic trend features
- this model extrapolates future trends for each retail industry

### step 2: prepare data for XGBoost
- the data is converted from wide to long format since XGBoost doesn't support multi-output regression
- industry labels are encoded as categorical features
- month numbers are added to represent annual seasonality

### step 3: learn residual patterns
- the linear regression trend predictions are subtracted from the original series to form residuals
- XGBoost is trained on these residuals to learn nonlinear structure and interactions

### step 4: combine predictions
- XGBoost's predicted residuals are added back to the linear trend forecasts
- the hybrid model produces improved fits and forecasts, though it cannot correct errors from a pooly learned trend

## 5. Key takeaways
- hybrid models work best when the first model captures the large-scale structure accurately
- the second model enhances the forecast by learning complex patterns in the residuals but cannot fix fundamental mistakes made by the initial trend model