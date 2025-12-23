# (6) Data Augmentation

https://www.kaggle.com/code/ryanholbrook/data-augmentation

## 1. Introduction
- after learning the basics of convolutional classifiers, this lesson introduces data augmentation, a technique used to improve model performance by artificially increasing training data

## 2. The Usefulness of Fake Data
- models generally perform better with **more training data**
- data augmentation creates **new training examples** by transforming existing images in ways that **do not change the class**
- example: flipping a car image left or right doesn’t change it from “car” to “truck”
- by seeing these variations, the model learns to **ignore irrelevant differences** and generalize better

## 3. Using Data Augmentation
- common transformations include:
    - flipping
    - rotation
    - color and contrast adjustments
    - warping and scaling
- augmentation is usually done **online during training**, not beforehand.
- each time an image is used, a **random transformation** is applied.
- this adds variability and reduces overfitting.
- important rule: transformations **must not mix up classes** (e.g., rotating digits could confuse 6 and 9).

## 4. Example - Training with Data Augmentation
- keras supports augmentation via:
    - data pipelines (e.g., `ImageDataGenerator`)
    - **preprocessing layers inside the model** (used here)
- preprocessing layers run on the **GPU**, which can speed up training
- simple augmentations added:
    - Random horizontal flip
    - Random contrast adjustment
- A **pretrained VGG16 base** is frozen and used for feature extraction, followed by a classifier head

## 5. Results
- compared to the non-augmented model:
    - training and validation curves stayed closer together
    - validation loss and accuracy improved slightly
- this indicates **reduced overfitting** and better generalization.

## 6. Conclusion
- data augmentation improves image classifiers by exposing them to realistic variations of existing data
- when chosen carefully, it acts as a powerful form of regularization and leads to better performance on unseen data