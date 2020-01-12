# SQL

## History
* It started life as SEQUEL in 1974, an IBM product
* In 1980 it was renamed SQL
* There is a SQL standard maintained by the American National Standards Institute (ANSI). Most database vendors extend the standard
* PhpMyAdmin is a tool that helps manage database using a web interface, it is written in PHP.
* The easiest way to get MySQL and PHPMyAdmin is to install free tools like XAMPP or WAMP, Then a database server can be installed on the computer and Database management can be accessed from browser using url: localhost:8080/myphpadmin.
(userid:root, password:"")

## Concepts
* Column Sometimes referred to as a field, contains the same type of information for every record in table.
* Row Sometimes referred to as a record
Table is a collection of related rows
* Database is a collection of related tables and other objects
* Entity is represented by a table, it is a thing or a person etc.
Cardinality can be used to represent the Entity relationship(one to one, one to many etc.), when the Entity can be zero it is optional.
* A weak entity is an entity that cannot be uniquely identified by its attributes alone; therefore, it must use a foreign key.
* Relationship has degree, A unary relationship(one entity, recursive relationship), binary relationship(two entities), ternary relationship(three entities), four-entity relationship(four entities), Ternary (and higher) relationships are usually represented by a series of binary relationships.
* Attribute is represented by column headings.
* Data Dictionary
  * Also called Metadata System Tables (SQL Server)  System dictionary is the repository of all data definitions for all objects within the scope of the database. It contains meta-data (Table name, column name, data constraints, primary and foreign keys, index)
* The System Catalog
  * A detailed system data dictionary that describes all objects in the database  
* For System table of the SQL Server
  * Starting with SQL Server 2005, all System Tables are hidden and inaccessible directly  A large collection of System Views have been created to accommodate accessing of database’s metadata  Two schemas  INFORMATION_SCHEMA  sys  
* A primary key is a single field in the table that uniquely identifies (unique nonempty values)the table records. primary auto creates index.
* Foreign Key is a field a reference a PK from another table.
* A good choice for primary keys is a Meaningless But Unique Number (MBUN)•Start at 1 and keep incrementing•The int datatype provides 2,147,483,647 possible values•The bigint datatype provides 9,223,372,036,854,775,807 possible values (> 9 quintillion)
* Another possible choice is the Globally Unique Identifier (GUID)–Also known as Universally Unique Identifier (UUID)•128 bit integer, typically expressed as 32 hex digits in the pattern 8-4-4-4-12–Example: 678e6b75-29ad-4cba-8d78-5ad68aad414b•Good for decentralized systems
* Naming Conventions
  * Do not put spaces in the names of anything you create
  * Do not use descriptive prefixes or postfixes such as tbl
  * Use all lowercase and divide word boundaries with ``_``, database name uppercase.
  * [Click here to see more](http://www.sqlstyle.guide).
* IDENTITY Property
  * SQL Server provides an optional identity property to simplify creating MBUNs•The identity property would be added to the definition of the primary key column when a table is being created.
  * IDENTITY [ (seed , increment) ]  Seed and increment are optional, both default to 1
  * when insert row without specifying the value for PK, default rules are used.
  * Using an identity property simplifies INSERTs.
  * Without an identity property, the primary key must first be determined and then specified
  * With an identity property, the primary key is left off the INSERT statement and the database automatically keeps track of it and provides it when necessary.
* Determinant
  * An attribute whose value determines the value for another attribute
  * Usually the primary key.
* Functional Dependency
  * Relationship between a determinant A and dependent attribute B.
  * Represented by A -> B
* Candidate Key
  * One of the attributes that could be used as a primary key.
* Relation
  * A table with rows and columns •Each row contains information on an instance of an entity
* Tuple is a row of data
* When design database, identity the entities then find their relationship.
* Many-to-Many relationship cannot be represented in the database. Hence, an intersection entities is required.
* Atomic attribute  
  * A component of the record definition that is used to describe an entity  A field  Unique meaningful names  Example: postal_code  Composite attribute  Composed of atomic attributes, each defined in the data dictionary  Address is comprised of  street_address  city  province_id  postal_code  
* Derived attribute  
  * An attribute whose value is obtained by applying a formula to other data elements  Examples:   		sales commission = sales * percentage  		age = DATEDIFF(YEAR, birth_date, GETDATE())  Multi-valued attribute  An attribute with multiple possible values  A employee can have more than one skill  Alias  Synonym  A different name for a data element with the same meaning  ``SELECT COUNT(*) AS total FROM patients``
* Domain  
  * The set of possible values an attribute can take on  Concatenated Key  Also known as Composite Key, Compound Key  Two or more attributes taken together to uniquely identify a record   Examples:  patient_id, admission_date in admissions table  purchase_order_id, line_num in purchase_order_lines table  Secondary Key   Requires an index may not be unique   Example: last_name  Sort Key   Used to physically sequence a file   Example: seniority listing of employee records
* Foreign Key   
  * A field (or multiple fields) in a table that uniquely identifies a row of another table (or the same table)  Example: nursing_unit_id in admissions table  Entity Occurrence   Represented by a record with actual data values in it, or a row in a table  Schema   The definition of an entire database  In SQL Server, schemas are used as containers to organize database objects
* Indexes is used to improve only the access time.
* Clustered indexes is the indexes that are associated with a column, usually the primary key. when create is physical sort and associated column data. Unclustered index store unsorted data on the store device and use pointers to associate the data with index.
* Multiple SQL statement can bu put in order, end with ;.
* Normalization Quick Summary•
  * 0NF - tables without normalization.
  * 1NF - Eliminate Repeating Groups And Derived Attributes–Make a separate table for each set of related attributes, and give each table a primary key•
  * 2NF - Eliminate Redundant Data–If an attribute depends on only part of a composite key, remove it to a separate table•
  * 3NF - Eliminate Columns Not Dependent On Key–If attributes do not contribute to a description of the key, remove them to a separate table
* OLTP(Online Transaction Process) uses normalized data.
* OLAP(Online Analytical Process) and BI(Business Intellige) and Data warehouse stores denormalized data.
* Business Rules are specifications that preserve the integrity of a conceptual or logical data model. They are enforced by for types of rules.
* Entity integrity(PK)
* Referential integrity(FK)
* Domains(Value Boundary, check)
* Triggering operations(?)
* View
  * View is a virtual table based on one or more tables.
  * The View result set is not permanently stored in the database, but generated each time it is used
  * Shows up in INFORMATION_SCHEMA.VIEWS &INFORMATION_SCHEMA.TAB
* SQL Statements have two types.
  * Data Definition Language (DDL)
    * CREATE table
    * CREATE index
  * Data Manipulation Language (DML)
    * SELECT
    * INSERT
    * UPDATE
    * DELETE
* Depending on the database vendor, data can be case sensitive ``'M' <> 'm'``
* For Character and string data single quotes are recommended and generally used.
* Convention is to capitalize keywords and place each clause on its own line
* multiple queries or commands can be entered at the same time and separate by ; at end of each line.
* SQL is case insensitive. However uppercase is preferred for all commands.
* SQL syntax is not sensitive to indentations.

## Syntax
The following SQL examples work for mySQL, variation for other SQL will be noted in the bracket.

* Check server version
```sql
select @@version
```

* the  command lists the databases managed by the server.
```sql
SHOW DATABASES MySQL
.databases in SQL Server
```


* display all of the tables in the currently selected database.
```sql
SHOW TABLES MySQL
.tables in SQL Server
```

* displays information about the columns in a given table.
```sql
SHOW COLUMNS FROM tablename
```


### SELECT
* The SELECT statement is used to query data from a database. Query results are stored in a table called result-set.
* A SELECT statement retrieves zero or more rows from one or more database tables.
* FROM is required expect for SQL Server.
```sql
SELECT column_list
FROM table_name
```
* SELECT can be followed by a column function.
  * AVG–Computes the average value of the column
  * COUNT–Counts the number of rows
  * MAX–Determines the maximum value
  * MIN–Determines the minimum value
  * SUM–Totals the numeric values
```sql
SELECT COUNT(*)FROM patients
SELECT AVG(patient_weight)FROM patients
SELECT MIN(last_name)FROM patients
```
* Columns have fully qualified names as tablename.columnname is acceptable. It is used to distinguish same columns names from different tables.
* Multiple columns can be queried in one command separated by commas.
* ``*`` represent all.
* ```DISTINCT``` qualifier return unique value of columns
```sql
SELECT DISTINCT column_name1, column_name2
FROM table_name;
```
* ```LIMIT``` keyword shows only specific number of d rows.
```sql
SELECT ID, FirstName, LastName, City
FROM customers LIMIT 5;
```
```sql
Select 4 start after 3rd(counting from zero)
SELECT ID, FirstName, LastName, City
 FROM customers LIMIT 3, 4;
```
* Im SQL Server use TOP, The TOP clause sets a maximum number of rows that can be retrieved
```sql
SELECT TOP 5 *
FROM patients;
and
SELECT TOP 5 PERCENT *
FROM patients;
```
* ORDER BY is used with SELECT to sort the returned data.
* Can order by multiple columns separate by commas. Sort the first column first then second.
```sql
SELECT * FROM customers
ORDER BY FirstName;
Default uses ascending order.
Or use
ORDER BY Salary DESC(ASC)
```
* Where keyword is used to add conditions.
  * Predicates are used in the WHERE clause to specify conditions, Basic Predicate:
    * ``=, <>, <, >, <=, >=``
    * BETWEEN Predicate
    * EXISTS Predicate
    * IN Predicate
    * LIKE Predicate
    * NULL Predicate
  ```sql
  SELECT column_list
  FROM table_name
  WHERE condition;
  Condition could be ID=5 (any comparison and logic operator(and & or)
  between. for example ID=5 and ID=10)
  SELECT * FROM customers
  WHERE ID BETWEEN 3 AND 7;
  (Boundaries are included)
  ```
* Single quotation marks (') is used for text.
```sql
SELECT ID, FirstName, LastName, City
FROM customers
WHERE City = 'New York';
```
* ‘ can also be the escape characters.  Ex: Can''t
* ``IN`` keyword includes all satisfied columns.
```sql
SELECT * FROM customers
WHERE City IN ('New York', 'Los Angeles', 'Chicago');
```
* The NOT IN operator allows you to exclude a list of specific values from the result set. Result set must included in bracket, even there is only one element in it. result set can be a column returned from other SELECT query.
* EXISTS returns true if a subquery contains any rows.
```sql
SELECT first_name, last_name
FROM patients
WHERE EXISTS (SELECT * FROM unit_dose_orders WHERE unit_dose_orders.patient_id = patients.patient_id)
(This select all row of patients tables that exist in the unit_dose_orders table.)

SELECT *
FROM vendors
WHERE NOT EXISTS (SELECT * FROM purchase_orders WHERE purchase_orders.vendor_id = vendors.vendor_id)
(This select all row of patients tables that don’t exist in the unit_dose_orders table.)
SELECT * FROM patients
WHERE allergies IS NULL;
IS can be used with NULL. or IS NOT NULL
```
* AND and OR can be used to connects conditions for WHERE statement.
* Concat combine two column in a format
  * A concatenation results in a new column. The default column name will be the CONCAT
```sql
SELECT CONCAT(FirstName, ', ' , City) FROM customers;
```
* AS is used for a column name change(Alias).
```sql
SELECT CONCAT(FirstName,', ', City) AS new_column
FROM customers;
```
* Arithmetic operator can also be used in query.
```sql
SELECT ID, FirstName, LastName, Salary+500 AS Salary
FROM employees;
```
* Upper and lower function change upper lower cases.
  * * Only affects on letters with default name Upper.
```sql
SELECT FirstName, UPPER(LastName) AS LastName
FROM employees;
```
* GROUP BY
  * It can be used to deal with results of the column that has different rows.
  * GROUP BY must be used in conjunction with an aggregating function
  * Does not sort automatically, still need ORDER BY for sort
  * Multiple groupings are allowed
```sql
SELECT province_id, city, COUNT(*)
FROM patients
GROUP BY province_id, city
```
* HAVING
```sql
SELECT nursing_unit_id, COUNT(*)
FROM admissions
GROUP BY nursing_unit_id
HAVING COUNT(*) >= 340
```
  * It is like another WHERE clause for grouped columns.
  * Used with GROUP BY
* Subqueries is a query that has queries inside.
  * the inner query is processed first.
  * Enclose the subquery in parentheses.
  * Subquery Returns Single Rows
  ```sql
  SELECT FirstName, Salary FROM employees
  WHERE  Salary > (SELECT AVG(Salary) FROM employees)
  ORDER BY Salary DESC;
  ```
  * Subquery Returns Multiple Rows
  ```sql
  SELECT nursing_unit_id, patient_id, admission_date
  FROM admissions
  WHERE nursing_unit_id IN(SELECT nursing_unit_idFROM nursing_unitsWHERE beds < 10)
  ORDER BY nursing_unit_id, patient_id
  ```
  * Nested Subquery
  ```sql
  SELECT nursing_unit_id, COUNT(*) AS patients
  FROM admissionsWHERE nursing_unit_id IN
  (SELECT nursing_unit_id
  FROM nursing_units
  WHERE beds >(SELECT AVG(beds)FROM nursing_units))
  GROUP BY nursing_unit_id
  ```
* The like keyword can be used to specify a pattern, pattern is represented by:
  * ``_`` any value.
  * ``%`` any group of values
```sql
SELECT * FROM employees
WHERE FirstName LIKE 'A%';
This choose any text begin with A.
```
* NOT LIKE picks anything that not in this pattern.

### Built-in Function
* Scalar Functions – Returns Single value.
* Column Function - works with a set of value.

* Mathematical Functions
  * ABS
  * ACOS
  * ASIN
  * ATAN
  * ATN2
  * CEILING
  * COS
  * COT
  * DEGREES
  * EXP
  * FLOOR
  * LOG
  * LOG10
  * PI
  * POWER
  * RADIANS
  * RAND
  * ROUND
  * SIGN
  * SIN
  * SQRT
  * SQUARE
  * TAN
* String Functions
  * ASCII
  * CHAR
  * CHARINDEX
  * DIFFERENCE
  * LEFT
  * LEN
  * LOWER
  * LTRIM
  * NCHAR
  * PATINDEX
  * QUOTENAME
  * REPLACE
  * REPLICATE
  * REVERSE
  * RTRIM
  * SOUNDEX
  * SPACE
  * STR
  * STUFF
  * SUBSTRING
  * UNICODE
  * UPPER
* Date And Time Functions
  * CURRENT_TIMESTAMP
  * DATEDIFF(datepartType, startdate, enddate)
    * datepartType: year, quarter, month, dayofyear, day, week, hour, minute, second, millisecond, microsecond, nanonsecond
  ```sql
  SELECT DATEDIFF(DAY, '2017-01-01', '2018-09-01')
  Result is 608 days

  SELECT DATEDIFF(MONTH, '2017-01-01', '2018-09-01')
  Result is 20 months

  SELECT DATEDIFF(YEAR, '1999-11-15', '2018-10-02')
  Result is 19 years
  ```
    * Be careful, DATEDIFF with YEAR does not calculate age. A person born on November 15, 1999 is not 19 on October 2, 2018. Use the following way to calculate.
    ```sql
    SELECT FLOOR(DATEDIFF(DAY, '1999-11-15', '2018-10-02') / 365.25)
    Result is 18 years
    ```
    * DATEDIFF extracts the YEAR from both dates and performs subtraction without considering the months or days
  * DATEADD(datepart, number, date)
  ```sql
  SELECT DATEADD(DAY, 60, '2018-09-01')
  Result is 2018-10-31

  SELECT DATEADD(MONTH, 5, '2018-09-01')
  Result is 2019-02-01

  SELECT DATEADD(YEAR, 3, '2018-09-01')
  Result is 2021-09-01
  ```
    * use DATEADD with negative values
    ```sql
    SELECT DATEADD(DAY, -60, '2018-09-01')
    Result is 2018-07-03

    SELECT DATEADD(MONTH, -5, '2018-09-01')
    Result is 2018-04-01

    SELECT DATEADD(YEAR, -3, '2018-09-01')
    Result is 2015-09-01
    ```
  * DATENAME(datepart, date) works like DATEPART but returns a string instead of an integer
  ```sql
  SELECT encounter_date_time,
         DATENAME(HOUR, encounter_date_time) AS [hour],
         DATENAME(MINUTE, encounter_date_time) AS [minute],
         DATENAME(SECOND, encounter_date_time) AS [second]
  FROM encounters
  ```
  * DATEPART(datepart, date)
  ```sql
  SELECT encounter_date_time,
         DATEPART(HOUR, encounter_date_time) AS [hour],
         DATEPART(MINUTE, encounter_date_time) AS [minute],
         DATEPART(SECOND, encounter_date_time) AS [second]
  FROM encounters
  ```
    * DAY(date) extracts the day of the month
    * MONTH(date) extracts the month of the year
    * YEAR(date) extracts the year
  ```sql
  SELECT birth_date,
         YEAR(birth_date) AS [year],
         MONTH(birth_date) AS [month],
         DAY(birth_date) AS [day]
  FROM patients
  ```
  * The GETDATE function returns the current date with time
  ```sql
  SELECT GETDATE()
  ```
    * To get the date without the time, the CONVERT function can be used
  ```sql
  SELECT CONVERT(DATE, GETDATE())
  ```
    * Calculate patient age
    ```sql
    SELECT birth_date,
           FLOOR(DATEDIFF(DAY, birth_date, GETDATE()) / 365.25)
    FROM patients
    ```
  * GETUTCDATE
  * ISDATE
  * MONTH
  * SWITCHOFFSET
  * TODATETIMEOFFSET
  * YEAR

### Join(regular)
Rows returned only if they exist in both tables


1. use SELECT…..WHERE Col1 =  Col2

SELECT customers.ID, customers.Name, orders.Name, orders.Amount
FROM customers, orders
WHERE customers.ID=orders.Customer_ID
ORDER BY customers.ID;

Table names can use nickname, set in from clause

SELECT ct.ID, ct.Name, ord.Name, ord.Amount
FROM customers AS ct, orders AS ord
WHERE ct.ID=ord.Customer_ID
ORDER BY ct.ID;

-AS can be omitted sometimes, like in SSMS.
SELECT ct.* ord.Name, ord.Amount
FROM customers ct, orders ord
WHERE ct.ID=ord.Customer_ID
ORDER BY ct.ID;

ct.* means all columns from table ct.

2. use join…on

SELECT column(s)
FROM firsttable
JOIN secondtable
ON firsttable.column = secondtable.column

example:
SELECT *
FROM purchase_orders
JOIN purchase_order_lines
ON purchase_orders.purchase_order_id = purchase_order_lines.purchase_order_id

Select all columns from both tables
Join on purchase order number

It is also called inner join

SELECT column_name(s)
FROM table1 INNER JOIN table2
ON table1.column_name=table2.column_name;

The LEFT JOIN returns all rows from the left table, even if there are no matches in the right table.
SELECT table1.column1, table2.column2...
FROM table1 LEFT OUTER JOIN table2
ON table1.column_name = table2.column_name;

If no match is found for a particular row, NULL is returned.

The RIGHT JOIN returns all rows from the right table, even if there are no matches in the left table.

MySQL only support above types of join.
OUTER keywords can be optional.
There are many other types of join.
full outer join
All rows returned from both tables
Missing values returned as NULL


cross join
Each row from left table is joined with each row from right table
if table_a has x rows, table_b has y rows. the cross join of them has x multiply by y rows.

SELECT p.product_id, sold, purchased
FROM sales_lines s
CROSS JOIN purchase_lines p

or (inner join using where = syntax and remove the where clause)
SELECT ct.ID, ct.Name, ord.Name, ord.Amount
FROM customers  ct, orders  ord


Example for join 3 tables

SELECT first_name, last_name, medication_description, dosage
FROM patients p
JOIN unit_dose_orders u
  ON p.patient_id = u.patient_id
JOIN medications m
  ON u.medication_id = m.medication_id
ORDER BY last_name, first_name, medication_description

Joining a Table with Itself
SELECT e1.employee_id, e1.first_name, e1.last_name, e1.department, e1.title, e1.supervisor, e2.employee_id, e2.first_name, e2.last_name
FROM employees e1
LEFT JOIN employees e2     - - if not using LEFT, somebody will be missing.
ON e1.supervisor = e2.employee_id
ORDER BY e1.department, e1.employee_id


UNION combines multiple datasets into a single dataset, removes any existing duplicates.
UNION ALL (faster) does not remove duplicate rows
Union combines two or more select statements with same type of columns(data type) in order. If one column can’t match use null instead.

SELECT FirstName, LastName, Company FROM businessContacts
UNION
SELECT FirstName, LastName, NULL FROM otherContacts;


Order of Clauses in SELECT

SELECT		list_of_columns
FROM		list_of_tables
WHERE		list of conditions
GROUP BY	list_of_expressions
HAVING		condition
ORDER BY	expressions






Insert into keyword:
INSERT INTO table_name
VALUES (value1, value2, value3,…);

INSERT INTO dental_services
VALUES(101, 'Tricky Extraction', 'E', NULL, 0)
New row will be added at the bottom. Order is important.
Must include a value for columns that have no default values or don’t allow null.
PK value can be omitted, identity property will be used.
Alternatively, you can specify the table's column names(so you can use your own order for columns, not the default)
INSERT INTO table_name (column1, column2, column3, ...,columnN)  
VALUES (value1, value2, value3,...valueN);


INSERT INTO dental_services
(service_id, service_description, service_type, hourly_rate, sales_ytd)
VALUES(302, 'Temporary Filling', 'F', 100, 0)

When omit one column its value will be set to NULL.


It is also possible to insert data into specific columns only.

Multiple rows of value can be inserted in one statement.
after VALUE separated by comma.

INSERT INTO dental_services
(service_id, service_description, service_type, hourly_rate, sales_ytd)
VALUES(302, 'Temporary Filling', 'F', 100, 0),(303,'Temp','T',230.0)


One can insert multiple rows
INSERT INTO tablename[(column1, column2, column3, column4)]
SELECT statement

INSERT INTO dental_service_archives(service_id, service_description, service_type, hourly_rate, sales_ytd)
SELECT service_id, service_description, service_type, hourly_rate, sales_ytd
FROM dental_services
or
INSERT INTO dental_service_archives(service_id, service_description, service_type, hourly_rate, sales_ytd)
SELECT *
FROM dental_services
WHERE sales_ytd >= 500
or
INSERT INTO dental_service_archives
SELECT *
FROM dental_services    
(all column must have values.and in order)

INSERT INTO dental_service_archives(service_id, service_description)
SELECT service_id, service_description
FROM dental_services
(omitted column will be null)


Update
UPDATE table_name
SET column1=value1, column2=value2, ...
WHERE condition;

UPDATE departments
SET manager_first_name = 'Bob', manager_last_name = ‘Loblaw'
WHERE department_id = 5

UPDATE items
SET item_cost = item_cost * 1.1
WHERE primary_vendor_id = 5
(select multi rows and apply updates using formula)

UPDATE purchase_orders
SET total_amount = (SELECT SUM(quantity * unit_cost)FROM purchase_order_linesWHERE purchase_order_id = 10)
WHERE purchase_order_id = 1
(Updating A Single Row With A Subquery)



If the WHERE clause is omitted, all records in the table will be updated!

Delete
DELETE FROM table_name
WHERE condition;

DELETE FROM dental_services
WHERE service_id = 301
Deletion can fail if the PK has a reference to other table.


DELETE FROM sales
WHERE amount >= 100
Delete multiple rows.


If you omit the WHERE clause, all records in the table will be deleted!
The DELETE statement removes the data from the table permanently.

A single database can house hundreds of tables

CREATE TABLE

CREATE TABLE table_name
(
column_name1 data_type(size),
column_name2 data_type(size),
column_name3 data_type(size),
....
columnN data_type(size)
);






Numeric

int(can have no length),can be signed or unsigned.
FLOAT(optional display length,decimal place) cannot be unsigned.
DOUBLE(optional display length,decimal place) cannot be unsigned.
Date and Time
DATE - A date in YYYY-MM-DD format.
DATETIME - A date and time combination in YYYY-MM-DD HH:MM:SS format.
TIMESTAMP - A timestamp, calculated from midnight, January 1, 1970
TIME - Stores the time in HH:MM:SS format.

String Type
CHAR(M) - Fixed-length character string. Size is specified in parenthesis. Max 255 bytes.
VARCHAR(M) - Variable-length character string. Max size is specified in parenthesis.
BLOB - "Binary Large Objects" and are used to store large amounts of binary data, such as images or other types of files.
TEXT - Large amount of text data.

The size parameter specifies the maximum length of the table's column.


Data Types for SQL Server

Exact Numerics
bigint
bit
decimal
int
money
numeric
smallint
smallmoney
tinyint


Approximate Numerics
float
real
Date and Time
date
datetime2
datetime
datetimeoffset
smalldatetime
time

Character Strings
char
text
varchar
Unicode Character Strings
nchar
ntext
nvarchar
Binary Strings
binary
image
varbinary
Other Data Types
Cursor
hierarchyid
sql_variant
table
timestamp
uniqueidentifier
xml





NULL
All data types support the concept of NULL
NULL is the absence of a value, it is unknown
For a numeric column NULL is not 0
For a string column NULL is not ''





Primary key keyword
Define it as a primary key

CREATE TABLE Users
(
   UserID int,
   FirstName varchar(100),
   LastName varchar(100),
   City varchar(100),
   PRIMARY KEY(UserID)
);

SQL Constraints
Not null
name varchar(100) NOT NULL

Unique
Primary key
Default
Check
Determines whether the value is valid or not from a logical expression.


During table creation, specify column level constraint(s) after the data type of that column.

Auto increment
the starting value for AUTO_INCREMENT is 1, and it will increment by 1 for each new record.

UserID int NOT NULL AUTO_INCREMENT,
PRIMARY KEY (UserID)

The ALTER TABLE command is used to add, delete, or modify columns constraints in an existing table.

Add new columns
ALTER TABLE People ADD DateOfBirth date;
Default value will set for the new column, if not default value then all null.

Delete columns
ALTER TABLE People
DROP COLUMN DateOfBirth;

Delete entire table
DROP TABLE People;

Rename columns

ALTER TABLE People
CHANGE FirstName name varchar(100);

Rename tables
RENAME TABLE People TO Users;

For SQL Server:

CREATE TABLE TableName (
    ColumnName1 DataType[(size)] [NOT NULL] [DEFAULT value],
    ColumnName2 DataType[(size)] [NOT NULL] [DEFAULT value],

   [CONSTRAINT CK_ConstraintName
               CHECK (ConstraintCheckCondition),]

    CONSTRAINT PK_ConstraintName
               PRIMARY KEY(ColumnName[, ColumnName]

  [,CONSTRAINT FK_ConstraintName
               FOREIGN KEY (ColumnName)
               REFERENCES TableName (ColumnName)
               ON DELETE RESTRICT
               ON UPDATE RESTRICT]
)


Example:

CREATE TABLE employees
(employee_id   INT         NOT NULL,
 employee_name VARCHAR(50) NOT NULL,
 department_id INT,
 job_id        CHAR(3),
 birth_date    DATE,
 gender        CHAR(1),
 salary        DECIMAL(8, 2),
 CONSTRAINT PK_employees PRIMARY KEY(employee_id),
 CONSTRAINT CK_gender CHECK(gender IN ('M', 'F')),
 CONSTRAINT CK_salary CHECK(salary >= 0),
 CONSTRAINT FK_employees_department_id_departments FOREIGN KEY(department_id) REFERENCES departments(department_id))

Table Creation Example with IDENTITY and Constraints Specified Inline
CREATE TABLE employees_with_identity
(employee_id   INT IDENTITY PRIMARY KEY,
 employee_name VARCHAR(50) NOT NULL,
 department_id INT FOREIGN KEY REFERENCES departments(department_id),
 job_id        CHAR(3),
 birth_date    DATE,
 gender        CHAR(1) CHECK(gender IN ('M', 'F')),
 salary        DECIMAL(8, 2) CHECK(salary >= 0))



Create an index
Create [UNIQUE] [CLUSTERED] INDEX index_name
ON table_name
(column_name1 [ ASC/DESC ].
...
column_nameN [ ASC/DESC ]

Ex:
CREATE INDEX STJ_patients_last_name
ON patients
(last_name ASC)


View
In SQL, a VIEW is a virtual table that is based on the result-set of an SQL statement.
It cannot use ORDER BY

CREATE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name;

Once generated, View can be later query as a normal table.
A view always shows up-to-date data.
When use substring in a view columns names must have alias(new name after AS)


Update view

CREATE OR REPLACE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition;

Delete view,
DROP VIEW List;

Stored Procedures
Pieces of executable code stored in the database (small programs)  
Stored procedures require procedural code  
Each database vendor extends SQL with procedural code  
Microsoft uses T-SQL  
Oracle uses Procedural Language SQL (PL/SQL)  
IBM uses SQL Procedural Language (SQL PL)   
MySQL uses SQL/Persistent Stored Module (SQL/PSM)
System Stored Procedures are  pre-defined stored procedures with name:
sp_help ‘column_name'  —see help about a column
sp_server_info    — see info about the server.
Procedures are stored in the data dictionary sys.procedures, sys.sql_modules.



Create Procedure
```sql
CREATE PROCEDURE procedure_name
	@param1 DATATYPE,
	@param2 DATATYPE
AS
…SQL COMMAND WITH @param1, @param2…
```


```sql
CREATE PROCEDURE update_items_item_cost    
	@increase DECIMAL(3, 2),    
	@vendor_id INT  = 0    - - SET default value after
AS  
UPDATE items    
	SET item_cost = item_cost * (1 + @increase)    
	WHERE primary_vendor_id = @vendor_id;  
```


Alter a Procedure
```sql
ALTER PROCEDURE procedure_name
	@param1 DATATYPE,
	@param2 DATATYPE
AS
…SQL COMMAND WITH @param1, @param2…
```
Delete a Procedure
```sql
DROP PROCEDURE procedure_name;
```
Run Procedure
```sql
EXEC sp_help  
EXEC procedure_name ‘column_name’;
```

Can accept command line parameters, separated by commas
functions are not accepted, new variables need to be declared to store values from function.
EXEC procedure_name @param1=‘value1’, @param2=‘value2’;

Parameters can be positional or named  
EXEC procedure_name value1 value2;


BEGIN-END
Used to enclose a block of statements, like {}.
```sql
BEGIN
	SET…
	SET…
END
Declare
Declare local variables
DECLARE @variable_name DATATYPE;
```
SET
It is used to assign value.
```sql
SET @variable_name = value;  
SET @variable_name = NULL;  
SET @variable_name = …SQL Command that return a single value…
```

IF
```sql
IF @ref_error = 1    
SET @error_msg = 'NOT FOUND';
```

IF/ELSE statements
```sql
IF @ref_error = 0    
	SET @error_msg = 'FOUND';  
ELSE    
	SET @error_msg = 'NOT FOUND';  
```
CASE statements
```sql
CASE @evaluation  
WHEN 100     
	THEN UPDATE employees SET salary = salary * 1.3;  
WHEN 90     
	THEN UPDATE employees SET salary = salary * 1.2;  
WHEN 80     
	THEN UPDATE employees SET salary = salary * 1.1;  
ELSE UPDATE employees SET salary = salary * 1.05;  
END  
```

Or

```sql
CASE  
WHEN @evaluation = 100     
	THEN UPDATE employees SET salary = salary * 1.3;  
WHEN @evaluation =  90     
	THEN UPDATE employees SET salary = salary * 1.2;  
WHEN @evaluation =  80     
	THEN UPDATE employees SET salary = salary * 1.1;  
ELSE UPDATE employees SET salary = salary * 1.05;  
END  
```
WHILE Loop
```sql
WHILE @@FETCH_STATUS = 0  
BEGIN   
	 <loop processing>  
END  
```
BREAK
it is used to break the loop.

CONTINUE
Used to advance to the next iteration of a WHILE loop.

Cursor
Used to access a SELECT result set one row at a time
Steps to use a cursor  
DECLARE a cursor with a SELECT statement  
OPEN the cursor  
This executes the SELECT statement and populates the cursor  
FETCH one row at a time from the result set INTO variables  
Each column fetched must have a correlating variable  
Perform whatever processing desired for each row  
CLOSE the cursor  
DEALLOCATE the cursor

Example:
```sql
ALTER PROCEDURE update_items_item_cost
  @increase DECIMAL(3, 2),
  @vendor_id INT,
  @update INT = 0, -- If @update = 1, perform update, else show what would be updated
  @number_of_records INT OUTPUT
AS
  DECLARE items_cursor CURSOR
    FOR SELECT item_cost
        FROM items
        WHERE primary_vendor_id = @vendor_id
    FOR UPDATE;
  DECLARE @item_cost DECIMAL(9, 2);
BEGIN
  IF @update = 1
  BEGIN
    SET @number_of_records = 0;
    OPEN items_cursor;
    FETCH NEXT FROM items_cursor
      INTO @item_cost;
    WHILE @@FETCH_STATUS = 0
    BEGIN
      SET @item_cost = @item_cost * (1 + @increase);
      UPDATE items
        SET item_cost = @item_cost
        WHERE CURRENT OF items_cursor;
      SET @number_of_records = @number_of_records + 1;
      FETCH NEXT FROM items_cursor
        INTO @item_cost;
    END
  CLOSE items_cursor;
  END
  ELSE -- No Update
    SELECT item_id, vendor_name, item_cost AS [existing_cost], item_cost * (1 + @increase) AS [proposed_cost]
    FROM items
    JOIN vendors
    ON primary_vendor_id = vendors.vendor_id
    WHERE primary_vendor_id = @vendor_id;
  DEALLOCATE items_cursor;
END

PRINT '**********Before Update**********'
SELECT * FROM items WHERE primary_vendor_id = 1;

-- Need to declare a variable to receive output
DECLARE @num_of_rows INT;

PRINT '**********No Update**********'
EXEC update_items_item_cost @increase=0.25, @vendor_id=1, @update=0, @number_of_records=@num_of_rows OUTPUT;
SELECT @num_of_rows AS [number_of_rows];

PRINT '**********After No Update**********'
SELECT * FROM items WHERE primary_vendor_id = 1;

PRINT '**********Update**********'
EXEC update_items_item_cost @increase=0.25, @vendor_id=1, @update=1, @number_of_records=@num_of_rows OUTPUT;
SELECT @num_of_rows AS [number_of_rows];

PRINT '**********After Update**********'
SELECT * FROM items WHERE primary_vendor_id = 1;
```




@@FETCH_STATUS
Returns the status of the last cursor FETCH statement  
0 = The FETCH statement was successful  
-1 = The FETCH statement failed or the row was beyond the result set  
-2 = The row fetched is missing  



Trigger
A trigger is a special stored procedure attached to a specific table.

It is Event-driven, it is "Fired" automatically in response to event

Can’t pass values into a trigger, values can be declared inside a trigger.

CREATE TRIGGER employees_insert    
	ON employees    
	AFTER INSERT, UPDATE   #triggered by both insert and update operation
AS    
	UPDATE company_stats      
		SET number_of_employees = number_of_employees + 1;  


During trigger execution, two special tables are used: deleted and inserted  
SQL Server automatically creates and manages these tables  
They have identical schema to the table being modified  

```sql
CREATE TRIGGER trigger_name    
	ON table_name    
	AFTER UPDATE  
AS    
	DECLARE @new_data MONEY;    
	DECLARE @old_data MONEY;  
BEGIN    
	SET @newData = (SELECT columnName FROM inserted);    
	SET @oldData = (SELECT columnName FROM deleted);    
	IF @new_data > (@old_data * 1.5)      
		ROLLBACK TRANSACTION;     - - cancel update
END  
```

Improvement for updating multiple records

ALTER TRIGGER employees_update    
	ON employees    
	AFTER UPDATE  
AS  
BEGIN    
	IF EXISTS (SELECT i.salary FROM inserted i                 
				JOIN deleted d                 
				ON i.employee_id = d.employee_id                 
				WHERE i.salary > (d.salary * 1.5))    
	ROLLBACK TRANSACTION;  
END  


Trigger with Cursor
```sql
ALTER TRIGGER employees_update    
	ON employees    
	AFTER UPDATE  
AS    
	DECLARE employees_cursor CURSOR      
		FOR SELECT i.salary, d.salary          
			FROM inserted i          
			JOIN deleted d          
			ON i.employee_id = d.employee_id;    
	DECLARE @new_salary MONEY;    
	DECLARE @old_salary MONEY;  
BEGIN    
	OPEN employees_cursor;    
  FETCH NEXT FROM employees_cursor      
		INTO @new_salary, @old_salary;    
	WHILE @@FETCH_STATUS = 0    
	BEGIN      
		IF @new_salary > @old_salary * 1.5      
		BEGIN        
			ROLLBACK TRANSACTION;        
			BREAK;      
		END      
		FETCH NEXT FROM employees_cursor        
			INTO @new_salary, @old_salary;    
	END    
	CLOSE employees_cursor;  
END  
```
To delete an existing trigger use:  
DROP TRIGGER Trigger_Name  


Every CREATE TRIGGER statement generates entries in  
sys.triggers  
sys.trigger_events  
sys.events  
sys.sql_modules

TRANSCATION
ROLLBACK

SELECT * FROM physicians WHERE physician_id = 2;SELECT * FROM patients WHERE patient_id = 1251;BEGIN TRANSACTION;UPDATE physicians SET specialty = 'Hematology' WHERE physician_id = 2;UPDATE patients SET allergies = 'Almonds' WHERE patient_id = 1251;SELECT * FROM physicians WHERE physician_id = 2;SELECT * FROM patients WHERE patient_id = 1251;ROLLBACK TRANSACTION;SELECT * FROM physicians WHERE physician_id = 2;SELECT * FROM patients WHERE patient_id = 1251;

Commit
SELECT * FROM physicians WHERE physician_id = 2;SELECT * FROM patients WHERE patient_id = 1251;BEGIN TRANSACTION T1;UPDATE physicians SET specialty = 'Hematology' WHERE physician_id = 2;UPDATE patients SET allergies = 'Almonds' WHERE patient_id = 1251;SELECT * FROM physicians WHERE physician_id = 2;SELECT * FROM patients WHERE patient_id = 1251;COMMIT TRANSACTION T1;SELECT * FROM physicians WHERE physician_id = 2;SELECT * FROM patients WHERE patient_id = 1251;







SQL Script
the script put multiple SQL statement together one by one in a file.
the script file has an extension of .sql
each statement requires; in the end
Excel can build inserts statements
When work with scripts in database management software always select the correct table or database before execution.

Script file comments
Single line comments begin with ``--``
Multi line comments are bounded with ``/* */``

A group of sql command is called a batch in sql script.

GO statements is used at the end of each batch, no ; followed. It can be followed by an integer that repeats the batch for certain time. When a batch fails other batches will still be executed.

Some CREATE and INSERT statements require that they are the first statement in a batch.

SET commands can be used to change session settings.
SET NOCOUNT ON
Suppress INSERT, UPDATE and DELETE completion messages
SET DATEFORMAT ymd
Sets the date format to YYYY-MM-D

SET Examples:

SET NOCOUNT ON

-- Set date format to year, month, day
SET DATEFORMAT ymd;

-- Make the master database the current database
USE master

-- If database co859 exists, drop it
IF EXISTS (SELECT  * FROM sysdatabases WHERE name = 'co859')
  DROP DATABASE co859;
GO

PRINT ‘Verification';
//Print statement in the script print string in console, when it is executed. For Microsoft SQL manegement output setting need to be changed to text.

SET DATEFORMAT format
format can be:
dmy (Preferred in much of the world)
mdy (Preferred in USA)
ymd (Unambiguous, best choice, SQL Server default)
ydm (Should be avoided)
myd (Should be avoided)
dym (Should be avoided)



-- Create the co859 database
CREATE DATABASE co859;
GO

-- Make the co859 database the current database
USE co859;
