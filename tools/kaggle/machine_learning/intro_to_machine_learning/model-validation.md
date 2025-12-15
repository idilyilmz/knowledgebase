# (4) Model Validation

https://www.kaggle.com/code/dansbecker/model-validation

## 1. Experimenting With Different Models
- once model accuracy can be measured, we can compare different models to find the best performer
- for decision trees, the most important hyperparameter is **tree depth**, which controls how many splits the tree makes
- deeper trees create more leaves, each containing fewer data points
- **overfitting** occurs when a model is too complex:
    - fits training data extremely well
    - performs poorly on validation (new) data
- **underfitting** occurs when a model is too simple
    - fails to capture important patterns
    - performs poorly even on training data
- the goal is to find a balance where validation error is minimized

## 2. Example
- the parameter `max_leaf_nodes` is used to control tree complexity
- fewer leaf nodes → simpler model (risk of underfitting)
- more leaf nodes → more complex model (risk of overfitting)
- a utility function computes **Mean Absolute Error (MAE)** for different values of `max_leaf_nodes`
- by testing several options, validation MAE reveals the optimal model size
- in the example, a tree with **500 leaf nodes** achieved the lowest validation error

## 3. Conclusion
- models can fail due to:
    - **overfitting**: learning noise instead of true patterns
    - **underfitting**: missing important patterns entirely
- validation data provides an unbiased way to evaluate models
- comparing models using validation error allows selection of the most accurate model for new data