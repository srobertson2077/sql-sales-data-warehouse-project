# Create DB and Schemas
---
## MySQL Database
---

The following code creates the schema for our project. Save it with a `.sql` extension on Git Hub. 

The first part of the code should check if the database exist and then drop the database if necessary and the 2nd part creates and initiates the schema. 

<aside>
💡

Remember that the first part of the script should be done if you are certain that you will no longer use the database. 

</aside>

### First Part: Check and drop database

```sql
/*
=============================================================
Create Database and Schemas
=============================================================
Script Purpose:
    This script creates a new database named 'DataWarehouse' after checking if it already exists. 
    If the database exists, it is dropped. 
	
WARNING:
    Running this script will drop the entire 'DataWarehouse' database if it exists. 
    All data in the database will be permanently deleted. Proceed with caution 
    and ensure you have proper backups before running this script.
*/

USE master;
GO

-- Drop and recreate the 'DataWarehouse' database
IF EXISTS (SELECT 1 FROM sys.databases WHERE name = 'DataWarehouse')
BEGIN
    ALTER DATABASE DataWarehouse SET SINGLE_USER WITH ROLLBACK IMMEDIATE;
    DROP DATABASE DataWarehouse;
END;
```

### Second Part: Create new data warehouse

```sql
/*
=============================================================
Create Database and Schemas
=============================================================
Script Purpose:
    This script creates a new database named 'DataWarehouse'. Additionally, the script sets up three schemas 
    within the database: 'bronze', 'silver', and 'gold'.
*/

-- Create the 'DataWarehouse' database
CREATE DATABASE DataWarehouse;
GO

USE DataWarehouse;
GO

-- Create Schemas
CREATE SCHEMA bronze;
GO

CREATE SCHEMA silver;
GO

CREATE SCHEMA gold;
GO
```

### Full SQL code

Name the following code `init_datawarehouse.sql`. 

```sql
/*
=============================================================
Create Database and Schemas
=============================================================
Script Purpose:
    This script creates a new database named 'DataWarehouse' after checking if it already exists. 
    If the database exists, it is dropped and recreated. Additionally, the script sets up three schemas 
    within the database: 'bronze', 'silver', and 'gold'.
	
WARNING:
    Running this script will drop the entire 'DataWarehouse' database if it exists. 
    All data in the database will be permanently deleted. Proceed with caution 
    and ensure you have proper backups before running this script.
*/

USE master; 

GO

IF EXISTS (SELECT 1 FROM sys.databases WHERE name = 'Datawarehouse')
BEGIN
    ALTER DATABASE DataWarehouse SET SINGLE_USER WITH ROLLBACK IMMEDIATE;
    DROP DATABASE DataWarehouse;
END

GO

-- Create the 'Datawarehouse' database
CREATE DATABASE Datawarehouse
GO

USE Datawarehouse
GO

-- Create Schemas

CREATE SCHEMA bronze
GO

CREATE SCHEMA silver
GO

CREATE SCHEMA gold
GO

```

## PostgreSQL database
---
1. In PostgreSQL `pgadmin` software, right-click on the server field and go to `Create` and select `Database`. 
2. Then name your database and leave everything else as default. 
3. Once your database is created, select and expand your database. 
4. Select **Query Tool**.
    - This opens a new tab connected directly to that database.
    - Run your queries in that tab — you're now “using” that database.
5. Now create your schemas with the following code: 

```sql
CREATE SCHEMA bronze
GO

CREATE SCHEMA silver
GO

CREATE SCHEMA gold
GO
```

1. Go to the View dropdown and select `Reload` . 
    - The schemas should appear as seen below:
    
    ![postgresql_schemas_bronze_silver_gold.png](attachment:9a3fd042-4bc4-4060-88b1-79e591baebca:postgresql_schemas_bronze_silver_gold.png)
