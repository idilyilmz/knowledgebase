# (2) Convolution and ReLU

https://www.kaggle.com/code/ryanholbrook/convolution-and-relu

## 1. Introduction
- this lesson focuses on one of the core building blocks of convolutional neural networks: the convolutional layer with ReLU activation
- it explains how the convolutional base of a CNN extracts visual features from images using convolution, activation, and pooling operations

## 2. Feature Extraction
- feature extraction in a convnet consists of three main steps:
    1. **convolution** – filters the image to highlight specific patterns.
    2. **ReLU activation** – detects and emphasizes important features.
    3. **max pooling** – condenses feature maps to make features more prominent (covered later).
- these steps allow the network to isolate meaningful visual characteristics such as edges, lines, and textures.

## 3. Filter with Convolution
a convolutional layer applies learnable filters (kernels) across an image to produce feature maps

### a. Weights
- the weights of a convolutional layer are called **kernels**
- kernels are small matrices (e.g., 3×3) that slide over the image and compute weighted sums of pixel values
- each kernel learns to detect a specific visual pattern, such as edges or horizontal lines
- the kernel size determines how input pixels connect to output neurons

### b. Activations
- the outputs of convolution are called **feature maps**
- each feature map highlights where a particular pattern appears in the image
- the number of feature maps is controlled by the `filters` parameter of the convolutional layer

## 4. Detect with ReLU
- after convolution, feature maps pass through the **ReLU (Rectified Linear Unit)** activation function
- ReLU sets all negative values to zero, keeping only important positive responses
- this helps isolate features and introduces nonlinearity, allowing features to combine and become more complex in deeper layers

## 5. Example - Apply Convolution and ReLU
- an example demonstrates applying a manually defined edge-detection kernel to an image using TensorFlow’s `conv2d` function, followed by `relu`
- the result is a feature map that highlights edges in the image, showing how convolution and ReLU work together to extract useful visual information

## 6. Conclusion
- this lesson explains the first two steps of feature extraction in a CNN: filtering images with convolutional layers and detecting features using ReLU activation
- these operations form the foundation of how convnets learn visual patterns
