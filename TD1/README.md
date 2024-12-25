TD1: Getting Started with Spatial SQL
This tutorial provides a step-by-step guide for installing PostGIS and setting up your first spatial database. PostGIS is a powerful extension for PostgreSQL that enables advanced GIS functionalities within a relational database system.

Prerequisites
PostgreSQL installed on your system.
Internet access to download the necessary extensions and tools.
Steps to Follow
1. Install PostgreSQL
Visit the PostgreSQL Downloads Page and download the version suitable for your operating system (Windows, macOS, or Linux).
Follow the installation guide to set up PostgreSQL on your system.
During installation, ensure you set a password for the postgres user (default superuser).
2. Install PostGIS
During the PostgreSQL installation, select all components, including the Stack Builder tool.
After installation, launch the Stack Builder and choose the PostgreSQL version installed on your system.
In the list of available applications, select PostGIS and proceed with the installation.
3. Create Your First Spatial Database
Using pgAdmin 4
Launch pgAdmin 4, the database management tool.
Connect to your PostgreSQL server with the credentials set during installation.
Right-click on Databases and select Create > Database.
Provide a name for your new database (e.g., spatial_db) and save it.
Enable PostGIS Extension
Open the Query Tool in pgAdmin for your newly created database.

Run the following SQL command to enable the PostGIS extension:

sql
Copier le code
CREATE EXTENSION postgis;
Verify the installation by checking for the spatial_ref_sys table under Schemas > Public > Tables in the database tree.

Next Steps
With your spatial database set up, you are ready to create tables with spatial columns and perform GIS operations using SQL. Proceed to TD2 for guidance on building spatial tables.

Resources
PostGIS Documentation
PostgreSQL Documentation
Feel free to explore and experiment with PostGIS capabilities or reach out if you need additional support!
