# (4) Manipulating Geospatial Data

https://www.kaggle.com/code/alexisbcook/manipulating-geospatial-data

## 1. Introduction
This course covers two essential geospatial data manupulations: **geocoding** and **table joins**. These techniques allow you to convert place names into map locations and combine geographic data with additional datasets.

## 2. Geocoding
- **Geocoding** converts place names or addresses into geographic coordinates (lat. and long.)
- uses the **geopy** library with the **Nominatim** geocoder.
- a successful geocode returns:
    - a geographic point (lat., long.)
    - a full address description
- geocoding can be applied to many locations at once DataFrame operations.
- geocoded results are converted into a **GeoDataFrame** with point geometrics and CRS (EPSG 4326)

## 3. Table joins

### a. Attribute joins
- combine datsets by matching values in a shared column.
- performed using `GeoDataFrame.merge()`
- Example: joining European country boundaries with population and GDP statistics.

### b. Spatial joins
- combine GeoDataFrames based on **spatial relationships** between geometries
- performed using `gdp.sjoin()`
- Example: assigning universities (points) to the countries (polygones) they fall within
- Only geometrics that satisfy the spatial condition are included.
- join behavior can be customized (left or right joins)