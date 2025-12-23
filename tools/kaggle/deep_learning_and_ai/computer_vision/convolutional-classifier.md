# (1) The Convolutional Classifier

https://www.kaggle.com/code/ryanholbrook/the-convolutional-classifier

## 1. Welcome to Computer Vision!
- this course teaches how to make computers “see” using deep learning
- you’ll build image classifiers with Keras, design custom convolutional networks, learn feature extraction, apply transfer learning, and use data augmentation
- prior knowledge from an introductory deep learning course is sufficient

## 2. Introduction
- the course introduces core computer vision concepts, focusing on how neural networks interpret images
- Convolutional Neural Networks (CNNs or convnets) are highlighted as the most effective models for vision tasks
- while the main application is image classification, the concepts apply broadly to other vision problems like segmentation and GANs

## 3. The Convolutional Classifier
- a convolutional classifier has two main parts:
    - **convolutional base**: extracts visual features (edges, textures, shapes, patterns) from images using convolution layers
    - **dense head**: uses these extracted features to classify the image
- this separation allows the model to learn feature extraction and classification jointly

## 4. Training the Classifier
- training involves learning:
    1. which visual features to extract (base)
    2. how to map features to classes (head)
- instead of training from scratch, models typically reuse a pretrained base (e.g., trained on ImageNet) and attach a new head
- this approach, called transfer learning, enables strong performance with relatively small datasets

## 5. Example - Train a Convnet Classifier
the example task is classifying images as **Car** or **Truck** using ~10,000 labeled images

### a. Step 1 - Load Data
images are loaded into training and validation datasets using TensorFlow utilities, resized, normalized, cached, and prefetched for efficient training

### b. Step 2 - Define Pretrained Base
a pretrained **VGG16** model (trained on ImageNet) is used as the convolutional base and frozen so its weights are not updated during training

### c. Step 3 - Attach Head
- a classifier head is added on top of the base, consisting of:
    - a flatten layer
    - a small dense hidden layer
    - a final dense layer with sigmoid activation for binary classification

### d. Step 4 - Train
- the model is compiled using the Adam optimizer, binary crossentropy loss, and binary accuracy metric, then trained for multiple epochs
- training and validation performance are visualized using loss and accuracy plots

## 6. Conclusion
- the lesson explains how convolutional classifiers combine automatic feature extraction with traditional classification layers
- this integration is a key advantage of deep learning over classical machine learning
- future lessons will explore how convolutional bases work internally and how to design custom classifiers