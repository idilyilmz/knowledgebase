# (5) Principal Component Analysis

https://www.kaggle.com/code/ryanholbrook/principal-component-analysis

## 1. Introduction
- this lesson introduces **Principal Component Analysis (PCA)** as a model-based feature engineering technique
- while clustering partitions data points, **PCA partitions the variation in the data**
- PCA helps uncover important relationships and can create more informative features
- PCA is typically applied to **standardized data**, where variation corresponds to correlation

## 2. Principal Component Analysis
- PCA replaces original features with new features called **principal components**, which represent the main axes of variation in the data.
- each component is a **linear combination** of the original features, defined by weights called **loadings**
- components are orthogonal (uncorrelated) and ordered by how much variance they explain
- the first component explains the most variation, the second explains the next most and so on
- the number of components equals the number of original features
- loading indicate
    - **magnitude** → how much a feature contributes
    - **sign** → whether features vary together or in opposition
- explained variance shows how much information each component captures, through higher variance does not always mean better predictive power

## 3. PCA for Feature Engineering
PCA can be used in two main ways.

### a. descriptive analysis
- analyze components to understand what types of variation are predictive
- use MI scores to identify important components
- inspire new feature creation (like, ratios, products or clustering on components)

### b. using components as features
- **Dimensionality reduction**: remove redundant or near-zero variance components.
- **Anomaly detection**: unusual patterns often appear in low-variance components.
- **Noise reduction**: seperate signal from shared background noise.
- **Decorrelation**: transform correlated features into uncorrelated components for better model perfomance.

### c. best practices
- PCA works only with **numeric features**
- always **standardize** data unless there's a strong reason not to
- handle outliers carefully, as they can distort components

## 4. Example - 1985 Automobiles
- PCA is applied to four standardized deatures: highway_mpg, engine_size, horsepower and curb_weight
- the first principal component (PC1) captures a **Luxury vs. Economy** axis
    - large, powerful, low-MPG cars vs. smaller, fuel-efficient cars.
- PC1 explains most of the variance and has the highest mutual information with price
- lower-variance components (like, PC3) still reveal meaningful patterns, such as **sports cars vs. wagons**
- PCA insights inspire new features, like a **curb_weight / horsepower** ratio, which shows a strong relationship with price
