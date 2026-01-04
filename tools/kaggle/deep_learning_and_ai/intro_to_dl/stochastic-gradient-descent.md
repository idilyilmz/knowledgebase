# (3) Stochastic Gradient Descent

https://www.kaggle.com/code/ryanholbrook/stochastic-gradient-descent

## 1. Introduction

- neural networks start with **random weights** and must be trained to learn meaningful relationships from data
- training means adjusting these weights so the network can map **input features** to **target values**
- this process requires training data, a **loss function**, and an **optimizer**

## 2. The Loss Function
- the **loss function** defines what problem the network is trying to solve by measuring how far predictions are from true targets
- for **regression problems**, a common loss function is **Mean Absolute Error (MAE)**:

$$
MAE=1𝑛∑∣𝑦true−𝑦pred∣MAE=n1∑∣ytrue−ypred∣
$$

- lower loss indicates better predictions
- other regression losses include **MSE** and **Huber loss**
- the loss function acts as the network’s **objective**, guiding learning

## 3. The Optimizer - Stochastoc Gradient Descent

- the **optimizer** determines how the network updates its weights to minimize loss
- most deep learning optimizers are variants of **Stochastic Gradient Descent (SGD)**

SGD works iteratively:

1. sample a **minibatch** of training data
2. compute predictions and loss
3. adjust weights to reduce the loss
4. repeat until the loss converges
- a **batch** is a small random subset of the data
- on **epoch** is one full pass through the dataset

### a. Learning Rate and Batch Size

- **learning rate** controls how large each weight update is
    - too large → unstable training
    - too small → slow convergence
- **batch size** determines how many samples are used per update
- the interaction between learning rate and batch size strongly affects training

**Adam** is a popular SGD variant with an adaptive learning rate and works well for most problems with little tuning.

### b. Adding the Loss and Optimizer

- in Keras, the loss function and optimizer are added using `compile`:

```
model.compile(
    optimizer='adam',
    loss='mae',
)
```

- these can be specified as strings using sensible defaults or customized via the Keras API

## 4. Example - Red Wine Quality

- the Red Wine Quality dataset contains **11 physiochemical features** used to predict a wine’s **quality score**
    - inputs: 11 features (excluding the target)
    - model: deep fully-connected network with three hidden layers
    - activation: ReLU for hidden layers, linear output for regression
    - training parameters: batch size = 256, epochs = 10
- during training, **loss decreases** and **eventually plateaus**, indicating the model has learned as much as it can
- plotting the training loss helps identify when additional epochs are no longer useful