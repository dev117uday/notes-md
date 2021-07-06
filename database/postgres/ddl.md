
# Data Definition Language

### Some Common commands

```sql
\l            to list all databases
\du           to list all users
```

### Database Commands

#### Create Database Command

```sql
CREATE DATABASE test;
```

#### Connect to DB
```sql
\c test
```

### Table Commands

#### Create a new table

```sql
CREATE TABLE person (
    id BIGSERIAL NOT NULL PRIMARY KEY,
    first_name VARCHAR(10) NOT NULL,
    last_name VARCHAR(10) NOT NULL,
    gender VARCHAR(7) NOT NULL,
    dob DATE NOT NULL
);                       
-- SEMI COLON ENDS THE STATEMENT
```

#### See list of tables

```sql
\d                       #to see tables
\d <name of table>       #to see details about table
```