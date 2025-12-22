# (5) Dropout and Batch Normalization

https://www.kaggle.com/code/ryanholbrook/dropout-and-batch-normalization

## 1. Introduction
- beyond dense layers, neural networks can include **special-purpose layers** that add functionality rather than neurons
- this chapter introduces **dropout** and **batch normalization**, two commonly used layers that help improve **generalization** and **training stability**

## 2. Dropout
- **dropout** is a regularization technique used to reduce **overfitting**
- overfitting occurs when a network learns fragile, overly specific patterns in the training data
- dropout addresses this by **randomly disabling a fraction of neurons during each training step**, forcing the network to learn more robust and general patterns
- dropout can also be viewed as an **ensemble method**, where training effectively averages the predictions of many smaller networks instead of relying on one large one

### a. Adding Dropout
- in Keras, dropout is applied using the `Dropout` layer, where `rate` specifies the fraction of inputs to drop:
```
layers.Dropout(0.3)
```
- dropout layers are typically placed **before the layer they affect**
- when using dropout, it’s often helpful to **increase the number of units** in dense layers to maintain capacity

## 3. Batch Normalization
- **batch normalization (batchnorm)** helps stabilize and speed up training
- neural networks train more effectively when inputs are on a **common scale**
- batch normalization extends this idea by **normalizing activations within the network** using the mean and standard deviation of each minibatch, followed by learnable rescaling

benefits of batch normalization:
- faster and more stable training
- fewer epochs needed
- reduced sensitivity to feature scale
- helps prevent training from getting “stuck”

### a. Adding Batch Normalization
- batch normalization can be added in several ways:
    - after a layer’s activation
    - between a layer and its activation function
    - as the first layer, acting as an adaptive preprocessor

Example:
```
layers.Dense(16),
layers.BatchNormalization(),
layers.Activation('relu')
```
## 4. Example - Using Dropout and Batch Normalization
- a high-capacity neural network is trained on the **Red Wine Quality** dataset using both dropout and batch normalization.
    - network: three large hidden layers (1024 units each)
    - dropout: 30% after each hidden layer
    - batch normalization: added to stabilize training
    - data: raw (not standardized) inputs
- the learning curves show controlled overfitting and stable optimization, demonstrating that **dropout improves generalization** while **batch normalization speeds and stabilizes training**