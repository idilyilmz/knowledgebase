# (3) Bar Charts and Heatmaps

https://www.kaggle.com/code/alexisbcook/bar-charts-and-heatmaps

- this lesson expands on line charts by introducing **bar charts** and **heatmaps**, two powerful visualization types for comparing values and spotting patterns
- the tutorial emphasizes that once you learn the basic structure of Seaborn code, creating new chart types becomes easier and more intuitive with practice

## 1. Set up the notebook
- as in previous lessons, the notebook begins by importing:
    - **pandas** for data handling,
    - **matplotlib** for formatting figures,
    - **seaborn** for plotting,
-  this setup remains consistent across all tutorials

## 2. Select a dataset
- the dataset comes from the **U.S. Department of Transportation** and contains average flight arrival delays (in minutes) for multiple airlines across each month of 2015.
    - rows represent **months**.
    - columns represent **airlines**.
    - negative values indicate flights that arrived early.
    - some values are missing (`NaN`).

## 3. Loading and examining the data
- the data is loaded using `pd.read_csv`, with the *Month* column used as the row index
- since months are not dates, no date parsing is required
- because the dataset is small, the entire table can be printed and inspected at once

## 4. Bar chart
- bar charts are used to compare values across categories
- in the example, a bar chart displays the **average monthly arrival delay for Spirit Airlines (NK)**
- key elements of a bar chart:
    - `sns.barplot` creates the chart,
    - `x=flight_data.index` sets months on the x-axis,
    - `y=flight_data['NK']` sets delay values on the y-axis,
    - titles, axis labels, and figure size are easily customized.
- an important note is that when a column is used as the index, it must be accessed with `.index`.

## 6. Heatmap
- heatmaps visualize large tables by using color to represent values.
    - `sns.heatmap` creates the chart,
    - `data=flight_data` uses the entire dataset,
    - `annot=True` displays numerical values inside each cell.
- heatmaps make it easy to identify trends, such as certain months having consistently lower delays across all airlines

## 7. Takeaway
- this lesson shows how Seaborn can be used to:
    - create bar charts for category comparisons,
    - build heatmaps to reveal patterns across many variables,
    - quickly customize visualizations with minimal code.
- together, bar charts and heatmaps provide powerful tools for exploring and interpreting structured data