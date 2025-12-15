# (5) Underfitting and Overfitting

https://www.kaggle.com/code/dansbecker/underfitting-and-overfitting

## 1. Experimenting With Different Models
- decision trees have many configuration options; the most important is **tree depth**, which controls how many splits the model makes
- deeper trees create more leaves, each containing fewer training examples
- **overfitting** happens when a model is too complex
    - fits training data very closely
    - makes unreliable predictions on new (validation) data
- **underfitting** happens when a model is too simple
    - fails to capture meaningful patterns
    - performs poorly even on training data
- the goal is to fidn a **balance** between underfitting and overfitting that minimizes validation error

## 2. Example
- the parameter `max_leaf_nodes` is used to control model complexity
- small values → underfitting; large values → overfitting
- a function is used to calculate **Mean Absolute Error (MAE)** on validation data for different tree sizes
- testing multiple values shows that:
    - too few leaves give high error
    - too many leaves also increase error
- in the example, **500 leaf nodes** produces the lowest validation MAE

## 3. Conclusion
- models can fail due to:
    - **overfitting**: learning noise instead of general patterns
    - **underfitting**: missing important patterns entirely
- validation data provides an unbiased wat to evaluate model performance
- comparing models across different complexities helps select the most accurate model for new data