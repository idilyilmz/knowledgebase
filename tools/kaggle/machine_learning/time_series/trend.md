# (2) Trend

https://www.kaggle.com/code/ryanholbrook/trend

## 1. What is Trend?
- the **trend** of a time series is the long-term, persistent change in its average value over time
- it moves more slowly than other components and reflects the largest time scale of importance
- **example**: increasing product sales over several years may indicate market growth
- while this lesson focuses on trends in the **mean**, trends can also exist in other properties of a series, such as variability

## 2. Moving Average Plots
- **moving average plot** helps reveal the underlying trend by smoothing short-term fluctuations
- it works by averaging values within a sliding time window, leaving only long-term patterns visible
- to ensure seasonal effects are removed, the window size should be **longer than the seasonal period** (like, a 12-month window for yearly seasonality)
- moving averages are primarly used for **visualizing** trends rather than forecasting

## 3. Engineering Trend
- once the trend shape is identified, it can be modeled using **time-step features** in linear regression
    - a **linear trend** uses the time dummy directly
    - a **quadratic (or higher-order) trend** is modeled by adding powers of the time variable
- although called "linear" regression, the model can fit curved if curved features (like time²) are included
- the lesson introduces **DeterministicProcess** from `statsmodels` to safely generate trend features (constant, linear, quadrsatic, etc) and avoid issues liek collinearity 

## 4. Example - Tunnel Traffic
- the Tunnel Traffic dataset is analyzed to model long-term vehocle flow
    - a **365-day moving average** shows the trend is approximately linear
    - a **linear trend model** is built using `DeterministicProcess` and `LinearRegression`
    - the fitted trend closely matches the moving average, confirming the choice of a linear trend
    - the model is then used to generate a **30-day out-of-sample forecast**

## 5. Key takeaways
- trend models provide a strong baseline for forecasting and are especially valuable as components in **hybrid models**
- where ML algorithms that cannot naturally learn trends benefit from having trend removed or modeled