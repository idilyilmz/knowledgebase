# (4) Time Series as Features

https://www.kaggle.com/code/ryanholbrook/time-series-as-features

## 1. What is Serial Dependence?
- **serial dependence** occurs when the value of a time series depends on its past values rather than directly on time itself
- unlike trend and seasonality, serial dependence may not be visible in a time plot, but becomes clear when plotting current values against previous values
- a common manifestation of serial dependence is **cycles**, which are patterns of growth and decay driven by feedback effects within a system (like, economies, epidemics, populations)
- cycles differ from seasonality because they aren't tied to specific dates and can be irregular in timing and magnitude

## 2. Lagged Series and Lag Plots
- to model serial dependence, we use **lagged series**, which shift past values of the target forward in time so they can be used as features
- **lag plots** visualize the relationship between a series and its lags and help reveal serial structure
- key tools for selecting lag features include
    - **autocorrelation**: measures correlation between a series and its lag
    - **partial autocorrelation**: measures the "new" information a lag provides after accounting for earlier lags
    - **correlograms**: plots of partial autocorrelations that help identify useful lags
- because autocorrelation captures only linear relationships, lag plots are essential for detecting **nonlinear dependence**, which may require transformations or nonlinear models

## 3. Example - Flu Trends
- the Flu Trends dataset shows irregular, cyclic behavior rather than clear seasonality.
- two forecasting approaches are explored
    1. **using lag features of flu visits**: 
        - lag plots and partial autocorrelation suggest using the most recent four weeks
        - this model reacts slowly to sudden changes because it relies only on past target values
    2. **using leading indicators**:
        - adding lagged Google search terms related to flu symptoms improves forecasts
        - these external time series act as early warning signals, allowing the model to anticipate increases in flu cases

## 4. Key takeaways
- lag features allow models to learn cycles and serial dependence, and forecasts can be significantly improved by including **leading indicator time series**
- many real-world time series contain trend, seasonality, and cycles simultaneously, and these components can be modeled together or combined using hybrid forecasting approaches
