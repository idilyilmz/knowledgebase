# (4) The Sliding Window

https://www.kaggle.com/code/ryanholbrook/the-sliding-window

## 1. Introduction

- convolutional and pooling layers both perform feature extraction using a **sliding window**.
    - in **convolution**, the window is the **kernel** (`kernel_size`).
    - in **pooling**, it is the **pooling window** (`pool_size`).

- two key parameters affect how this window moves and interacts with the image:
    - **Stride**
    - **Padding**

- these parameters control how much information is captured and how feature maps are sized.

## 2. Stride

- **stride** is the number of pixels the window moves at each step (horizontally and vertically).
    - larger strides **skip pixels**, reducing detail.
    - **convolution layers** usually use `stride = 1` to preserve high-quality features.
    - **pooling layers** often use larger strides (e.g., 2 or 3) to reduce spatial size.
    - if strides are equal in both directions, a single value can be used (e.g., `stride=2`).

- larger strides can speed up computation but may lose important information

## 3. Padding

- **padding** determines how the sliding window handles image boundaries.
    - `padding='valid'`
        - no padding added.
        - output size shrinks.
        - can limit network depth, especially with small inputs.

    - `padding='same'`
        - zero-padding added around the image.
        - output size matches input size.
        - slightly weakens edge pixel influence.

- most modern CNNs (e.g., VGG) use **same padding** for convolution layers, though a mix of both is common

## 4. Example - Exploring Sliding Windows

- a low-resolution image (a simple circle) is used to visualize feature extraction.
    - a Sobel kernel detects horizontal edges.
    - with **stride = 1**, features are captured clearly.
    - increasing convolution stride to **3** reduces feature quality because fine details are skipped.
    - some models (e.g., **ResNet50**) use large kernels and larger strides in early layers to quickly extract large-scale features without losing too much information

## 5. Conclusion

- the sliding window is a core mechanism in CNNs
- **stride** controls how much detail is captured, while **padding** controls feature map size and edge handling
- together, these parameters strongly influence feature quality, model depth, and performance