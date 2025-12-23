# (8) Creating Your Own Notebooks

https://www.kaggle.com/code/alexisbcook/creating-your-own-notebooks

## 1. Kaggle Notebooks Workflow
- Navigate to Kaggle Notebooks (https://www.kaggle.com/code)
- click [+ New Notebook] to start a new notebook

## 2. Notebook Setup
- check the **language** (File → Language) and set to **Python** if needed
- remove default code and add the standard setup code for Python data visualization:
```
import pandas as pd
pd.plotting.register_matplotlib_converters()
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
print("Setup Complete")
```

## 3. Working with Data
- **attach a dataset** (from Kaggle Datasets or your own upload)
- write code to **generate visualizations** using tools like Seaborn and Matplotlib

## 4. Saving Visualizations
- after creating a figure, **save it as an image** to include in presentations or reports