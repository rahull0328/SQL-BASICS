# 🌟 Database Management Systems (DBMS) - BASICS 🌟
### Introduction 📚
Whether you are just starting with databases or looking to refine your skills, this repository offers comprehensive insights into designing, querying, and managing relational databases. Explore the core concepts through practical examples and detailed explanations tailored for learners and professionals alike.
### Contents 📋

1. **Data Definition Language (DDL)**
   - CREATE 🛠️
   - ALTER ✏️
   - DROP 🗑️
   - TRUNCATE 🚮
2. **Data Query Language (DQL)**
   - SELECT 🔍
3. **Data Manipulation Language (DML)**
   - INSERT ➕
   - UPDATE ✏️
   - DELETE ➖
4. **Transaction Control Language (TCL)**
   - COMMIT 💾
   - ROLLBACK ⏪
   - SAVEPOINT 📍
5. **Examples**

### Data Definition Language (DDL) 🛠️

DDL statements are used to define, alter, and manage database schema.

#### CREATE 🛠️

Used to create databases, tables, indexes, views, etc.

```sql
-- Create a new database
CREATE DATABASE mydatabase;

-- Create a new table
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    department VARCHAR(50)
);
```

#### ALTER ✏️

Used to modify the structure of an existing database object.

```sql
-- Add a new column to an existing table
ALTER TABLE employees ADD salary DECIMAL(10, 2);

-- Modify the datatype of a column
ALTER TABLE employees MODIFY COLUMN age SMALLINT;
```

#### DROP 🗑️

Used to delete databases, tables, indexes, views, etc.

```sql
-- Drop a table
DROP TABLE employees;

-- Drop a database
DROP DATABASE mydatabase;
```

#### TRUNCATE 🚮

### Data Query Language (DQL) 🔍

DQL is used to query the database and retrieve data.

#### SELECT 🔍

Used to retrieve data from one or more tables.

```sql
-- Select specific columns
SELECT name, department FROM employees WHERE age > 30;

-- Select all columns
SELECT * FROM employees;
```

Used to delete all rows from a table without deleting the table itself.

```sql
-- Truncate a table
TRUNCATE TABLE employees;
```
