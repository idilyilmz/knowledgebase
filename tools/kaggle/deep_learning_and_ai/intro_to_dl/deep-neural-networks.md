# (2) Deep Neural Network

https://www.kaggle.com/code/ryanholbrook/deep-neural-networks

## 1. Introduction
- this chapter explains how neural networks learn **complex**, **non-linear relationships** by combining simple building blocks
- the key idea is **modularity**: complex models are built by stacking and modifying simple units like linear neurons

## 2. Layers
- neural networks organize neurons into **layers**.
- a **dense layer** is a group of linear units that all receive the same inputs.
- each layer performs a **simple transformation** of the data. By stacking many layers, a neural network can gradually transform inputs into more meaningful representations, allowing it to solve complex problems.
- keras layers are very flexible
    - some use neurons (dense, convolutional, recurrent)
    - while others perform feature engineering or arithmetic operations

## 3. The Activation Function
- stacking dense layers alone is not enough, without activation functions, neural networks can only learn **linear relationships**
- an **activation function** introduces **nonlinearity**, allowing the network to model curves and complex patterns.
- the most common activation is **ReLU (Rectified Linear Unit)**:
$$
ReLU(𝑥) = max(0,𝑥)
$$

applying ReLU to a linear unit bends the data, moving the model beyond lines and planes.
## 4. Stacking Dense Layers
- by stacking dense layers with activation functions, we create a **fully connected (deep) neural network**
    - layers between input and output are called **hidden layers**
    - the **output layer** is often left linear for **regression tasks**
    - other tasks (e.g., classification) may require an activation on the output

### a. Building Sequential Models
- keras provides the Sequential API to stack layers in order from input to output:

```
model = keras.Sequential([
    layers.Dense(units=4, activation='relu', input_shape=[2]),
    layers.Dense(units=3, activation='relu'),
    layers.Dense(units=1),
])
```
- hidden layers use **ReLU activations**
- the final layer is linear for regression
- layers must be passed as a **list**
- activations are added using the `activation` argument