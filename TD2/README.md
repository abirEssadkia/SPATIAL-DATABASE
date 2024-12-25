TD2: Creating Spatial Tables
This tutorial demonstrates how to create spatial tables in a PostgreSQL database with PostGIS enabled. Spatial tables are essential for storing and managing geographic data, including points, polygons, and lines.

Prerequisites
A PostgreSQL database with the PostGIS extension installed (refer to TD1 if assistance is needed).
Installed tools:
pgAdmin: For database management.
QGIS: For data visualization and editing.
Steps to Follow
1. Creating a Spatial Table (Points)
Open pgAdmin 4 and connect to your PostgreSQL server.
Use the Query Tool in your spatial database and run the following SQL command:
sql
Copier le code
CREATE TABLE points_of_interests (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    geom GEOMETRY(Point, 4326)
);
Table Description:

id: A unique identifier for each entry.
name: The name of the point of interest.
geom: A geometry column for storing point data using the EPSG:4326 coordinate system.
2. Adding Data Using QGIS
Launch QGIS and connect to your PostgreSQL database:

Right-click on PostgreSQL in the Browser panel and select New Connection.
Enter your database details (host, port, database name, username, password).
Test the connection, then click OK.
Locate the points_of_interests table and add it as a layer.

Switch to Edit Mode to start adding points.

Use the map interface to place points and save your changes.

3. Verifying Data in pgAdmin
Open pgAdmin and execute this query to review the data:
sql
Copier le code
SELECT * FROM points_of_interests;
You will see a list of points added via QGIS.

4. Creating a Spatial Table (Polygons)
For polygons, execute the following SQL command in pgAdmin:
sql
Copier le code
CREATE TABLE protected_areas (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    geom GEOMETRY(Polygon, 4326)
);
Use QGIS to populate this table following the same steps as with points.
5. Creating a Spatial Table (Linestrings)
For line geometries (e.g., roads), execute this SQL command:
sql
Copier le code
CREATE TABLE roads (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    geom GEOMETRY(LINESTRING, 4326)
);
Populate and verify the data using the same steps described above.
Next Steps
Now that you can create and populate spatial tables, proceed to the next tutorial (TD3) to explore spatial SQL functions for advanced data analysis.

Resources
PostGIS Documentation
QGIS Documentation
Feel free to experiment further with spatial data types and explore the rich functionalities of PostGIS!
