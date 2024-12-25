TD3: Spatial SQL Functions
This tutorial focuses on advanced spatial SQL functions in PostGIS for analyzing and manipulating spatial data. You'll learn how to perform proximity analysis, calculate areas, and create insightful spatial queries.

Prerequisites
A PostgreSQL database with PostGIS installed and configured (refer to TD1).
Spatial tables populated with relevant geometry data (refer to TD2).
Objectives
Count the number of parcels within a 1 km radius of specific fire points.
Calculate the total area of parcels near the fire points.
Steps to Follow
1. Download and Import the Parcels Shapefile
Download the Shapefile: Obtain the parcels shapefile from the provided link.
Import the Shapefile into PostGIS:
Launch the PostGIS Shapefile Import/Export Manager (on Windows, search for "Shapefile Import" in the Start menu).
Select the downloaded shapefile.
Choose the target database and schema.
Click Import to load the shapefile into your database.
Verify the parcels table in your database under Schemas > Public > Tables.
2. Count Parcels within 1 km Radius
Use the following SQL query to count parcels within 1 km of specified fire points:

sql
Copier le code
SELECT count(*)
FROM "public"."parcels"
WHERE ST_DWithin(
    geom, 
    (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 
    1000
) OR ST_DWithin(
    geom, 
    (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 
    1000
);
Explanation:

ST_DWithin: Finds geometries within a specified distance.
The fire points are represented by the centroids of parcels with gid = 462273 and gid = 460957.
Result:
The query outputs the count of parcels within the 1 km radius (e.g., 472 parcels).

3. Calculate Total Area of Parcels
To calculate the total area of parcels within the same radius, run this query:

sql
Copier le code
SELECT SUM(shape_area)
FROM "public"."parcels"
WHERE ST_DWithin(
    geom, 
    (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 
    1000
) OR ST_DWithin(
    geom, 
    (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 
    1000
);
Explanation:

SUM(shape_area): Sums the area of the parcels.
Result:
The total area of parcels within the radius (e.g., 5,192,474.35 square units).

Additional Notes
Visualization in QGIS
Duplicate the parcels layer in QGIS:
Right-click the layer and select Duplicate.
Apply a filter to isolate parcels within the 1 km radius using SQL logic:
sql
Copier le code
ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000)
OR
ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 1000)
Steps:

Right-click the duplicated layer and select Filter.
Paste the SQL filter expression.
Click Apply to view filtered parcels.
Customize symbology to highlight risk zones:

Double-click the layer and apply styles like color coding.
Expanding Analysis
Add more fire points: Include their centroids in the ST_DWithin clause.
Adjust the radius: Modify the value in ST_DWithin (e.g., 500m or 2km).
Advanced functions: Use ST_Intersection to find overlapping areas from multiple fire points.
Example query for detailed statistics:

sql
Copier le code
SELECT AVG(shape_area) AS avg_area, MAX(shape_area) AS max_area
FROM "public"."parcels"
WHERE ST_DWithin(
    geom, 
    (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 
    1000
) OR ST_DWithin(
    geom, 
    (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 
    1000
);
Resources
PostGIS Documentation
QGIS Documentation
Experiment with spatial queries to deepen your understanding of PostGIS capabilities!
