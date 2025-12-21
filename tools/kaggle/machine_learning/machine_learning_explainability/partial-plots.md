# (3) Partial Plots

https://www.kaggle.com/code/dansbecker/partial-plots

## 1. Partial Dependence Plots
- while **feature importance** shows which features matter most, **partial dependence plots** explain **how a feature affects model predictions**.
- PDPs help answer questions such as:
    - how does a single feature influence predictions while holding other features constant?
    - are observed differences between groups driven by a specific feature or by other factors?
- PDPs can be interpreted similarly to coefficients in linear or logistic regression, but they are more powerful because they can capture **non-linear** and **complex relationships** in advanced models

## 2. How It Works
- partial dependence plots are computed **after the model is trained**, without altering the model itself
- the process:
    1. select a single data point
    2. vary one feature across a range of values while keeping all other features fixed
    3. Use the model to predict outcomes for each value
    4. Repeat this process for many data points
    5. Average the predictions to produce the partial dependence curve
- the x-axis shows feature values, and the y-axis shows the average change in the model’s prediction relative to a baseline

## 3. Code Example
- a model predicts whether a player wins *Man of the Match* based on team statistics
- PDPs reveal how individual features such as **Goals Scored** or **Distance Covered** affect predictions

### a. Goals Scored
- scoring at least one goal greatly increases the probability of winning *Man of the Match*
- additional goals beyond the first have little extra effect

### b. Distance Covered
- decision Tree PDPs produce step-like plots reflecting the tree structure
- random Forest PDPs generate smoother curves, showing more realistic trends
- the Random Forest model suggests performance improves up to about 100 km covered, then declines

## 4. Comparing Models with PDPs
- PDPs make it easy to compare how different models interpret the same feature:
    - simple models (Decision Trees) show abrupt changes
    - ensemble models (Random Forests) capture smoother, more plausible relationships

## 5. 2D Partial Dependence Plots
- 2D PDPs visualize interactions between two features
- key insights from the example:
    - the highest predictions occur when a team scores at least one goal and runs close to 100 km
    - if no goals are scored, distance covered has little effect
    - these interaction patterns can be verified directly from the decision tree structure

## 6. Key takeaways
partial dependence plots provide interpretable, model-agnostic insights into how features (and feature interactions) influence predictions, helping validate and explain complex machine learning models