# (5) Custom Convnets

https://www.kaggle.com/code/ryanholbrook/custom-convnets

## 1. Introduction
- after learning how individual CNN layers extract features, this lesson shows how to combine them into a full convolutional network (convnet) for image classification

## 2. Simple to Refined Features
- convnets extract features using repeated **filter** → **detect (ReLU)** → **condense (pooling)** operations
- early layers capture **simple features** (edges, lines)
- deeper layers combine these into **more complex** and **refined features**
- repeating this process allows convnets to solve complex classification tasks

## 3. Convolutional Blocks
- feature extraction is organized into **convolutional blocks**
- each block typically contains:
    - `Conv2D` (filtering)
    - ReLU activation (detection)
    - `MaxPool2D` (condensing)
- stacking many blocks allows the network to build increasingly sophisticated representations
- this deep structure is a major reason for CNNs’ strong performance

## 4. Example - Design a Convnet
- a custom CNN is built and trained on a car-vs-truck image dataset.
- **model structure**:
    - **base (feature extractor)**:
        - 3 convolutional blocks
        - filters increase with depth: **32** → **64** → **128**
        - max pooling reduces spatial size after each block
    - **head (classifier)**:
        - flatten layer
        - dense (ReLU)
        - output Dense layer with sigmoid for binary classification
- **key design pattern**:
    - as feature maps shrink via pooling, the **number of filters increases** to maintain expressive power.

## 5. Training
- model is trained using:
    - **adam optimizer**
    - **binary cross-entropy loss**
    - **binary accuracy** metric
- despite being much smaller than VGG16, the model fits the dataset well.
- performance could be improved by adding more convolutional layers.

## 6. Conclusion
- this lesson demonstrates how to build a custom convnet by stacking convolutional blocks and a classifier head, enabling complex feature engineering for image classification tasks