# (2) Coordinate Reference Systems

https://www.kaggle.com/code/alexisbcook/coordinate-reference-systems

## 1. Introduction
Because Earth is a 3D globe, maps require **map projections** to display locations on a flat surface.

All projections introduce destortion but preserve certain properties:
- **Equal-area projections** preserve area (useful for size comparisons)
- **Equidistant projections** preserve distance (useful for measuring travel)
- Some projections (like Mercator) preserve angles but distort area.

A **Coordinate Reference System (CRS)** defines how map coordinates correspond to real locations on Earth.

This tutorial explains how CRS works and how to manage it in GeoPandas. 

## 2. Setting the CRS
- When loading a **shapefile**, the CRS is automatically included.
- CRS are commonly identified using **EPSG codes**
- Example: Ghana region data uses **EPSG 32630** (UTM Zone 30N / Mercator-like projection)
    - Latitude/longitude data uses **EPSG 4326**
    - Points are created using `gdp.points_from_xy()`

## 3. Re-projecting
- **Re-projecting** means changing the CRS of a GeoDataFrame
- Done using the `to_crs()` method
- All layers must share the **same CRS** to plot correctly together.
- Re-projecting only changes the **geometru column**, not the original latitude/longitude values.
- If an EPSG code is unavailable, CRS can be set using a **proj4 string**.

## 4. Attributes of geometric objects

GeoPandas geometry types include:
- **Point** (e.g., health facilities)
- **LineString** (e.g., roads or trails)
- **Polygon** (e.g., region boundaries)

Each geometry type has useful attributes:
- Points → `x`, `y`
- LineStrings → `length`
- Polygons → `area`

Area calculations depend on the CRS:
- Using a Mercator-style projection introduces slight inaccuracies.
- Equal-area projections give more precise results.
- Example: Ghana’s total area is estimated at ~239,585 km², close to the true value.
