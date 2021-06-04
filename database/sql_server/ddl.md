# Data Definition

**CREATE DATABASE**

```text
CREATE DATABASE database_name;
go
```

**GET ALL DATABASES**

```text
SELECT name FROM  master.sys.databases
go
```

**DROP DATABASE**

```text
DROP DATABASE IF EXISTS TestDb;
go
```

## What is a schema in SQL Server

A schema is a collection of database objects including tables, views, triggers, stored procedures, indexes, etc. A schema is associated with a username which is known as the schema owner, who is the owner of the logically related database objects.

A schema always belongs to one database. On the other hand, a database may have one or multiple schemas.

**Get Information about tables**

```text
Select * From INFORMATION_SCHEMA.COLUMNS Where TABLE_NAME = 'jobs'
```

**Create Schema**

```text
CREATE SCHEMA customer_services;
GO
```

**Transfer Schema**

syntax : `ALTER SCHEMA [to schema] TRANSFER OBJECT::[from schema].offices;`

```text
ALTER SCHEMA dbo TRANSFER OBJECT::customer_services.offices;
```

**Drop Schema**

First you have to drop every table inside the schema

```text
DROP SCHEMA [IF EXISTS] schema_name;
```

**Create Table**

```text
CREATE TABLE sales.visits (
    visit_id INT PRIMARY KEY IDENTITY (1, 1),
    first_name VARCHAR (50) NOT NULL,
    last_name VARCHAR (50) NOT NULL,
    visited_at DATETIME,
    phone VARCHAR(20),
    store_id INT NOT NULL,
    FOREIGN KEY (store_id) REFERENCES sales.stores (store_id)
);
```

## SQL Server Identity

To create an identity column for a table, you use the IDENTITY property as follows:

```text
IDENTITY[(seed,increment)]
```

**Example**

```text
CREATE TABLE person (
    person_id INT IDENTITY(1,1) PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender CHAR(1) NOT NULL
);
```

Here the the value in the person\_id column will start from _1_ from and increment by _1_

## SQL Server Sequence

A sequence is simply a list of numbers, in which their orders are important. For example, the {1,2,3} is a sequence

**Create Sequence**

```text
CREATE SEQUENCE [schema_name.] sequence_name  
    [ AS integer_type ]  
    [ START WITH start_value ]  
    [ INCREMENT BY increment_value ]  
    [ { MINVALUE [ min_value ] } | { NO MINVALUE } ]  
    [ { MAXVALUE [ max_value ] } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ cache_size ] } | { NO CACHE } ];
```

* Example

```text
CREATE SEQUENCE item_counter
    AS INT
    START WITH 10
    INCREMENT BY 10;

SELECT NEXT VALUE FOR item_counter;
```

Read more here : [https://www.sqlservertutorial.net/sql-server-basics/sql-server-sequence/](https://www.sqlservertutorial.net/sql-server-basics/sql-server-sequence/)

**Getting Info**

```text
SELECT 
    * 
FROM 
    sys.sequences;
```

**DROP table**

```text
DROP TABLE [database_name.][schema_name.]table_name_1
```

**TRUNCATE TABLE** Server TRUNCATE TABLE statement to remove all rows from a table faster and more efficiently.

```text
TRUNCATE TABLE sales.customer_groups;
```

**Rename table**

```text
EXEC sp_rename 'old_table_name', 'new_table_name'
```

**Alter Table**

```text
ALTER TABLE sales.quotations 
ADD description VARCHAR (255) NOT NULL;
```

**ALTER TABLE ALTER COLUMN**

SQL Server allows you to perform the following changes to an existing column of a table:

* Modify the data type
* Change the size
* Add a NOT NULL constraint

```text
ALTER TABLE table_name 
ALTER COLUMN column_name new_data_type(size);
```

**ALTER TABLE DROP COLUMN**

```text
ALTER TABLE table_name
DROP COLUMN column_name;
```

Read more about compute columns SQL server : [https://www.sqlservertutorial.net/sql-server-basics/sql-server-computed-columns/](https://www.sqlservertutorial.net/sql-server-basics/sql-server-computed-columns/)

**Create Temporary Tables**

```text
select office_name into #temp_table from customer_services.offices;
```

