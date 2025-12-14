# (3) Interactive Maps

https://www.kaggle.com/code/alexisbcook/interactive-maps

## 1. Introduction
This course introduces **interactive geospatial visualization** using the **folium** library. The skills are applied to explore and analyze **Boston crime data**, allowing users to zoom, pan and interact with maps in a web-based format.

## 2. Your first unteractive map
- an interactive map is created with `folium.Map()`
- key parameters:
    - `location`: initial map center (lat. and long.)
    - `titles`: map style (OpenStreetMap, CartoDB)
    - `zoom_start`: initial zoom level
- the resulting map supports user interaction such as dragging and zooming

## 3. The data
- crime data is loaded into a Pandas DataFrame
- rows with mssing location or district information are removed
- the dataset is filtered to include **major crimes from 2018 onward**
- lat. and long. coordinates are used for mapping incidents

## 4. Plotting points

### a. `folium.Marker`
- individual crime incidents are plotted as markers.
- example focused on **daytime robberies** to reduce visual clutter.
- each marker represents a single event at its geographic location.

### b. `folium.plugins.MarkerCluster`
- marker clustering groups nearby markers together
- improves readability when plotting large numbers of points
- clusters expand into individual markers when zoomed in.

## 5. Bubble maps
- bubble maps use `folium.Circle()` instead of markers
- circle properties (color and size) can represent additional variables.
- example uses color to distinguish robbery times (morning vs afternoon)

## 6. Heatmaps
- created using 'folium.plugins.HeatMap()'
- visualizes **crime density** rather than individual incidents
- hotter colors indivate areas with higher concentrations of crime
- the `radius` parameter controls smoothing of the heatmap.

## 7. Choropleth maps
- choropleth maps shows how crime varies by **police district**
- uses a GeoDataFrame containing district boundaries
- crime counts per district are calculated and matched by index
- `folium.Choroplets()` colors each district based on crime frequency
- includes a legend for interpreting the color scale

