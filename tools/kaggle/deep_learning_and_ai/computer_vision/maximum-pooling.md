# (3) Maximum Pooling

https://www.kaggle.com/code/ryanholbrook/maximum-pooling

## 1. Introduction

- this lesson completes the feature extraction process in a convolutional neural network by introducing **maximum pooling**
- after convolution and ReLU activation, maximum pooling condenses feature maps to make them more efficient and informative

## 2. Condense with Maximum Pooling

- a MaxPool2D layer reduces the size of feature maps by replacing small patches of activations with their maximum value
- unlike convolutional layers, max pooling has no trainable weights
- its purpose is to remove unnecessary “dead space” (zeros from ReLU) while preserving the most important parts of a feature, effectively intensifying detected patterns

## 3. Example - Apply Maximum Pooling

- an example demonstrates applying max pooling after convolution and ReLU using TensorFlow functions
- pooling with a 2×2 window condenses the feature map, highlighting strong activations while reducing spatial dimensions
- this shows how pooling sharpens and simplifies features extracted earlier in the network

## 4. Translation Invariance

- by reducing positional information, max pooling gives convnets **translation invariance**, the ability to recognize features even when they appear in slightly different locations
- while some spatial detail is lost, important features remain detectable over small shifts
- this property improves classification robustness and reduces the amount of training data needed

## 5. Conclusion

- this lesson explains the final step of feature extraction: condensing feature maps using MaxPool2D
- maximum pooling improves efficiency, intensifies features, and introduces translation invariance
- the next lesson continues exploring convolution and pooling using sliding windows.