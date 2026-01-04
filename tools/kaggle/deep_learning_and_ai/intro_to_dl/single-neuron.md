# (1) A Single Neuron

https://www.kaggle.com/code/ryanholbrook/a-single-neuron

## 1. Welcome to Deep Learning (DL)!

- the course introduces deep learning using **Keras** and **TensorFlow**
- you’ll learn 
    - how to build neural networks
    - apply them to **regression** and **classification**
    - train them using **stochastic gradient descent**
    - improve performance with techniques like **dropout** and **batch normalization**

## 2. What is DL?

- deep learning is a branch of machine learning that uses **deep stacks of computations** to model complex, hierarchical patterns in data
- it has powered major advances in areas like **image recognition**, **language translation**, and **game playing**
- neural networks are the core models behind deep learning, gaining power from how many simple neurons are connected together

## 3. The Linear Unit
- a linear unit (neuron) is the basic building block of a neural network.
- it computes an output using the formula:

$$
y=wx+b
$$

- x: input
- w (or a): weight (learned during training)
- b: bias (allows shifting the output independently of inputs)
- y: output

this equation is the same as the slope-intercept form of a line, making a single neuron a linear model

## 4. Example - The Linear Unit as a Model
- a single neuron can be used as a simple predictive model.
- for example, predicting cereal calories from sugar content:
    - weight 𝑤 = 2.5
    - bias 𝑏 = 90

if sugar = 5 grams:

$$
𝑐𝑎𝑙𝑜𝑟𝑖𝑒𝑠 = 2.5 × 5 + 90 = 102.5
$$

this shows how a linear unit models relationships in real-world data

## 5. Multiple Inputs
- a neuron can accept **multiple inputs**, each with its own weight
- the formula becomes:

$$
y = w_0 x_0 + w_1 x_1 + w_2 x_2 + b
$$

- one input → fits a **line**
- two inputs → fits a **plane**
- many inputs → fits a **hyperplane**

this allows the model to use multiple features (e.g., sugar, fiber, protein).

## 6. Linear Units in Keras
- in Keras, a linear model is created using a Dense layer inside a Sequential model:
```
model = keras.Sequential([
    layers.Dense(units=1, input_shape=[3])
])
```
- `units=1`: one output (e.g., calories)
- `input_shape=[3]`: three input features

Keras uses a list for `input_shape` to support more complex data types, like images with multiple dimensions