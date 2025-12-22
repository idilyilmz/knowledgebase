# (6) Binary Classification

https://www.kaggle.com/code/ryanholbrook/binary-classification

## 1. Introduction
- this chapter extends neural networks from **regression** to **classification**
- most concepts remain the same, but classification requires different **loss functions** and **output activations** so the model can predict class probabilities instead of numeric values

## 2. Binary Classification
- **binary classification** involves predicting one of two possible classes (e.g., yes/no, fraud/not fraud, disease/no disease).
    - classes are encoded numerically as **0** and **1**
    - neural networks use these numeric labels to learn decision boundaries
    - common applications include customer behavior, medical diagnosis, and anomaly detection

## 3. Accuracy and Cross-Entropy
- **accuracy** measures the proportion of correct predictions and is useful when classes are balanced, but it cannot be used as a loss function because it changes in discrete steps
- instead, neural networks use **cross-entropy loss**, which:
    - measures the distance between predicted probabilities and true labels
    - penalizes confident but incorrect predictions heavily
    - provides a smooth objective suitable for gradient descent
- for binary classification, the appropriate loss is **binary cross-entropy**
- as this loss decreases, accuracy typically improves as well

## 4. Making Probabilities with the Sigmoid Function
- neural networks produce real-valued outputs, which must be converted into probabilities.
- the **sigmoid activation function** maps any real number into the interval [0,1], making it ideal for binary classification outputs.
    - a probability threshold (usually 0.5) determines the predicted class
    - values below 0.5 → class 0
    - values at or above 0.5 → class 1

## 5. Example - Binary Classification
- the **Ionosphere dataset** is used to classify radar signals as detecting an object or empty space.
    - inputs: normalized radar signal features
    - model: two hidden ReLU layers and a sigmoid output layer
    - loss: binary cross-entropy
    - metric: binary accuracy
    - optimizer: Adam
- training includes **early stopping** to prevent overfitting
- the trained model achieves strong validation performance, demonstrating how neural networks can effectively solve binary classification problems