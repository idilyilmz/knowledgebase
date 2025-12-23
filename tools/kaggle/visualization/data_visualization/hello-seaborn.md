# (1) Hello, Seaborn

https://www.kaggle.com/code/alexisbcook/hello-seaborn

## 1. Welcome to Data Visualization
- this lesson introduces **data visualization using Seaborn**, a Python library that makes creating attractive and informative charts fast and easy
- the course is designed for **beginners with no prior programming experience**, using short and simple code to produce professional-quality visualizations more efficiently than tools like Excel

## 2. Your coding environment
- the course uses **Jupyter notebooks**, which combine:
    - **text** (explanations),
    - **code cells** (Python code in gray boxes),
    - **output** (results shown below code).
- initially, the notebooks come with pre-run code, but later lessons will let you write and run your own code.

## 3. Set up the notebook
- each notebook begins with setup code that imports common libraries:
    - **pandas** for data handling,
    - **matplotlib** and **seaborn** for visualization.
- you don’t need to understand this setup yet, just know it prepares the environment for plotting.

## 4. Load the data
- the lesson works with a **CSV file containing historical FIFA rankings** for six countries (Argentina, Brazil, Spain, France, Germany, and Italy)
- the data is loaded using `pandas.read_csv`, specifying:
    - the file location,
    - a date column as the index,
    - automatic date parsing.
- comments (`#`) are used to explain code and are ignored when the code runs.

## 5. Examine the data
To confirm the data loaded correctly, the `.head()` method is used to display the first five rows of the dataset. This helps verify the structure and contents before plotting.

## 6. Plot the data
With just a few lines of code, a **line chart** is created using Seaborn to show how FIFA rankings change over time. While the code details aren’t explained yet, this example gives a preview of how quickly meaningful visualizations can be made.

## 7. Takeaways
- this lesson sets the foundation for the course by:
    - introducing Seaborn and Python,
    - explaining how to work in Jupyter notebooks,
    - showing how to load, inspect, and visualize data.
- next, you’ll start hands-on exercises to practice using the coding environment yourself.