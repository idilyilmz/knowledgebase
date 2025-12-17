# (3) Seasonality

https://www.kaggle.com/code/ryanholbrook/seasonality

## 1. What is Seasonality?
- a time series exhibits **seasonality** when there is a regular, repeating pattern in its mean that follows a fixed calendar or clock cycle (such as daily, weekly or yearly)
- seasonal behavior is often driven by natural cycles (day/night, seasons) or human activity (workweeks, holidays)
- unlike trends, seasonal patterns repeat consistenlty over time

## 2. Seasonal Plots and Seasonal Indicators
- **seasonal indicators** (also called dummy variables) model seasonality by treating the seasonal period as a categorical variable and applying one-hot encoding
    - best for **short seasons** with few observations (like, weekly seasonality in daily data)
    - each indicator represents a specific position in the season (like, day of week)
    - linear regression learns a baseline level and adjusts it using the active indicator
- this approach allows the model to learn different average values for each seasonal time point

## 3. Fourier Features and the Periodogram
- for **long seasons** with many observations (such as annual seasonality in daily data), seasonal indicators become inefficient
- **fourier features** provide a compact alternative by modeling seasonality using pairs of sine and cosine curves at different frequencies:
    - each sine/consine pair captures a specific frequency (once per year, twice per year, etc)
    - a small number of Fourier pairs can approximate complex seasonal shapes
- the **periodigram** helps determine how many Fourier pairs to include by showing which frequencies explain the most variance in the series
- frequencies with low contribution can be ignored, reducing overfitting and computation

## 4. Example - Tunnel Traffic
- The Tunnel Traffic dataset shows both **weekly** and **annual** seasonality
    - seasonal plots and the periodogram reveal a strong weekly pattern and a weaker annual pattern
    - **weekly seasonality** is modeled using seasonal indicators
    - **annual seasonality** is modeled using Fourier features (10 sine/cosine pairs).
    - these seasonal features are combined with a linear trend using `DeterministicProcess`
- the fitted model captures repeating traffic patterns and produces a reasonable **out-of-sample seasonal forecast**

## 5. Key takeaway
- choose seasonal indicators for short, discrete seasons and Fourier features for long, continuous seasons
- together with trend modeling, these techniques form a strong foundation for accurate time series forecasting