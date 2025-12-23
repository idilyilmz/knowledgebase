# (5) Distributions

https://www.kaggle.com/code/alexisbcook/distributions

## 1. Set up the Notebook
- import `pandas`, `matplotlib.pyplot`, and `seaborn`.
- enable inline plotting in Jupyter notebooks.
- example:
```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

## 2. Select a Dataset
- iris dataset: 150 flowers, 50 each of **Iris setosa**, **Iris versicolor**, **Iris virginica**.
- columns: `Sepal Length`, `Sepal Width`, `Petal Length`, `Petal Width`, `Species`.

## 3. Load and Examine the Data
```
iris_data = pd.read_csv("../input/iris.csv", index_col="Id")
iris_data.head()
```
## 4. Historgrams
- show distribution of a single variable
- example: Petal length:
```
sns.histplot(iris_data['Petal Length (cm)'])
```

## 5. Density (KDE) Plots
- smoothed version of histograms.
- example:
```
sns.kdeplot(data=iris_data['Petal Length (cm)'], fill=True)
```

## 6. 2D KDE plots
- show relationships between two variables with density
- example:
```
sns.jointplot(
    x=iris_data['Petal Length (cm)'],
    y=iris_data['Sepal Width (cm)'],
    kind="kde"
)
```

## 7. Color-coded plots
- compare distributions across species using `hue`
- **histograms by species**:
```
sns.histplot(data=iris_data, x='Petal Length (cm)', hue='Species')
plt.title("Histogram of Petal Lengths, by Species")
```
- **KDE plots by species**:
```
sns.kdeplot(data=iris_data, x='Petal Length (cm)', hue='Species', fill=True)
plt.title("Distribution of Petal Lengths, by Species")
```
- observations:
    - **iris setosa** has shorter petal lengths (<2 cm), easily distinguishable
    - **iris versicolor** and **Iris virginica** overlap more