TD1: Getting Started with Spatial SQL
This guide provides a detailed walkthrough for installing PostGIS and setting up your first spatial database. PostGIS is a powerful spatial database extender for PostgreSQL, enabling advanced GIS operations within a relational database system.

Prerequisites
PostgreSQL installed on your system.
Internet access to download necessary extensions and tools.
Steps to Follow
1. Install PostgreSQL
Visit the PostgreSQL Downloads Page and download the appropriate version for your operating system (Windows, macOS, or Linux).
Follow the installation guide and set up PostgreSQL on your system.
During the installation, set a password for the postgres user.
2. Install PostGIS
During the PostgreSQL installation, ensure you select all components, including the Stack Builder tool.
Launch the Stack Builder and select the PostgreSQL version you installed.
In the application selection list, choose PostGIS.
Complete the installation following the prompts.
3. Create Your First Spatial Database
Open pgAdmin 4, the PostgreSQL database management tool.

Connect to the PostgreSQL server using the credentials set during installation.

Right-click on Databases and select Create > Database.

Provide a name for your database (e.g., spatial_db) and save it.

Open the Query Tool for your database and run the following command to enable PostGIS:

CREATE EXTENSION postgis;
Verify the installation by checking for the spatial_ref_sys table under Schemas > Public > Tables.

Next Steps
Once your spatial database is set up, you can move on to creating tables with spatial columns and performing GIS operations using SQL. Check out TD2 for more information on creating spatial tables.

Resources
PostGIS Documentation
PostgreSQL Documentation
Feel free to reach out if you encounter any issues or need further assistance!
