# (2) Line Charts

https://www.kaggle.com/code/alexisbcook/line-charts

- this tutorial teaches the basics of creating **professional-looking line charts** using Seaborn, with minimal Python knowledge required
- it builds on familiarity with the coding environment and prepares you to visualize real-world data

## 1. Set up the notebook
- the notebook begins by setting up the Python environment with common libraries:
    - **pandas** for data handling,
    - **matplotlib** for figure formatting,
    - **seaborn** for plotting.
- this setup is reused in every notebook

## 2. Select a dataset
- the dataset contains **daily global Spotify streaming counts** for five popular songs from 2017–2018:
    - *Shape of You*
    - *Despacito*
    - *Something Just Like This*
    - *HUMBLE.*
    - *Unforgettable*
Some entries contain missing values (`NaN`) because songs were released on different dates.

## 3. Load the data
- the data is loaded from a CSV file using `pd.read_csv`
- to inspect the dataset:
    - `.head()` shows the first five rows,
    - `.tail()` shows the last five rows.
- this helps verify that the data is correctly loaded and structured.

## 4. Examine the data
- a full line chart is created with a single line of code:
```
sns.lineplot(data=spotify_data)
```
- this plots one line per song, showing how streaming counts change over time.

## 5. Plot the data
- additional lines of code allow easy customization:
    - `plt.figure(figsize=(width, height))` sets the chart size,
    - `plt.title("...")` adds a title
- these small changes improve readability and presentation

## 6. Plot a subset of the data
instead of plotting all columns, you can plot selected songs:
- column names are listed using `list(spotify_data.columns)`
- individual lines are added by selecting columns, e.g.:
```
sns.lineplot(data=spotify_data['Shape of You'], label="Shape of You")
```
- labels are added to distinguish lines in the legend
- the x-axis label is set with `plt.xlabel("Date")`

## 7. Key Takeaway
- with just a few lines of code, Seaborn makes it easy to:
    - load and inspect datasets,
    - create line charts,
    - customize titles, sizes, and labels,
    - plot all or selected columns from a dataset,
- these skills form the foundation for more advanced data visualizations later in the course
