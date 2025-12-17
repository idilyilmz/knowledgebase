# (1) Linear Regression With Time Series

https://www.kaggle.com/code/ryanholbrook/linear-regression-with-time-series

## 1. Welcome to Time Series!
- time series forecasting is one of the most common real-worls uses of ML, applied in areas like
    - business demand forecasting
    - economics
    - population growth
    - weather prediction
- this course focuses on using **modern machine learning methods**, inspired by winning Kaggle solutions, to produce accurate forecasts
- by the end of this course, learners will be able to
    - engineer time series features
    - visualize time series data
    - combine multiple models into forecasting hybrids
    - adapt ML techniques to different forecasting problems
- a hands-on kaggle competition is included for practivce :)

## 2. What is a Time Series?
- a **time series** is a sequence of observations recorded over time at a regular frequency (like, daily or monthly)
- in forecasting tasks, data is indexed by time, often using dates
- **example**: daily hardcover book sales recorded over 30 days, where the dataset consists of a single observation column and a time-based index

## 3. Linear Regression with Time Series
- **linear regression** is used as a foundational forecasting model due to its simplicity and flexibility
- the key idea is to predict future values using a weighted combination of input features
- two important **time-series-specific features** are introduced
    - **time-step features**: derived directly from the time index (like, a time counter), these help model **time dependence** and trends
    - **lag features**: past values of the series shifted forward in time (like, yesterday's value), these help model **serial dependence**, where current values depend on previous observations
- using these featuress, linear regression can model trends over time and correlations between consecutive observations

## 4. Example - Tunnel Traffic
- the tunnel traffic dataset records daily vehicle counts through a Swiss tunel
- a **lag feature** is used to predict today's traffic based on yesterday's traffic
- linaer regression models are trained using each feature type and visualizations (time plots and lag plots) show how well the models capture trends and dependencies

## 5. key takeaways
- effective time series forecasting usually combines both **time-step features (for trends)** and **lag features (for short-term dependencies)**
- these concepts form the foundation for more advanced models later in the course