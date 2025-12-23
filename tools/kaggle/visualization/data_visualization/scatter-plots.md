# (4) Scatter Plots

https://www.kaggle.com/code/alexisbcook/scatter-plots

- this tutorial introduces **advanced scatter plots** and shows how they can be used to explore relationships between multiple variables using Seaborn

## 1. Set up the notebook
- as in previous lessons, the notebook begins by importing the standard libraries:
    - **pandas** for data handling,
    - **matplotlib** for visualization setup,
    - **seaborn** for plotting.

## 2. Dataset Overview
- the dataset contains **insurance customer information**, including age, BMI, smoking status, region, and insurance charges
- the goal is to understand why some customers pay higher insurance costs than others

## 3. Basic Scatter Plots
- a simple scatter plot is created using `sns.scatterplot`, with:
    - **BMI** on the x-axis,
    - **insurance charges** on the y-axis.
- this visualization reveals a **positive correlation**: as BMI increases, insurance charges generally increase as well.

## 4. Regression Lines
- to better understand the strength of the relationship, a regression line is added using `sns.regplot`
- this line shows the overall trend and confirms the positive correlation between BMI and insurance costs

## 5. Color-Coded Scatter Plots
- scatter plots can display relationships between three variables by color-coding points:
    - BMI and charges remain on the axes,
    - smoking status is shown using color (`hue`).
- this reveals that smokers pay significantly higher insurance costs than non-smokers, especially as BMI increases

## 6. Multiple Regression Lines
- using `sns.lmplot`, separate regression lines are drawn for smokers and non-smokers
- the smoker line has a much steeper slope, highlighting how smoking dramatically increases insurance charges

## 7. Categorical Scatter Plots
- the tutorial introduces **categorical scatter plots** using `sns.swarmplot`, where:
    - smoking status is shown on the x-axis
    - insurance charges are shown on the y-axis
- this plot clearly shows that:
    - non-smokers generally pay less
    - the highest charges belong to smokers
    - the lowest charges belong to non-smokers

## 8. Key Takeaway
- advanced scatter plots allow you to:
    - analyze relationships between multiple variables,
    - compare groups using color and categories,
    - uncover patterns that are not obvious from summary statistics alone.
- these visualizations are powerful tools for exploratory data analysis.