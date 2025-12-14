# (4) Clustering With K-Means

https://www.kaggle.com/code/ryanholbrook/clustering-with-k-means

## 1. Introduction
- this lesson introduces **unsupervised learning**, where models learn patterns from data **without a target variable**
- unsupervised algorithms are often used for **feature discovery**, helping reveal structure within the data
- **Clustering** groups data points based on similarity ("birds of a feather flock together")
- in feature engineering, clustering can identify meaningful groups such as market segments or geographic regions
- cluster labels can be added as features to help models learn complex relationships more efficiently

## 2. Cluster Labels as a Feature
- cluster labels represent group membership and act as a **categorical feature**
- for a single feature, clustering behaves like **binning or discretization**
- for multiple features, clustering performs **multi-dimensional binning** (vector quantization)
- cluster labels are usually integer-encoded but may require **one-hot encoding** depending on the model
- adding cluster labels simplifies complex relationships, allowing models to learn patterns using a **divide-and-conquer** approach
- clustering can help linear models approx. non-linear relationships by learning them in smaller segments.

## 3. k-Means Clustering
- **k-means** is a popular clustering algorithm that measures similarity using **Euclidean distance**
- the algorithm creates **k centroids**, where each data point is assigned to its nearest centroid
- the resulting partition of space is called a **Voronoi tesselation**, which determines cluster boundaries
- k-means works through an iterative two-step process:
    1. assign points to the nearest centroid
    2. update centroids to minimize within-cluster distance
- key parameters
    - `n_clusters`: number of clusters (k)
    - `max_iter`: maximum iterations for convergence 
    - `n_init`: number of random initializations to find the best solution
- choosing the best value for k depends on the model and task and should be treated as a **hyperparameter**

## 4. Example - California Housing
- lat. and long. are natural inputs for clustering spatial data
- median income (`MedInc`) is added to form **economic-geographic segments**
- k-means is applied with `n_clusters=6` to create a new **Cluster** feature
- cluster labels are stored as a categorical variable in tje dataset
- visualizations show:
    - distinct geographic regions (like, coastal vs. inland areas)
    - clear seperation in median houde values across clusters
- this demonstrates how clustering can create informative features that improve predictive modeling