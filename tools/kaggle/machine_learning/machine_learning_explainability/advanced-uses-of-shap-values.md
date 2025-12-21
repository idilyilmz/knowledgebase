# (5) Advanced Uses of SHAP Values

https://www.kaggle.com/code/dansbecker/advanced-uses-of-shap-values

## 1. Recap
- **permutation importance** and **Partial Dependence Plots (PDPs)** provide high-level, model-wide insights.
- **SHAP values** explain individual predictions
- by **aggregating SHAP values**, we can gain richer, more detailed global insights that improve upon permutation importance and PDPs

## 2. SHAP Values Review
- SHAP values measure how much a feature value changes a prediction compared to a baseline.
- Key property:
    - The sum of SHAP values across all features explains the difference between the model’s prediction and the baseline prediction.
- although SHAP values are complex to compute for advanced models, they allow any prediction to be decomposed into interpretable feature contributions

## 3. Summary Plots
- permutation importance ranks features but does not explain how features influence predictions
- SHAP summary plots provide a comprehensive view showing:
    - **which features are most important**
    - **whether high or low feature values increase or decrease predictions**
    - **how effects vary across data points**

### a. how to Read a Summary Plot:
- each dot represents one data point
- vertical position = feature name
- color = feature value (high or low)
- horizontal position = SHAP value (positive or negative effect on prediction)

key insights from the soccer example:
- some features (e.g., Red cards) are ignored by the model
- high values of *Goals Scored* strongly increase predictions
- some features have rare but extreme effects rather than consistent influence

## 4. Summary Plots in Code
- PDPs show average feature effects but hide variation and interactions
- SHAP dependence plots improve on PDPs by:
    - Showing the **distribution of effects** for each feature value
    - Revealing **interactions with other features**

### a. Interpretation:
- Each dot is a data point
- X-axis = feature value
- Y-axis = SHAP value (feature’s impact on prediction)
- vertical spread indicates interaction with other features

For example:
- increased ball possession generally raises predictions
- however, when teams score only one goal, increased possession may reduce the prediction, an interaction revealed through color coding

## 5. SHAP Dependence Contribution Plots
- color in dependence plots represents the value of an interacting feature
- this helps identify cases where a feature’s effect depends on another feature’s value
- linear models produce straight lines with no spread, while complex models show variability and interactions

## 6. Dependence Contribution Plots in Code / (Key Takeaways)
- aggregated SHAP visualizations combine the strengths of permutation importance and partial dependence plots while adding deeper insight into feature distributions and interactions
- the real challenge lies not in generating these plots, but in critically interpreting what they reveal about model behavior