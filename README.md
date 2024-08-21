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
