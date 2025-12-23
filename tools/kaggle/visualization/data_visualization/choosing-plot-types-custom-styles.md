# (6) Choosing Plot Types and Custom Styles

https://www.kaggle.com/code/alexisbcook/choosing-plot-types-and-custom-styles

## 1. What have you learned?

Charts are grouped into three **main categories** based on the story they help tell:

### a. Trends
- show patterns of change over time
- line charts: sns.lineplot — good for showing trends, multiple lines for multiple groups.

### b. Relationships
- explore relationships between variables
- **bar charts**: `sns.barplot` — compare quantities across groups
- **heatmaps**: `sns.heatmap` — find color-coded patterns in tables
- **scatter plots**: `sns.scatterplot` — relationship between two continuous variables; color can show a third categorical variable
- **regression plots**: `sns.regplot`, `sns.lmplot` — add regression lines to scatter plots, handle multiple groups
- **categorical scatter plots**: `sns.swarmplot` — continuous vs. categorical variable

### c. Distributions
- how the range of values and their likelihood
- **histograms**: `sns.histplot` — distribution of a single numerical variable
- **KDE plots**: `sns.kdeplot` — smooth estimated distributions (1D or 2D)
- **joint plots**: `sns.jointplot` — combine 2D KDE with individual KDEs for each variable

## 2. Changing styles with seaborn
- default plots have a clean style, but themes can be changed with a single line:
```
sns.set_style("dark")
```
- available themes: `"darkgrid"`, `"whitegrid"`, `"dark"`, `"white"`, `"ticks"`
- example with line chart:
```
sns.set_style("dark")
sns.lineplot(data=spotify_data)
```