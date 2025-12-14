# (5) Proximity Analysis

https://www.kaggle.com/code/alexisbcook/proximity-analysis

## 1. Introduction
This course introduces **proximity analysis** in geospatial data. The focus is on measuring distances between geographic features and identifying points that fall within a specified radius. The examples use EPA toxic release data and air quality monitoring stations in Philadelphia.

## 2. Measuring distance
- distance calculations require all GeoDataFrames to use the **same CRS**.
- the datasets use **EPSG 2272**, which measures distance in **feet**.
- GeoPandas computes distances using the `geometry.distance()` method
- distance analysis can be used to:
    - calculate average distances
    - identify the nearest feature (like, closesr ninitoring station)
    - compare proximity across multiple locations

## 3. Creating a buffer
- a **buffer** represents all points within a fixed distance of a feature.
- buffers are created with `geometry.buffer()`
- example: a 2-mile buffer around each air monitoring station.
- multiple buffers can be combined into a single **MultiPolygon** using `unary_union`
- the `contains()` method checks whether a point lies inside the buffer area.
- buffers and resulrs can be visualized with **Folium**, after converting to lat/long (EPSG 4326).