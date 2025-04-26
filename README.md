# SQL Basics

> *Click &#9733; if you like the project. Your contributions are heartily ♡ welcome.*

<br/>

## Related Topics

* *[SQL Commands](sql-commands.md)*
* *[SQL Query Practice](sql-query-practice.md)*

<br/>

## Table of Contents

* [Introduction](#-1-introduction)
* [SQL Data Types](#-2-sql-data-types)
* [SQL Database](#-3-sql-database)
* [SQL Table](#-4-sql-table)
* [SQL Select](#-5-sql-select)
* [SQL Clause](#-6-sql-clause)
* [SQL Order By](#-7-sql-order-by)
* [SQL Insert](#-8-sql-insert)
* [SQL Update](#-9-sql-update)
* [SQL Delete](#-10-sql-delete)
* [SQL Keys](#-11-sql-keys)
* [SQL Join](#-12-sql-join)
* [SQL RegEx](#-13-sql-regex)
* [SQL Indexes](#-14-sql-indexes)
* [SQL Wildcards](#-15-sql-wildcards)
* [SQL Date Format](#-16-sql-date-format)
* [SQL Transactions](#-17-sql-transactions)
* [SQL Functions](#-18-sql-functions)
* [SQL View](#-19-sql-view)
* [SQL Triggers](#-20-sql-triggers)
* [SQL Cursors](#-21-sql-cursors)
* [SQL Stored Procedures](#-22-sql-stored-procedures)
* [Miscellaneous](#-23-miscellaneous)

<br/>

## # 1. Introduction

<br/>

## Q. What is a database?

A database is a systematic or organized collection of related information that is stored in such a way that it can be easily accessed, retrieved, managed, and updated.

**Syntax:**

```sql
CREATE DATABASE <databaseName>
```

**Example:**

```sql
CREATE DATABASE Product
```

## Q. What is a database table?

A database table is a structure that organises data into rows and columns – forming a grid.

Tables are similar to a worksheets in spreadsheet applications. The rows run horizontally and represent each record. The columns run vertically and represent a specific field. The rows and columns intersect, forming a grid. The intersection of the rows and columns defines each cell in the table.

<p align="center">
  <img src="assets/table.png" alt="database table" width="400px" />
</p>

**Syntax:**

```sql
CREATE TABLE <table_name> (ID INT, NAME VARCHAR(30) )

DROP TABLE <table_name>

SELECT * FROM <table_name>
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is a database relationship?

Database relationships are associations between tables that are created using join statements to retrieve data. It helps improve table structures and reduce redundant data.

Understanding relationship in databases is important as it allows you to fetch data from multiple tables simultaneously and helps ensure that data in databases are consistent and updated.

**Types of Database Relationships:**

**1. One-to-One:**

A one-to-one relationship is a relationship between two tables where each table can have only one matching row in the other table.

<p align="center">
  <img src="assets/one-to-one.png" alt="One to One" width="450px" />
</p>

Using the above screenshot as an example, the business case is that each employee\'s pay details must be stored in a separate table to the employee\'s contact details. In such a case, there can only be one row in the Pay table that matches a given employee in the Employees table. This is a good candidate for a one-to-one relationship.

**2. One-to-Many:**

The one-to-many relationship is similar to the one-to-one relationship, except that it allows multiple matching rows in one of the tables.

<p align="center">
  <img src="assets/one-to-many.png" alt="One to Many" width="450px" />
</p>

In the above example, each author can have many books, but each book can only have one author.

Therefore, the Books table is allowed to contain multiple rows with the same AuthorId value. If an author has released five books, then there would be one row in Authors for that author, and five rows in Books, each with that author\'s AuthorId.

**3. Many-to-Many:**

In a many-to-many relationship, each side of the relationship can contain multiple rows.

<p align="center">
  <img src="assets/many-to-many.png" alt="Many to Many" width="450px" />
</p>

In this example, each book is allowed to have multiple authors. Therefore, I created a lookup table (also known as a "junction table") that stores both the AuthorId and the BookId.

These two columns could be configured to be the primary key of the table (in which case they would be a "composite primary key" or simply "composite key"), or you could create a separate column to be the primary key.

Note that the Books table doesn\'t have AuthorId in this case. That column has been moved to the AuthorBooks table so that we can have many AuthorIds for the same BookId.

<div align="right">
  <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is data Integrity?

Data Integrity defines the accuracy and consistency of data stored in a database. It can also define integrity constraints to enforce business rules on the data when it is entered into the application or database.

**Classification of Data Integrity:**

* a) System/Pre Defined Integrity
* b) User-Defined Integrity

<p align="center">
  <img src="assets/data-integrity.png" alt="Many to Many" width="500px" />
</p>

**a) System/Pre Defined Integrity:**

<p align="center">
  <img src="assets/system-integrity.png" alt="Many to Many" width="500px" />
</p>

**1. Entity Integrity:**

Entity integrity ensures each row in a table is a uniquely identifiable entity. We can apply Entity integrity to the Table by specifying a primary key, unique key, and not null.

**2. Referential Integrity:**

Referential integrity ensures the relationship between the Tables.

We can apply this using a Foreign Key constraint.

**3. Domain Integrity:**

Domain integrity ensures the data values in a database follow defined rules for values, range, and format. A database can enforce these rules using Check and Default constraints.

**b) User-Defined Integrity:**

It comprises the rules defined by the operator to fulfill their specific requirements. Entity, referential, and domain integrity are not enough to refine and secure data. Time in time again, particular business rules must be considered and integrated into data integrity processes to meet enterprise standards.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What are the two principles of relational database model?

The two principal rules for the relational model are as follows:

- Entity integrity: this is used to maintain the integrity at entity level
- Referential integrity: it is used to maintain integrity on all the values which have been referenced.

The differences between them are as follows:

- Entity integrity tells that in a database every entity should have a unique key; on the other hand referential integrity tells that in the database every table values for all foreign keys will remain valid.
- Referential integrity is based on entity integrity but it is not the other way around.
- For example: if a table is present and there is a set of column out of which one column has parent key set then to ensure that the table doesn'\t contain any duplicate values, a unique index is defined on the column that contains the parent key.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What are the relational operations that can be performed on the database?

There are many relational operators that are used to perform actions on relational database. These operators are as follows:

1. Union operator that combines the rows of two relations and doesn'\t include any duplicate. It also removes the duplicates from the result.
2. Intersection operator provides a set of rows that two relations have in common.
3. Difference operator provide the output by taking two relations and producing the difference of rows from first that don'\t exist in second.
4. Cartesian product is done on two relations. It acts as a cross join operator.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What do you understand by database Normalization?

- Normalization is very essential part of relational model.
- Normal forms are the common form of normalization.
- It helps in reducing redundancy to increase the information overall.
- It has some disadvantages as it increases complexity and have some overhead of processing.
- It consists of set of procedures that eliminates the domains that are non-atomic and redundancy of data that prevents data manipulation and loss of data integrity.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What are the different types of normalization that exists in the database?

There are 9 normalizations that are used inside the database. These are as follows:

1. First normal form: in this table represents a relation that has no repeating groups.
2. Second normal form: non- prime attributes are not functional dependent on subset of any candidate key.
3. Third normal form: in a table every non- prime attribute is non-transitively dependent on every candidate key
4. Elementary key normal form: superkey dependency or elementary key dependency effects the functional dependency in a table.
5. Boyce codd normal form: “every non-trivial functional dependency in the table is dependent on superkey”.
6. Fourth normal form: “Every non-trivial multivalued dependency in the table is a dependent on a superkey”.
7. Fifth normal form (5NF): “Every non-trivial join dependency in the table is implied by the superkeys of the table”.
8. Domain/key normal form (DKNF): “Every constraint on the table is a logical consequence of the table's domain constraints and key constraints”.
9. Sixth normal form (6NF): “Table features no non-trivial join dependencies at all”.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How de-normalization is different from normalization?

- Analytical processing databases are not very normalized. The operations which are used are read most databases. 
- It is used to extract the data that are ancient and accumulated over long period of time. For this purpose de-normalization occurs that provide smart business applications.
- Dimensional tables in star schema are good example of de-normalized data. 
- The de-normalized form must be controlled while extracting, transforming, loading and processing. 
- There should be constraint that user should not be allowed to view the state till it is consistent.
- It is used to increase the performance on many systems without RDBMS platform.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the type of de-normalization?

Non-first normal form (NFA) 

– It describes the definition of the database design which is different from the first normal form.
- It keeps the values in structured and specialized types with their own domain specific languages. 
- The query language used in this is extended to incorporate more support for relational domain values by adding more operators.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How many levels of data abstraction are available?

There are three levels of data abstraction available in database model and these are as follows:

1. Physical level: It is the lowest level that describes how data is stored inside the database.
2. Logical level: It is the next higher level in the hierarchy that provides the abstraction. It describes what data are stored and the relationship between them.
3. View level: It is the highest level in hierarchy that describes part of the entire database. It allows user to view the database and do the query.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What do you understand by Data Independence?

Data independence tells about the independence of the data inside the application. It usually deals with the storage structure and represents the ability to modify the schema definition. It doesn'\t affect the schema definition which is being written on the higher level. 

There are two types of data independence:

1. Physical data independence: It allows the modification to be done in physical level and doesn'\t affect the logical level.
2. Logical data independence: It allow the modification to be done at logical level and affects the view level. 

NOTE: Logical Data Independence is more difficult to achieve.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How view is related to data independence?

- View is a virtual table that doesn'\t really exist, but it remains present so that user can view their data.
- It is derived from the base table. The view is stored in the data dictionary and represents the file directly. 
- The base table updation or reconstruction is not being reflected in views.
- It is related to the logical data independence as it is at the logical level and not at the physical level.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Why E-R models are used?

E-R model stands for entity-relationship model and it is used to represent a model with their relationships. This is an object oriented approach and it is based on real world that consists of objects which are called entities and relationship between them. Entities are further used inside the database in the form of attributes.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What do you understand by cardinality and why it is used?

- Cardinality is important and used to arrange the data inside the database. 
- It is related to the design part and need to be properly used in database. 
- It is used in E-R diagrams and used to show the relationship between entities/tables. 
- It has many forms like the basic is one to one, which associate one entity with another.
- Second is one to many: which relates one entity with many entities in a table.
- Third is many to many M: N that allows many entities to be related to many more.
- Last is many to one that allows the many entities to be associated with one entity.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is DDL, DML and DCL?

SQL commands can be divided in three large subgroups.

1) DDL: The SQL commands which deals with database schemas and information of how the data will be generated in database are classified as Data Definition Language.
-For example: CREATE TABLE or ALTER TABLE belongs to DDL.

2) DML: The SQL commands which deals with data manipulation are classified as Data Manipulation Language.
For example: SELECT, INSERT, etc.

3) DCL: The SQL commands which deal with rights and permission over the database are classified as DCL.
For example: GRANT, REVOKE

## Q. How to prevent from database SQL Injection?

SQL Injection is a code-based vulnerability that allows an attacker to read and access sensitive data from the database. Attackers can bypass security measures of applications and use SQL queries to modify, add, update, or delete records in a database.

**Simple SQL Injection Example:**

```sql
SELECT id FROM users WHERE username='username' AND password='password' OR 1=1'
```

Because of the **OR 1=1** statement, the **WHERE** clause returns the first **id** from the **users** table no matter what the **username** and **password** are. The first user id in a database is very often the administrator. In this way, the attacker not only bypasses authentication but also gains administrator privileges.

**Prevent SQL Injections:**

**1. Continuous Scanning and Penetration Testing:**

The automated web application scanner has been the best choice to point out vulnerabilities within the web applications for quite some time now. Now, with SQL injections getting smarter in exploiting logical flaws, website security professionals should explore manual testing with the help of a security vendor.

They can authenticate user inputs against a set of rules for syntax, type, and length. It helps to audit application vulnerabilities discreetly so that you can patch the code before hackers exploit it to their advantage.

**2. Restrict Privileges:**

It is more of a database management function, but enforcing specific privileges to specific accounts helps prevent blind SQL injection attacks. Begin with no privileges account and move on to "read-only", "edit", "delete" and similar privilege levels.

Minimizing privileges to the application will ensure that the attacker, who gets into the database through the application, cannot make unauthorized use of specific data.

**3. Use Query Parameters:**

Dynamic queries create a lot of troubles for security professionals. They have to deal with variable vulnerabilities in each application, which only gets graver with updates and changes. It is recommended that you prepare parameterized queries.

These queries are simple, easy to write, and only pass when each parameter in SQL code is clearly defined. This way, your info is supplied with weapons to differentiate between code and information inputs.

**4. Instant Protection:**

A majority of organizations fail the problems like outdated code, scarcity of resources to test and make changes, no knowledge of application security, and frequent updates in the application. For these, web application protection is the best solution.

A managed web application firewall can be deployed for immediate mitigation of such attacks. It contains custom policies to block any suspicious input and deny information breach instantly. This way, you do not have to manually look for loopholes and mend problems afterward.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What are the non standard string types available in SQL?

Following are Non-Standard string types:

| Name     | Max Length |
|----------|------------|
|TINYTEXT  |255 bytes   |
|TEXT      |65,535 bytes|
|MEDIUMTEXT|16 MB       |
|LONGTEXT  |4GB         |

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 2. SQL Data Types

<br/>

## Q. What is difference between CHAR and VARCHAR in MySQL?

Both of them are used for string type data. `char` has fixed length and if the inserted data is less than the defined length, required no. of blank spaces are added as padding. `varchar` has variable length and no padding is used to fill up the left out space. So technically, varchar will save space.

## Q. What are the string datatypes in SQL?

A list of data types used in MySQL database. This is based on MySQL 8.0.

|Data Types      | Description                           |
|----------------|---------------------------------------|
|CHAR(Size)      |It is used to specify a fixed length string that can contain numbers, letters, and special characters. Its size can be 0 to 255 characters. Default is 1.|
|VARCHAR(Size)   |It is used to specify a variable length string that can contain numbers, letters, and special characters. Its size can be from 0 to 65535 characters.|
|BINARY(Size)    |It is equal to CHAR() but stores binary byte strings. Its size parameter specifies the column length in the bytes. Default is 1.|
|VARBINARY(Size) |It is equal to VARCHAR() but stores binary byte strings. Its size parameter specifies the maximum column length in bytes.|
|TEXT(Size)      |It holds a string that can contain a maximum length of 255 characters.|
|TINYTEXT        |It holds a string with a maximum length of 255 characters.|
|MEDIUMTEXT      |It holds a string with a maximum length of 16,777,215.|
|LONGTEXT        |It holds a string with a maximum length of 4,294,967,295 characters.
|ENUM(val1, val2, val3,...)|It is used when a string object having only one value, chosen from a list of possible values. It contains 65535 values in an ENUM list. If you insert a value that is not in the list, a blank value will be inserted.|
|SET( val1,val2,val3,....)|It is used to specify a string that can have 0 or more values, chosen from a list of possible values. You can list up to 64 values at one time in a SET list.|
|BLOB(size)    |It is used for BLOBs (Binary Large Objects). It can hold up to 65,535 bytes.|

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What are the differences between the BLOB and TEXT datatypes in MySQL?

BLOB stands for Binary Large Objects and as its name suggests, it can be used for storing binary data while TEXT is used for storing large number of strings. BLOB can be used to store **binary data** that means we can store pictures, videos, sounds and programs also.

BLOB values behave like byte string and BLOB does not have a character set. Therefore, comparison and sorting is fully dependent upon numeric values of bytes.

TEXT values behave like non-binary string or character string. TEXT has a character set and the comparison/ sorting fully depends upon the collection of character set.

**Creating a table with TEXT data type:**

```sql
mysql> create table TextTableDemo ( Address TEXT );

mysql> DESC TextTableDemo;
```

**Creating a table with BLOB type:**

```sql
mysql> create table BlobTableDemo ( Images BLOB );

mysql> desc BlobTableDemo;
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 3. SQL Database

<br/>

#### Q. How to create a database using SQL?

To create a database using SQL, you can use the `CREATE DATABASE` statement followed by the name of the database you want to create. Here's the basic syntax:

```sql
CREATE DATABASE database_name;
```
For example, if you want to create a database called "mydatabase", you can run the following SQL query:

```sql
CREATE DATABASE mydatabase;
```
Note that depending on your SQL environment, you may need to have appropriate permissions to create a database.

## # 4. SQL Table

<br/>