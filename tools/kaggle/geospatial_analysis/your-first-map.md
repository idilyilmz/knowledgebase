# (1) Your First Map

https://www.kaggle.com/code/alexisbcook/your-first-map

## 1. Introduction
The micro-course introduces **geospatial data wrangling and visualization** using real-worls examples, such as conservation planning, wildlife migration, disaster preparedness, business expansion and public health access.

The goal is to learn how to load, filter, analyze and visualize geographic data to answer location-based questions.

## 2. Reading data
- uses the **GeoPandas** library to work with geospatial data.
- supports common formats like **shapefiles**, **GeoJSON**, **KML** and **GPKG**
- demonstrates loading a New York State DEC lands shapefile with `gpd.read_file()`
- the data includes forests, wilderness areas and other protected lands, each represented as geometric shapes (mostly polygons)

## 3. Prerequisites
- GeoPandas objects are **GeoDataFrames**, which behave like Pandas DataFrames.
- Standard pandas operations work:
    - `head()` to preview data
    - Column selection with `loc`
    - `value_counts()` to summarize categories
    - Filtering with `isin()`
- example: selecting only **WILD FOREST** and **WILDERNESS** land types for analysis.

## 4. Create your first map!
- Each GeoDataFrame contains a special `geometry` **column** (Points, LineStrings, or Polygons).
- The `plot()` method visualizes geographic data directly.
- Multiple layers can be combined on one map using a shared `ax`:
    - County boundaries (base map)
    - Wild lands (polygons)
    - Campsites (points)
    - Foot trails (lines)
- The final layered map helps identify suitable camping regions, highlighting northeastern New York as a strong option.
