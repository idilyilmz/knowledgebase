# (4) Overfitting and Underfitting

https://www.kaggle.com/code/ryanholbrook/overfitting-and-underfitting

## 1. Introduction

- this chapter explains how to use learning curves (training and validation loss) to guide model development
- by analyzing these curves, we can detect underfitting and overfitting and apply strategies to improve generalization

## 2. Interpreting the Learning Curves

- training data contains both **signal** (patterns that generalize) and **noise** (random or non-informative patterns)
    - **training loss** decreases when the model learns signal or noise
    - **validation loss** decreases only when the model learns signal
- when both losses decrease together, the model is learning useful patterns
- when a gap forms and validation loss stops improving or increases, the model is learning noise
    - **underfitting**: model hasn’t learned enough signal
    - **overfitting**: model has learned too much noise
- the goal is to find the best balance between the two, where validation loss is minimized

## 3. Capacity

- a model’s capacity is its ability to learn complex patterns and is mainly determined by:
    - number of neurons
    - number of layers
- to fix **underfitting**, increase capacity by:
    - making the network **wider** (more units per layer)
    - making it **deeper** (more layers)
- wider networks tend to learn linear patterns more easily, while deeper networks capture nonlinear relationships

## 4. Early Stoppingh

- when validation loss begins to rise, the model is starting to overfit.
- **early stopping** halts training at the point where validation loss is lowest.
- benefits:
    - prevents overfitting from training too long
    - prevents underfitting from stopping too early
    - restores the model to its best-performing weights

### a. Adding Early Stopping

- early stopping is implemented in Keras using a **callback**, which checks validation loss after each epoch:
    - `min_delta`: minimum improvement to count as progress
    - `patience`: number of epochs to wait before stopping
    - `restore_best_weights`: keeps the best model found

## 5. Example - Train a Model with Early Stopping

- a high-capacity neural network is trained on the **Red Wine Quality** dataset using early stopping.
    - network: three hidden layers with 512 ReLU units each
    - inputs: 11 scaled features
    - optimizer: Adam
    - loss: MAE
    - training stops automatically before the maximum number of epochs
- the learning curves show validation loss decreasing and then leveling off, confirming that early stopping prevents overfitting while preserving performance.