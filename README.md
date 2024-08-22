# SQL-Notes

## Database

Database is a collection of data in a format that can be easily accessed.

A software application used to manage our Database is called Database Management System(DBMS).

### Types of Database

- Relational: Data Stored in tables, eg. MySQL, ORACLE, PostgreSQL
- Non-relational(NoSQL): data not stored in table, eg. mongoDB

## What is SQL?

SQL is a programming language used to intereact with relational database.

It is used to perform CRUD operation:
- Create
- Read
- Update
- Delete

SQL was previously known as SEQUEL (Structured English Query Language) but then named as SQL(Structured Query Language).

## Creating our first Database

``` CREATE DATABASR db_name;``` - Syntax to create database

``` DROP DATABASE db_name``` - Syntax to delete database

## Creating table 

```
USE db_name;

CREATE TABLE table_name (
    column_name1 datatype constraint,
    column_name2 datatype constraint,
    column_name2 datatype constraint
);
```
example: 
```
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT NOT NULL
);
```

## SQL Datatypes

They define the types of values that can be stored in a column

| DATATYPE | DESCRIPTION | USAGE |
|----------|-------------|-------|
| CHAR     | string(0-255), can store characters of fixed length | `CHAR(50)` |
| VARCHAR  | string(0-255), can store characters up to given length | `VARCHAR(50)` |
| BLOB     | string(0-65535), can store binary large object | `BLOB(1000)` |
| INT      | integer (-2,147,483,648 to 2,147,483,647) | `INT` |
| TINYINT  | integer (-128 to 127) | `TINYINT` |
| BIGINT   | integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807) | `BIGINT` |
| BIT      | can store x-bit values. x can range from 1 to 64 | `BIT(2)` |
| FLOAT    | Decimal number with precision to 23 digits | `FLOAT` |
| DOUBLE   | Decimal number with 24 to 53 digits | `DOUBLE` |
| BOOLEAN  | Boolean values 0 or 1 | `BOOLEAN` |
| DATE     | date in format of YYYY-MM-DD ranging from 1000-01-01 to 9999-12-31 | `DATE` |
| TIME     | HH:MM:SS | `TIME` |
| YEAR     | year in 4 digits format ranging from 1901 to 2155 | `YEAR` |

### Signed and Unsigned datatype

As we know tinyint stored values from -128 to -127 `TINYINT(-128 to 127)` but in some cases where we know that values can't be negative eg. age, salary there we can use `TINYINT UNSIGNED(0 TO 255)` it will increase the size to positive side.

## Types of SQL Commands

1. DQL (Data Query Language) : Used to retrieve data from databases. (SELECT)
2. DDL (Data Definition Language) : Used to create, alter, and delete database objects
like tables, indexes, etc. (CREATE, DROP, ALTER, RENAME, TRUNCATE)
3. DML (Data Manipulation Language): Used to modify the database. (INSERT,
UPDATE, DELETE)
4. DCL (Data Control Language): Used to grant & revoke permissions. (GRANT,
REVOKE)
5. TCL (Transaction Control Language): Used to manage transactions. (COMMIT,
ROLLBACK, START TRANSACTIONS, SAVEPOINT)

## Database Related Queries

```
CREATE DATABASE db_name; 
CREATE DATABASE IF NOT EXISTS db_name;
CREATE DATABASE IF NOT EXISTS college; 

DROP DATABASE db_name; 
DROP DATABASE IF EXISTS db_name; 

SHOW DATABASES; 
SHOW TABLES;
```
In this query `CREATE DATABASE IF NOT EXISTS db_name;` , we have written If not exists which means that create a database with name `xyz` if this name doesn't exist and if exist it will give us a warning.

Same with `DROP DATABASE IF EXISTS db_name;` , delete a database it exist and if not exist throw us a warning.

## Table related Queries

To select and view all columns : `SELECT * FROM table_name;` where `*` means all.

To insert : 
```
INSERT INTO table_name 
(colname1, colname2);
VALUES
(col1_v1, col2_v1),
(col1_v2, col2_v2);
```

example :
```
INSERT INTO student
(rollno, name)
VALUES
(15, "Aman"),
(34, "Mayank");
(43, "Devesh");
```

## Keys

### Primary Key 
It is a column (or set of columns) in a table that uniquely identifies each row. (a unique id) There is only 1 PK & it should be NOT null.

### Foreign Key
A foreign key is a column (or set of columns) in a table that refers to the primary key in another table. There can be multiple Foreign Keys.
- Foreign key can have duplicate and null values.

## Constraints

SQL constraints are used to specify rules for data in a table. 
- NOT NULL: columns cannot have a null value `col1 int NOT NULL`
- UNIQUE: all values in column are different `col2 int UNIQUE`
- PRIMARY KEY: makes a column unique & not null but used only for one `id int PRIMARY KEY`
    ```
    CREATE TABLE temp (
    id int not null,
    PRIMARY KEY (id)
    );
    ```
- FOREIGN KEY: prevent actions that would destroy links between tables
  ```
  CREATE TABLE temp (
  cust_id int,
  FOREIGN KEY (cust_id) references customer(id)
  );```
- DEFAULT: sets the default value of a column `salary INT DEFAULT 25000`, If we create a table and provide values for each column, any columns without specified values will automatically be set to their default values.
- CHECK: it can limit the values allowed in a column
  ```
  CREATE TABLE city (
  id INT PRIMARY KEY,
  city VARCHAR(50),
  age INT,
  CONSTRAINT age_check CHECK (age >= 18 AND city="Delhi")
  );
  ```
## Select in Detail
used to select any data from the database

 Basic Syntax : `SELECT col1, col2 FROM table_name;`
 
 To Select All : ` SELECT * FROM table_name;`
## Where Clause
clause is use to define some conditions
```
syntax:  SELECT col1, col2 FROM table_name
         WHERE conditions
Exapmle : 
        SELECT * FROM student WHERE marks > 80;
        SELECT * FROM student WHERE city = "Delhi";
```
Using Operators in WHERE 
- Arithmetic Operators: +(addition), -(subtraction), *(multiplication), /(division), % (modulus)
- Comparison Operators: = (equal to), != (not equal to), > > <=
- Logical Operators: AND, OR, NOT, IN, BETWEEN, ALL, LIKE, ANY
- Bitwise Operators: & (Bitwise AND), ❘ (Bitwise OR) APNA

## Operators
- AND (to check for both conditions to be true)
  
  `SELECT * FROM student WHERE marks > 80 AND city = "Mumbai";`
- OR (to check for one of the conditions to be true)
  
  `SELECT * FROM student WHERE marks > 90 OR city = "Mumbai";`
- Between (selects for a given range)
  
  `SELECT * FROM student WHERE marks BETWEEN 80 AND 90;`
- In (matches any value in the list)
  
  `SELECT * FROM student WHERE city IN ("Delhi", "Mumbai");`
- NOT (to negate the given condition)
  
  `SELECT * FROM student WHERE city NOT IN ("Delhi", "Mumbai");`

## Limit Clause
Sets an upper limit on number of (tuples)rows to be returned 

SELECT col1, col2 FROM table_name 

LIMIT number;

`SELECT * FROM student LIMIT 3;`

## Aggregate Functions
Aggregare functions perform a calculation on a set of values, and return a single value.
-  COUNT()
-  MAX()
-  MIN()
-  SUM()
-  AVG()

  ```
  Get Maximum Marks
  SELECT max (marks) FROM student;

  Get Average marks
  SELECT avg (marks) FROM student;
  ```

## Group by Clause
Groups rows that have the same values into summary rows. 
It collects data from multiple records and groups the result by one or more column. 

*Generally we use group by with some aggregation function. 

Count number of students in each city 
```
SELECT city, count(name)
FROM student
GROUP BY city;
```
