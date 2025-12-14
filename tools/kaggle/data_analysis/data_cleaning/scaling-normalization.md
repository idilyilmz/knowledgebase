# (2) Scaling and Normalization

https://www.kaggle.com/code/alexisbcook/scaling-and-normalization

## 1. Get our environment set up
- import common data science library:
    - `pandas`, `numpy` for data handling
    - `scipy.stats` for statistical transformations (Box-Cox)
    - `mlxtend.preprocessing.minmax_scaling` for scaling
    - `seaborn`, `matplotlib` for visualization
- set a random seed for reproducibility

## 2. Scaling vs. Normalization: What's the difference?
- both techniques transform **numeric data**, but they serve different purposes:
    - **scaling** → change the **range** of the data
    - **normalization** → changes the **shape** of the data distribution
- they are often confused because both modify values, but they are used for different types of models

## 3. Scaling
- scaling transforms values to fit within a specific range (commonly **0 to 1**)
- the **shape of the distribution stays the same**
- useful for models that rely on distances between data points.
    - K-Nearest Neighbors (KNN)
    - Support Vector Machines (SVM)

### a. why scaling matters
- without shaling, features with larger units (like Yen vs Dollars or weight vs height) dominance distance-based models.
- scaling puts all numeric features on **equal footing**

### b. example
- min-max scaling rescales data so:
$$
x_{\text{scaled}} = \frac{x - \min(x)}{\max(x) - \min(x)}
$$
- original data might rnage from 0-8, but after scaling it ranges from 0-1.
- **Distribution shape does not change**

## 4. Normalization
- normalization changes data so it follows a **normal (Gaussian) distribution**
- a normal distribution
    - is bell-shaped
    - has mean approx. median
    - has more values near the center

### a. When to normalize
- when using models that **assume normality**, such as:
    - Linear Discriminant Analysis (LDA)
    - Gaussian Naive Bayes

### b. Box-con transformation
- a common normalization technique
- changes the **shape** of the data distribution
- can turn skewed (like, exponential or L-shaped) data into a bell curve

## 5. Key takeaways
- **scaling** = change the range, keep the shape
- **normalization** = change the shape, aim for a normal distribution
- choose the method based on the **assumptions of your model**, not at random