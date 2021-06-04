# PostgreSQL

## Setup and Basics

#### Installation

```bash
sudo apt-get install postgresql
```

#### Usage commands

```bash
service postgresql
```

#### Directories

```bash
etc/postgresql/12/main/
```

#### Switch to default user

```text
sudo su postgres
```

#### Launch Postgres shell

```bash
psql
```

## Docker Postgres

```bash
# pull the image
sudo docker pull postgres
sudo docker run --name postgres-dev -e POSTGRES_PASSWORD=password -d -p 5432:5432 postgres
sudo docker exec -it postgres-dev bash
psql -U postgres
```

#### See list of commands

```bash
man psql
```

#### Some Common commands

```sql
\l            to list all databases
\du            to list all users
```

#### Change password of user

```sql
ALTER USER postgres WITH PASSWORD 'test123';    #semi colon is important
```

#### Create new User

```sql
CREATE USER uday WITH PASSWORD 'test123';        # semi colon
```

#### Upgrade user to super user

```sql
ALTER USER dev WITH SUPERUSER;
```

#### Delete \| Drop user

```sql
DROP USER user;
```

! use only lower or only upper casing, also try to use upper case with command and lowercase with names

### Benefits of Relational Databases

* Efficient storage

There are a lot of information produced from single source of data and hence storing them category-wise in multiple tables in important.

Ex : one table about customer information and another table about order details about customer.

* Easier manipulation

When we need to process some data, then we wont be going through all the data coming from that source.

Ex : while processing orders, you don't need details of customer \(we might in some case\)

* Greater scalability
* Logically models a process
* Tables are related through common values \(keys\)

### Getting Started

#### Create a database

```sql
CREATE DATABASE test;
```

#### Connect to a database

```sql
psql --help
psql -h localhost -p 5432 -U postgres test
```

1. Here port : 5432 is default and can be get from psql --help
2. postgres is the super user, replace with your user
3. test is the name of database

#### To connect to another database

```sql
\c test            #name of database is test
```

#### Create a new table

```sql
CREATE TABLE person (
    id BIGSERIAL NOT NULL PRIMARY KEY,
    first_name VARCHAR(10) NOT NULL,
    last_name VARCHAR(10) NOT NULL,
    gender VARCHAR(7) NOT NULL,
    dob DATE NOT NULL
);                       # SEMI COLON ENDS THE STATEMENT
```

1. person is the name of table
2. `VARCHAR(x)` is the datatype to store string 
3. DATE is also a datatype

#### See list of tables

```sql
\d                      #to see tables
\d <name of table>       #to see detailes about table
```

### Dummy Data

**You can download dummy database from mackaroo.com**

![mockaroo](../../.gitbook/assets/mockaroo.png)

**now make the following changes in `.sql` file**

![changes to be made](../../.gitbook/assets/vscode-sql-mockaroo-changes.png)

**Import downloaded SQL database**

```sql
\i /home/uday/Downloads/person.sql
```

### Comments in PostgreSQL

```sql
-- hello
/*
    hello
*/
```

### Insert values into table

```sql
INSERT INTO person (first_name,last_name,gender,dob)
VALUES('UDAY','YADAV','MALE',date '2001-02-02');
```

1. make sure that values you enter should be in correct sequence
2. only ' single inverted comma must be used
3. only end VALUES with semi colon;

### Aliases

Just to rename the a column temporarily. Search for ' as ' in the document and you will find examples. an alias only exists for the duration of the query. they are often used to make column names more readable.

