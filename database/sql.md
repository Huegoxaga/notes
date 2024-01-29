# SQL

## History

- It started life as SEQUEL in 1974, an IBM product
- In 1980 it was renamed SQL
- There is a SQL standard maintained by the American National Standards Institute (ANSI). Most database vendors extend the standard
- PhpMyAdmin is a tool that helps manage database using a web interface, it is written in PHP.
- The easiest way to get MySQL and PHPMyAdmin is to install free tools like XAMPP or WAMP, Then a database server can be installed on the computer and Database management can be accessed from browser using url: localhost:8080/myphpadmin.
  (userid:root, password:"")

## Concepts

- Compare with NoSQL, SQL it good at making complicated anlytics queries. NoSQL is good at getting direct or simple access to massive data
- Column Sometimes referred to as a field, contains the same type of information for every record in table.
- Row Sometimes referred to as a record
  Table is a collection of related rows
- Database is a collection of related tables and other objects
- Entity is represented by a table, it is a thing or a person etc.
  Cardinality can be used to represent the Entity relationship(one to one, one to many etc.), when the Entity can be zero it is optional.
- A weak entity is an entity that cannot be uniquely identified by its attributes alone; therefore, it must use a foreign key.
- Relationship has degree, A unary relationship(one entity, recursive relationship), binary relationship(two entities), ternary relationship(three entities), four-entity relationship(four entities), Ternary (and higher) relationships are usually represented by a series of binary relationships.
- Attribute is represented by column headings.
- Data Dictionary
  - Also called Metadata System Tables (SQL Server) System dictionary is the repository of all data definitions for all objects within the scope of the database. It contains meta-data (Table name, column name, data constraints, primary and foreign keys, index)
- The System Catalog
  - A detailed system data dictionary that describes all objects in the database
- For System table of the SQL Server
  - Starting with SQL Server 2005, all System Tables are hidden and inaccessible directly A large collection of System Views have been created to accommodate accessing of database’s metadata Two schemas INFORMATION_SCHEMA sys
- A primary key is a single field in the table that uniquely identifies (unique nonempty values)the table records. primary auto creates index.
- Foreign Key is a field a reference a PK from another table.
- A good choice for primary keys is a Meaningless But Unique Number (MBUN)•Start at 1 and keep incrementing•The int datatype provides 2,147,483,647 possible values•The bigint datatype provides 9,223,372,036,854,775,807 possible values (> 9 quintillion)
- Another possible choice is the Globally Unique Identifier (GUID)–Also known as Universally Unique Identifier (UUID)•128 bit integer, typically expressed as 32 hex digits in the pattern 8-4-4-4-12–Example: 678e6b75-29ad-4cba-8d78-5ad68aad414b•Good for decentralized systems
- Naming Conventions
  - Do not put spaces in the names of anything you create
  - Do not use descriptive prefixes or postfixes such as tbl
  - Use all lowercase and divide word boundaries with `_`, database name uppercase.
  - [Click here to see more](http://www.sqlstyle.guide).
- IDENTITY Property
  - SQL Server provides an optional identity property to simplify creating MBUNs•The identity property would be added to the definition of the primary key column when a table is being created.
  - IDENTITY [ (seed , increment) ] Seed and increment are optional, both default to 1
  - when insert row without specifying the value for PK, default rules are used.
  - Using an identity property simplifies INSERTs.
  - Without an identity property, the primary key must first be determined and then specified
  - With an identity property, the primary key is left off the INSERT statement and the database automatically keeps track of it and provides it when necessary.
- Determinant
  - An attribute whose value determines the value for another attribute
  - Usually the primary key.
- Functional Dependency
  - Relationship between a determinant A and dependent attribute B.
  - Represented by A -> B
- Candidate Key
  - One of the attributes that could be used as a primary key.
- Relation
  - A table with rows and columns •Each row contains information on an instance of an entity
- Tuple is a row of data
- When design database, identity the entities then find their relationship.
- Many-to-Many relationship cannot be represented in the database. Hence, an intersection entities is required.
- Atomic attribute
  - A component of the record definition that is used to describe an entity A field Unique meaningful names Example: postal_code Composite attribute Composed of atomic attributes, each defined in the data dictionary Address is comprised of street_address city province_id postal_code
- Derived attribute
  - An attribute whose value is obtained by applying a formula to other data elements Examples: sales commission = sales _ percentage age = DATEDIFF(YEAR, birth_date, GETDATE()) Multi-valued attribute An attribute with multiple possible values A employee can have more than one skill Alias Synonym A different name for a data element with the same meaning ``SELECT COUNT(_) AS total FROM patients``
- Domain
  - The set of possible values an attribute can take on Concatenated Key Also known as Composite Key, Compound Key Two or more attributes taken together to uniquely identify a record Examples: patient_id, admission_date in admissions table purchase_order_id, line_num in purchase_order_lines table Secondary Key Requires an index may not be unique Example: last_name Sort Key Used to physically sequence a file Example: seniority listing of employee records
- Foreign Key
  - A field (or multiple fields) in a table that uniquely identifies a row of another table (or the same table) Example: nursing_unit_id in admissions table Entity Occurrence Represented by a record with actual data values in it, or a row in a table Schema The definition of an entire database In SQL Server, schemas are used as containers to organize database objects
- Indexes is used to improve only the access time.
- Clustered indexes is the indexes that are associated with a column, usually the primary key. when create is physical sort and associated column data. Unclustered index store unsorted data on the store device and use pointers to associate the data with index.
- Multiple SQL statement can bu put in order, end with ;.
- Normalization Quick Summary•
  - 0NF - tables without normalization.
  - 1NF - Eliminate Repeating Groups And Derived Attributes–Make a separate table for each set of related attributes, and give each table a primary key•
  - 2NF - Eliminate Redundant Data–If an attribute depends on only part of a composite key, remove it to a separate table•
  - 3NF - Eliminate Columns Not Dependent On Key–If attributes do not contribute to a description of the key, remove them to a separate table
- OLTP(Online Transaction Process) uses normalized data.
- OLAP(Online Analytical Process) and BI(Business Intellige) and Data warehouse stores denormalized data.
- Business Rules are specifications that preserve the integrity of a conceptual or logical data model. They are enforced by for types of rules.
- Entity integrity(PK)
- Referential integrity(FK)
- Domains(Value Boundary, check)
- Triggering operations(?)
- View
  - View is a virtual table based on one or more tables.
  - The View result set is not permanently stored in the database, but generated each time it is used
  - Shows up in INFORMATION_SCHEMA.VIEWS &INFORMATION_SCHEMA.TAB
- SQL Statements have two types.
  - Data Definition Language (DDL)
    - CREATE table
    - CREATE index
  - Data Manipulation Language (DML)
    - SELECT
    - INSERT
    - UPDATE
    - DELETE
- Depending on the database vendor, data can be case sensitive `'M' <> 'm'`
  - Data in Oracle database is case sensitive
- SQL is not case sensitive
  - Convention is to capitalize keywords and use lower case for tables, columns, etc
- SQL ignores whitespace
  - Convention is to capitalize keywords and place each clause on its own line
- For Character and string data single quotes are recommended and generally used.
- multiple queries or commands can be entered at the same time and separate by ; at end of each line.
- SQL is case insensitive. However uppercase is preferred for all commands.
- SQL syntax is not sensitive to indentations.
- `dual` is a "dummy" table in Oracle that has 1 row and 1 column
  – Used whenever a single value is expected from a `SELECT ... FROM dual;` syntax

## Database Tools

- Tools for connecting to the database server for testing and maintainance purpose

### SQL Developer

- Used for Oracle Database
- [Click](https://github.com/oracle/docker-images/blob/main/OracleDatabase/SingleInstance/README.md) to see to installation instruction from oracle docker image repo
  - Oracle 18.4 Express Edition has SID as `xe`
- SET command
  - it only effect the current session
    - To set all sessions, a connection startup script can be created and set in `Tools / Preferences...`
  - `SET PAGESIZE 1000` set output page size for text output
    - default is `14`
- `Run Statement` - runs the current statement and presents the query result in a grid
- `Run Script` - runs the whole script and presents the script output as text
- If a section of the script is highlighted and `Run Statement` or `Run Script` is pressed, only the highlighted section will run
  - This is a good way to test a subquery to ensure that it’s working as expected
- `History` - returns all previously ran commands
  – Double-clicking one of them brings them back into the Worksheet tab where they can be run again or edited
- Enable line numbers - right-click the line gutter (left margin of the code editor) and select Toggle Line Numbers

### SQL Command Line

- Available on all installs of Oracle, known as `SQL*Plus`
- If something is wrong with database, may be only tool that allows database access
- For mac, to install
- It can run any `PL/SQL` query
  - SQL statements must be terminated by `;`
- run `sqlplus` to open the tool
  - or, `sqlplus <user>/<password> as <role>`
  - or, `sqlplus <user>/<password>`
  - Will be prompted for credentials
- Useful command:
  - `show user`
  - `help`
  - `connect` (prompted for credentials)
    - or `connect <user>/<password> as <role>`
  - `disconnect`
  - `/` to rerun previous SQL command
  - `help index` see a list of `SQL*Plus` commands
  - `help <command>` see help for a certain command
  - `@<filename>.sql` run a `sql` script
  - `quit`

### pgAdmin

- A web app for managing Postgres database

## Data Types

### General Data Types

#### Numeric

- int(can have no length),can be signed or unsigned.
- FLOAT(optional display length,decimal place) cannot be unsigned.
- DOUBLE(optional display length,decimal place) cannot be unsigned.

#### Date and Time

- DATE - A date in YYYY-MM-DD format.
- DATETIME - A date and time combination in YYYY-MM-DD HH:MM:SS format.
- TIMESTAMP - A timestamp, calculated from midnight, January 1, 1970
- TIME - Stores the time in HH:MM:SS format.

#### String Type

- CHAR(M) - Fixed-length character string. Size is specified in parenthesis. Max 255 bytes
- VARCHAR(M) - Variable-length character string. Max size is specified in parenthesis
- BLOB - "Binary Large Objects" and are used to store large amounts of binary data, such as images or other types of files.
- TEXT - Large amount of text data.
- The size parameter specifies the maximum length of the table's column.

### SQL Server Data Type

#### Exact Numerics

- bigint
- bit
- decimal
- int
- money
- numeric
- smallint
- smallmoney
- tinyint

#### Approximate Numerics

- float
- real

#### Date and Time

- date
- datetime2
- datetime
- datetimeoffset
- smalldatetime
- time

#### Character Strings

- char
- text
- varchar

#### Unicode Character Strings

- nchar
- ntext
- nvarchar

#### Binary Strings

- binary
- image
- varbinary

#### Other Data Types

- Cursor
- hierarchyid
- sql_variant
- table
- timestamp
- uniqueidentifier
- xml

### Postgres Data Types

- Array is supported for all types

### Oracle Data Types

- VARCHAR2(maximum length)
  – Variable length character data
  – Maximum length up to 32,767 bytes
  – Maximum length of a database column is 4,000 bytes
  – NVARCHAR2 Unicode version of VARCHAR2
  – For Oracle databases: VARCHAR is synonymous with VARCHAR2; to avoid possible changes in behavior, always use VARCHAR2 to store variable-length character strings
- CHAR(max)
  – Fixed length character data, blank padded if necessary
  – Optional maximum length up to 32,767 bytes
  – Maximum length of a database column is 2,000 byte
  – Defaults to 1 byte
  – NCHAR Unicode version of CHAR
- NUMBER[(precision, scale)]
  – Fixed or floating point number of almost any size
  – Precision is total number of digits
  – Scale determines where rounding occurs
  – If scale is omitted, it is 0 and value becomes integer (default)
  – Maximum precision is 38 digits–Scale can be from 0 to 127
- BINARY_INTEGER
  - Stores signed integer values
  - Compares to NUMBER, but takes up less space and is faster in calculations
  - -2,147,483,747 to 2,147,483,747
- DATE
  - Stores fixed length date values
  - January 1, 4712 BC to December 31, 9999 AD
    – Start date based on Julian Day Number used in astronomy
  - When stored in a database column, date values include the time of day in seconds since midnight
- TIMESTAMP
  - Extension of DATE type
  - Stores fixed length date values with precision down to a fraction of a second, with up to 9 places after the decimal (default is 6)
  - Example: 28-SEP-1966 09.51.44.000000 AM
- BOOLEAN
  - Stores the value TRUE or FALSE as well as NULL
  - PL/SQL only, database tables don't support this type
- LONG
  - Stores variable length character strings
  - LONG is like VARCHAR2, but it’s maximum length is 2GB
- LONG RAW
  - Stores raw binary up to 2GB
- LOB
  - Large OBject
  - 4 types: BLOB, CLOB , NCLOB and BFILE
  - Stores binary objects such as image or video files up to 4GB
  - BLOBs and CLOBs are functionally equivalent
  - LOB types stored in the database, BFILE stored outside the database
  - NCLOB Unicode version of CLOB
- ROWID
  - Internally, every Oracle table has a ROWID pseudocolumn, which stores binary values called ROWIDs
  - ROWIDs uniquely identify rows (within a table) and provide the fastest way to access particular rows
  - Use the ROWID data type to store ROWIDs in a readable format
- ROWNUM
  - ROWNUM is a pseudocolumn that indicates the order of the row within the result set
  - Determined before ORDER BY
  - Can be used to approximate SQL Server's TOP clause
- ROWTYPE
  - A list column types from a table
  - `rowtypeName tableName%ROWTYPE;`
- RECORD
  - user defined list of column types
  ```sql
  DECLARE
    type books is record
        (title varchar(50),
        author varchar(50),
        subject varchar(100),
        book_id number);
    book1 books;
    book2 books;
  ```

## SQL Syntax

### Get Database Info

- The following SQL examples work for mySQL, variation for other SQL will be noted
  - Check server version
    ```sql
    select @@version
    ```
  - the command lists the databases managed by the server.
    ```sql
    SHOW DATABASES MySQL
    .databases in SQL Server
    ```
  - display all of the tables in the currently selected database.
    ```sql
    SHOW TABLES MySQL
    .tables in SQL Server
    ```
  - displays information about the columns in a given table.
    ```sql
    SHOW COLUMNS FROM tablename
    ```

### SELECT

- The `SELECT` statement is used to query data from a database. Query results are stored in a table called result-set.
- A `SELECT` statement retrieves zero or more rows from one or more database tables.
- `FROM` is required expect for SQL Server.
  ```sql
  SELECT column_list
  FROM table_name
  ```
- SELECT can be followed by a aggregating function
  - Aggregating functions will ignore columns with NULL values
  - AVG – Computes the average value of the column
  - COUNT – Counts the number of rows
  - MAX – Determines the maximum value
  - MIN – Determines the minimum value
  - SUM – Totals the numeric values
    ```sql
    SELECT COUNT(*)FROM patients
    SELECT AVG(patient_weight)FROM patients
    SELECT MIN(last_name)FROM patients
    ```
- Coalesce - takes any number of columns name and returns the first value that is not null, it is used to set a default value if returns null
  ```sql
  SELECT first_name, last_name, COALESCE(allergies, 'No known allergies')FROM patients
  -- For each returning records, When allergies has a value it will return the value
  -- If allergies is NULL, it will return 'No known allergies'
  ```
- `NVL()` function: if the first argument is NULL, return the second argument
- Case Function - Case function allows boolean logic in a SQL statement
- If no conditions are true and there is no else clause, null is returned
  ```sql
  SELECT first_name, last_name,
    CASE WHEN patient_height > 170 THEN 'Tall'
    WHEN patient_height > 120 THEN 'Average'
    ELSE 'Short'
    END
  FROM patients
  ```
- Case function can be aliased as a column to enhance readability
  ```sql
  SELECT first_name, last_name,
    CASE WHEN patient_height > 170 THEN 'Tall'
    WHEN patient_height > 120 THEN 'Average'
    ELSE 'Short'
    END height
  FROM patients
  ```
- Columns have fully qualified names as `tablename.columnname` is acceptable. It is used to distinguish same columns names from different tables.
- Multiple columns can be queried in one command separated by commas.
- `*` represent all.
- `DISTINCT` qualifier return unique value of columns
  ```sql
  SELECT DISTINCT column_name1, column_name2
  FROM table_name;
  ```
- `LIMIT` keyword shows only specific number of d rows.
  ```sql
  SELECT ID, FirstName, LastName, City
  FROM customers LIMIT 5;
  ```
  ```sql
  Select 4 start after 3rd(counting from zero)
  SELECT ID, FirstName, LastName, City
  FROM customers LIMIT 3, 4;
  ```
- Im SQL Server use TOP, The TOP clause sets a maximum number of rows that can be retrieved
  ```sql
  SELECT TOP 5 *
  FROM patients;
  and
  SELECT TOP 5 PERCENT *
  FROM patients;
  ```
- ORDER BY is used with `SELECT` to sort the returned data.
  - By default the order is `ASC`, use `DESC` to get results in descending order
- Can order by multiple columns separate by commas. Sort the first column first then second.
  ```sql
  SELECT * FROM customers
  ORDER BY FirstName;
  Default uses ascending order.
  Or use
  ORDER BY Salary DESC
  ```
- Where keyword is used to add conditions.
  - Predicates are used in the `WHERE` clause to specify conditions, Basic Predicate:
    - `=, <>, <, >, <=, >=`
    - BETWEEN Predicate
    - EXISTS Predicate
    - IN Predicate
    - LIKE Predicate
    - NULL Predicate
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
- Single quotation marks (') is used for text.
  ```sql
  SELECT ID, FirstName, LastName, City
  FROM customers
  WHERE City = 'New York';
  ```
- single qoute can also be the escape characters. Ex: Can''t
- `IN` keyword includes all satisfied columns.
  ```sql
  SELECT * FROM customers
  WHERE City IN ('New York', 'Los Angeles', 'Chicago');
  ```
- The `NOT IN` operator allows you to exclude a list of specific values from the result set. Result set must included in bracket, even there is only one element in it. result set can be a column returned from other SELECT query.
- `ANY` and `SOME` checks whether any value in the list makes the condition true
- `ALL` checks to ensure that all values in the list are true
  ```sql
  SELECT first_name, last_name, patient_height
  FROM patients
  WHERE gender = 'M'
  AND patient_height > ALL (
    SELECT patient_height
    FROM patients
    WHERE gender = 'F')
  ```
- EXISTS returns true if a subquery contains any rows.
- `IS` can be used with `NULL`. or `IS NOT NULL`
  - `WHERE column = NULL` will not return anything
  - `NULL + 5` will return `NULL`
    ```sql
    -- This select all row of patients tables that exist in the unit_dose_orders table
    SELECT first_name, last_name
    FROM patients
    WHERE EXISTS (SELECT * FROM unit_dose_orders WHERE unit_dose_orders.patient_id = patients.patient_id)
    SELECT *
    FROM vendors
    WHERE NOT EXISTS (SELECT * FROM purchase_orders WHERE purchase_orders.vendor_id = vendors.vendor_id)
    -- This select all row of patients tables that don’t exist in the unit_dose_orders table
    SELECT * FROM patients
    WHERE allergies IS NULL;
    ```
- `AND` and `OR` can be used to connects conditions for WHERE statement.
- `CONCAT` combines two column in a format
  - A concatenation results in a new column. The default column name will be the CONCAT
    ```sql
    SELECT CONCAT(FirstName, ', ' , City) FROM customers;
    ```
- `AS` is used for a column name change(Alias)
- `AS` is optional
- Use double qoute for alias name to reserves capitalization, e.g. `AS "Name"`(works when database support case sensitive data)
  ```sql
  SELECT CONCAT(FirstName,', ', City) AS new_column
  FROM customers;
  ```
- Arithmetic operator can also be used in query.
  ```sql
  SELECT ID, FirstName, LastName, Salary+500 AS Salary
  FROM employees;
  ```
- Upper and lower function change upper lower cases.
  ```sql
  SELECT FirstName, UPPER(LastName) AS LastName
  FROM employees;
  SELECT FirstName, LastName AS LastName
  FROM employees
  WHERE LOWER(LastName) like 'smi%';
  ```
- GROUP BY
  - It can be used to deal with results of the column that has different rows.
  - GROUP BY must be used in conjunction with an aggregating function
  - Does not sort automatically, still need ORDER BY for sort
  - Multiple groupings are allowed
    ```sql
    SELECT province_id, city, COUNT(*)
    FROM patients
    GROUP BY province_id, city
    ```
- HAVING
  - It is like another WHERE clause for grouped columns.
  - Used with GROUP BY
  ```sql
  SELECT nursing_unit_id, COUNT(*)
  FROM admissions
  GROUP BY nursing_unit_id
  HAVING COUNT(*) >= 340
  ```
- Subqueries is a query that has queries inside.
  - the inner query is processed first.
  - Enclose the subquery in parentheses.
  - Subquery Returns Single Rows
  ```sql
  SELECT FirstName, Salary FROM employees
  WHERE  Salary > (SELECT AVG(Salary) FROM employees)
  ORDER BY Salary DESC;
  ```
  - Subquery Returns Multiple Rows
  ```sql
  SELECT nursing_unit_id, patient_id, admission_date
  FROM admissions
  WHERE nursing_unit_id IN(SELECT nursing_unit_idFROM nursing_unitsWHERE beds < 10)
  ORDER BY nursing_unit_id, patient_id
  ```
  - Nested Subquery
  ```sql
  SELECT nursing_unit_id, COUNT(*) AS patients
  FROM admissionsWHERE nursing_unit_id IN
  (SELECT nursing_unit_id
  FROM nursing_units
  WHERE beds >(SELECT AVG(beds)FROM nursing_units))
  GROUP BY nursing_unit_id
  ```
  - Subquery as a Table
  ```sql
  SELECT * FROM (
    SELECT province_id, city, COUNT(*) citycount
    FROM patients
    GROUP BY province_id, city)
    WHERE city LIKE 'H%'
  ```
- The like keyword can be used to specify a pattern, pattern is represented by:
  - `_` any value.
  - `%` any group of values
  ```sql
  SELECT * FROM employees
  WHERE FirstName LIKE 'A%';
  ```
- This choose any text begin with `A`.
- NOT LIKE picks anything that not in this pattern.
- Clauses in SELECT should follow orders as `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`

### Union

- `UNION` combines two or more `SELECT` statements with same type of columns(data type), removes any existing duplicates
  - If one column can’t match the data type, use null instead
  ```sql
  SELECT FirstName, LastName, Company FROM businessContacts
  UNION
  SELECT FirstName, LastName, NULL FROM otherContacts;
  ```
- `UNION ALL` works faster, and it does not remove duplicate rows

### Built-in Function

- Scalar Functions – Returns Single value.
- Column Function - works with a set of value.

- Mathematical Functions
  - ABS
  - ACOS
  - ASIN
  - ATAN
  - ATN2
  - CEILING
  - COS
  - COT
  - DEGREES
  - EXP
  - FLOOR
  - LOG
  - LOG10
  - PI
  - POWER
  - RADIANS
  - RAND
  - ROUND
  - SIGN
  - SIN
  - SQRT
  - SQUARE
  - TAN
- String Functions
  - ASCII
  - CHAR
  - CHARINDEX
  - DIFFERENCE
  - LEFT
  - LEN
  - LOWER
  - LTRIM
  - NCHAR
  - PATINDEX
  - QUOTENAME
  - REPLACE
  - REPLICATE
  - REVERSE
  - RTRIM
  - SOUNDEX
  - SPACE
  - STR
  - STUFF
  - SUBSTRING
  - UNICODE
  - UPPER
- Date And Time Functions
  - CURRENT_TIMESTAMP
  - DATEDIFF(datepartType, startdate, enddate)
    - datepartType: year, quarter, month, dayofyear, day, week, hour, minute, second, millisecond, microsecond, nanonsecond
    - Be careful, DATEDIFF with YEAR does not calculate age. A person born on November 15, 1999 is not 19 on October 2, 2018. Use the following way to calculate.
    ```sql
    SELECT DATEDIFF(DAY, '2017-01-01', '2018-09-01')
    Result is 608 days
    SELECT DATEDIFF(MONTH, '2017-01-01', '2018-09-01')
    Result is 20 months
    SELECT DATEDIFF(YEAR, '1999-11-15', '2018-10-02')
    Result is 19 years
    ```
    ```sql
    SELECT FLOOR(DATEDIFF(DAY, '1999-11-15', '2018-10-02') / 365.25)
    Result is 18 years
    ```
  - DATEDIFF extracts the YEAR from both dates and performs subtraction without considering the months or days
  - DATEADD(datepart, number, date)
    ```sql
    SELECT DATEADD(DAY, 60, '2018-09-01')
    Result is 2018-10-31
    SELECT DATEADD(MONTH, 5, '2018-09-01')
    Result is 2019-02-01
    SELECT DATEADD(YEAR, 3, '2018-09-01')
    Result is 2021-09-01
    ```
  - use DATEADD with negative values
    ```sql
    SELECT DATEADD(DAY, -60, '2018-09-01')
    Result is 2018-07-03
    SELECT DATEADD(MONTH, -5, '2018-09-01')
    Result is 2018-04-01
    SELECT DATEADD(YEAR, -3, '2018-09-01')
    Result is 2015-09-01
    ```
  - DATENAME(datepart, date) works like DATEPART but returns a string instead of an integer
    ```sql
    SELECT encounter_date_time,
          DATENAME(HOUR, encounter_date_time) AS [hour],
          DATENAME(MINUTE, encounter_date_time) AS [minute],
          DATENAME(SECOND, encounter_date_time) AS [second]
    FROM encounters
    ```
  - DATEPART(datepart, date)
    ```sql
    SELECT encounter_date_time,
          DATEPART(HOUR, encounter_date_time) AS [hour],
          DATEPART(MINUTE, encounter_date_time) AS [minute],
          DATEPART(SECOND, encounter_date_time) AS [second]
    FROM encounters
    ```
    ```sql
    SELECT  DATEPART(YEAR, Timestamp) AS 'Year',
            DATEPART(MONTH, Timestamp) AS 'Month',
            DATEPART(DAY, Timestamp) AS 'Day',
            COUNT(*) AS 'Visits'
    FROM      tblVisits
    GROUP BY  DATEPART(DAY, Timestamp),
              DATEPART(MONTH, Timestamp),
              DATEPART(YEAR, Timestamp)
    ORDER BY  'Year',
              'Month',
              'Day'
    ```
  - DAY(date) extracts the day of the month
  - MONTH(date) extracts the month of the year
  - YEAR(date) extracts the year
    ```sql
    SELECT birth_date,
          YEAR(birth_date) AS [year],
          MONTH(birth_date) AS [month],
          DAY(birth_date) AS [day]
    FROM patients
    ```
  - The GETDATE function returns the current date with time
    ```sql
    SELECT GETDATE()
    ```
  - To get the date without the time, the CONVERT function can be used
    ```sql
    SELECT CONVERT(DATE, GETDATE())
    ```
  - Calculate patient age
    ```sql
    SELECT birth_date,
          FLOOR(DATEDIFF(DAY, birth_date, GETDATE()) / 365.25)
    FROM patients
    ```
  - GETUTCDATE
  - ISDATE
  - MONTH
  - SWITCHOFFSET
  - TODATETIMEOFFSET
  - YEAR

### Extensions

- It provides additional functions to the database engine
- `CREATE EXTENSION extension_name;` enable extension to the database
- `DROP EXTENSION extension_name;` disable extension from the database

#### postgis

- A Postgres extension for geo-database support
- `CREATE EXTENSION postgis;` enable extension
- `SELECT PostGIS_Full_Version();` get the extension version
- `CREATE TABLE test (id serial NOT NULL, geom geometry(LineString,4326),` Create a table store geoinfo
  - `LineString` is the geo data type that will be stored in the column `geom`
- `INSERT INTO public.test (geom) VALUES (ST_GeomFromText('LINESTRING(0 0, 10 10, 20 20)', 4326));` Insert geometry
  - `ST_GeomFromText(string, SRID_id)` function is used to create the geometry value from a WKT (Well-Known Text) string representation
  - Geometry objects can be written as `'POINT(1 2)'::geometry`
  - Optionally, use `NSERT INTO public.test (id, geom) VALUES (DEFAULT, 'SRID=4326;LINESTRING(0 0, 10 10)');` for pure string input
- `SELECT * FROM test ORDER BY ST_Distance(ST_GeomFromText('POINT(0 0)', 4326), geometry) ASC LIMIT 1;` Get the linestring which has shortest distance to `POINT(0 0)`
  - Optionally, `SELECT *, ST_Distance(geometry, ST_GeomFromText('POINT(0 0)', 4326)) AS distance FROM test ORDER BY distance LIMIT 1;`
  - `ST_Distance(ST_GeomFromText(geometry_1, geometry_2)` it returns the distance betweeen to geometry objects
    - For distance between coordinates, project them with different SRID, `SELECT ST_Distance(ST_Transform('SRID=4326;POINT(-72.1235 42.3521'::geometry, 26986), ST_Transform('SRID=4326;LINESTRING(-72.1260 42.45, -72.123 42.1546)'::geometry, 26986));`
    - Alternatively, use `ST_DistanceSphere(geometry_1, geometry_2)`
  - `ST_Equals(geometry_1, geometry_2)`: Returns true if the two geometries are equal.
  - `ST_Intersects(geometry_1, geometry_2)`: Returns true if the two geometries intersect.
  - `ST_Overlaps(geometry_1, geometry_2)`: Returns true if the two geometries overlap (i.e., share some but not all points).
  - `ST_Touches(geometry_1, geometry_2)`: Returns true if the two geometries touch (i.e., share a common boundary).
  - `ST_Within(geometry_1, geometry_2)`: Returns true if the first geometry is within the second geometry.
  - `ST_Contains(geometry_1, geometry_2)`: Returns true if the first geometry contains the second geometry.
  - `ST_Crosses(geometry_1, geometry_2)`: Returns true if the two geometries cross (i.e., share a common boundary).
  - `ST_Disjoint(geometry_1, geometry_2)`: Returns true if the two geometries are disjoint (i.e., do not intersect).
  - `ST_SymDifference(geometry_1, geometry_2)`: Returns a geometry representing the symmetric difference (i.e., the areas where the two geometries do not overlap).
  - `ST_Union(geometry_1, geometry_2)`: Returns a geometry representing the union of the two geometries.
  - `ST_Intersection(geometry_1, geometry_2)`: Returns a geometry representing the intersection of the two geometries.
  - `ST_Within(geometry_1, geometry_2, radius)`: Returns true if the distance between two geometries are within the given radius.
  - `ST_IsValid(geometry)`: Returns true if the geometry is valid.
  - `ST_IsSimple(geometry)`: Returns true if the geometry is simple (i.e., has no self-intersections).
  - `ST_IsRing(geometry)`: Returns true if the geometry is a ring (i.e., a closed linestring).
  - `ST_IsClosed(geometry)`: Returns true if the geometry is closed (i.e., a polygon or a ring).
  - `ST_Area(geometry)`: Returns the area of the geometry.
  - `ST_Length(geometry)`: Returns the length of the geometry.
  - `ST_Perimeter(geometry)`: Returns the perimeter of the geometry.
  - `ST_Centroid(geometry)`: Returns the centroid of the geometry.
  - `ST_PointOnSurface(geometry)`: Returns a point on the surface of the geometry.
  - `ST_ConvexHull(geometry)`: Returns the convex hull of the geometry.
    - `SELECT ST_AsText(ST_ConvexHull(ST_GeomFromText('MULTIPOLYGON(((0 0, 1 1, 1 0, 0 0)), ((2 2, 3 3, 3 2, 2 2)))'))) AS convex_hull;`
- `Select ST_AsText(geometry) FROM test` the function `ST_AsText()` takes a geometry object and returns its WKT string representation
- `ST_Dump(multi_geoms)` it separates multi geo objects into a set of geo objects
- `ST_GeometryN(multi_geoms, n)` it returns the nth objects from multi geo objects

#### postgis_topology

### Join

- Table names can use nickname, set after `FROM` clause, e.g. `FROM tablename alias`
- Columns that appear in multiple tables must be table prefixed(ususally use alias for short) to prevent ambiguity
  - `alias.*` means all columns from table `alias`
- MySQL only supports some basic join types like inner and outer

#### Inner Join

- Rows returned only if they exist in both tables
- `INNER` in the query is optional
  ```sql
  SELECT column
  FROM firsttable
  INNER JOIN secondtable
  ON firsttable.column = secondtable.column
  ```
- Select all columns from both tables, Join on purchase order id
  ```sql
  SELECT *
  FROM purchase_orders
  JOIN purchase_order_lines
  ON purchase_orders.purchase_order_id = purchase_order_lines.purchase_order_id
  ```
- Optionally, the old pre ANSI 92 syntax
  ```sql
  SELECT ct.ID, ct.Name, ord.Name, ord.Amount
  FROM customers AS ct, orders AS ord
  WHERE ct.ID=ord.Customer_ID
  ORDER BY ct.ID;
  ```

#### Outer Join

- It can be either `LEFT OUTER JOIN` or `RIGHT OUTER JOIN`
- Keyword `OUTTER` is optional
- The `LEFT OUTTER JOIN` returns all rows from the first table, even if there are no matches in the right table
- The `RIGHT OUTTER JOIN` returns all rows from the second table, even if there are no matches in the right table
  ```sql
  SELECT table1.column1, table2.column2
  FROM table1 LEFT OUTER JOIN table2
  ON table1.column_name = table2.column_name;
  ```
- If no match is found for a particular row, NULL is returned
- Excluding records that both tables have
  ```sql
  SELECT *
  FROM tableA A
  LEFT JOIN tableB B ON A.key = B.key
  WHERE B.key IS NULL
  ```
- Optionally, old syntax for left outer join
  ```sql
  SELECT s.item_id, p.item_id, quantity_sold, quantity_purchased
  FROM sales s, purchases p
  WHERE s.item_id = p.item_id(+)
  ```

#### Natural Join

- The database will decide which columns from both tables are used to join, based on the names and data types
- Table prefixes are not required
  ```sql
  SELECT patient_id, nursing_unit_id, room, bed
  FROM patients
  NATURAL JOIN admissions
  ```

#### Full Outer Join

- All rows returned from both tables
- Missing values returned as NULL
  ```sql
  SELECT s.item_id, p.item_id, quantity_sold, quantity_purchased
  FROM sales s
  FULL OUTER JOIN purchases p ON s.item_id = p.item_id
  ```
- To exclude records that both tables have
  ```sql
  SELECT *
  FROM tableA A
  FULL OUTER JOIN tableB B
  ON A.key = B.key
  WHERE A.key IS NULL OR B.key IS NULL
  ```

#### Cross Join

- Each row from left table is joined with each row from right table
- If `table_a` has `x` rows, `table_b` has `y` rows. the cross join of them has `x` multiply by `y` rows.
  ```sql
  SELECT p.product_id, sold, purchased
  FROM sales_lines s
  CROSS JOIN purchase_lines p
  ```
- optionally, cross join can be expressed as:
  ```sql
  SELECT ct.ID, ct.Name, ord.Name, ord.Amount
  FROM customers ct, orders ord
  ```

#### Self Join

- A table Join on itself using any types of join
  ```sql
  SELECT e1.employee_id, e1.first_name, e1.last_name, e1.department, e1.title, e1.supervisor, e2.employee_id, e2.first_name, e2.last_name
  FROM employees e1
  LEFT JOIN employees e2 - - if not using LEFT, somebody will be missing.
  ON e1.supervisor = e2.employee_id
  ORDER BY e1.department, e1.employee_id
  ```

#### Join Multiple Tables

```sql
SELECT first_name, last_name, medication_description, dosage
FROM patients p
JOIN unit_dose_orders u
ON p.patient_id = u.patient_id
JOIN medications m
ON u.medication_id = m.medication_id
ORDER BY last_name, first_name, medication_description
```

### View

- `VIEW` is a virtual table that is based on the result-set of an SQL statement
- The View result set is not permanently stored in the database, but generated and executed each time it is used
- A `VIEW` can be modified by an `UPDATE`, `INSERT` or `DELETE` provided it doesn’t use any of the following
  - Set operations (UNION, UNION ALL, INTERSECT, MINUS)
  - Group functions (AVG, COUNT, MAX, MIN, SUM)–GROUP BY or HAVING clauses
  - CONNECT BY or START WITH clauses
  - DISTINCT operator–ROWNUM pseudocolumn
- For Oracle use `GRANT CREATE VIEW TO tableA;` to grant permission
- Create a view
  ```sql
  CREATE VIEW current_patients
  AS
  SELECT a.patient_id, first_name, last_name, nursing_unit_id, room
  FROM patients p
  JOIN admissions a
  ON p.patient_id = a.patient_id
  WHERE discharge_date IS NULL
  ```
- Once generated, View can be later query as a normal table
  ```sql
  SELECT *
  FROM current_patients
  ```
- A view always shows up-to-date data.
- When use `SUBSTRING()` function in a view columns names must have alias(new name after AS)
- Update view
  ```sql
  CREATE OR REPLACE VIEW view_name AS
  SELECT column_name(s)
  FROM table_name
  WHERE condition;
  ```
  - `REPLACE` is used to replace the view, if it has already been created,
- Delete View
  ```sql
  Delete view,
  DROP VIEW List;
  ```

### Insert

- Insert a single row to the database
  ```sql
  INSERT INTO table_name
  VALUES (value1, value2, value3);
  ```
  ```sql
  INSERT INTO dental_services
  VALUES(101, 'Tricky Extraction', 'E', NULL, 0);
  ```
- New row will be added at the bottom. Order is important.
- Must include a value for columns that have no default values or don’t allow null.
- `PK` value can be omitted, identity property will be used.
- Alternatively, you can specify the table's column names, then it is also possible to insert data into specific columns
  ```sql
  INSERT INTO table_name (column2, column4)
  VALUES (value2, value4);
  ```
  ```sql
  INSERT INTO dental_services
  (service_id, service_description, service_type, hourly_rate, sales_ytd)
  VALUES(302, 'Temporary Filling', 'F', 100, 0)
  ```
- When omit one column, its value will be set to NULL.
- Multiple rows of value can be inserted in one statement after `VALUE` separated by comma.
  ```sql
  INSERT INTO dental_services
  (service_id, service_description, service_type, hourly_rate, sales_ytd)
  VALUES(302, 'Temporary Filling', 'F', 100, 0),(303,'Temp','T',230.0)
  ```
- One can insert multiple rows
  ```sql
  INSERT INTO tablename[(column1, column2, column3, column4)]
  SELECT statement
  ```
  ```sql
  INSERT INTO dental_service_archives(service_id, service_description, service_type, hourly_rate, sales_ytd)
  SELECT service_id, service_description, service_type, hourly_rate, sales_ytd
  FROM dental_services
  ```
  ```sql
  INSERT INTO dental_service_archives(service_id, service_description, service_type, hourly_rate, sales_ytd)
  SELECT *
  FROM dental*services
  WHERE sales_ytd >= 500
  ```
  ```sql
  INSERT INTO dental_service_archives
  SELECT *
  FROM dental_services
  ```
  - if column names are not specified, all columns must have values
  ```sql
  INSERT INTO dental_service_archives(service_id, service_description)
  SELECT service_id, service_description
  FROM dental_services
  ```
  - omitted column will be null

### Update

- Update a single row
  ```sql
  UPDATE departments
  SET manager_first_name = 'Bob', manager_last_name = 'Loblaw'
  WHERE department_id = 5
  ```
- select multi rows and apply updates using formula
  ```sql
  UPDATE items
  SET item_cost = item_cost * 1.1
  WHERE primary_vendor_id = 5
  ```
- Updating A Single Row With A Subquery
  ```sql
  UPDATE purchase_orders
  SET total_amount = (SELECT SUM(quantity * unit_cost)FROM purchase_order_linesWHERE purchase_order_id = 10)
  WHERE purchase_order_id = 1
  ```
- If the WHERE clause is omitted, all records in the table will be updated

### Delete

- The `DELETE` statement removes the data from the table permanently.
- Delete a single row
  ```sql
  DELETE FROM dental_services
  WHERE service_id = 301
  ```
- `FROM` is optional
- Deletion can fail if the PK has a reference to other table.
- Delete multiple rows.
  ```sql
  DELETE FROM sales
  WHERE amount >= 100
  ```
- If `WHERE` clause is omitted, all records in the table will be deleted
  - `DELETE table_name;`

### Constraints

- During table creation, specify column level constraint(s) after the data type of that column.
- NULL
  - All data types support the concept of NULL
  - NULL is the absence of a value, it is unknown
  - For a numeric column NULL is not 0
  - For a string column NULL is not ''
- Primary Key
  - Define it as a primary key
  - PRIMARY KEY (UserID)
- Not Null
  name varchar(100) NOT NULL
- Unique
- Default
  - Default value will set for the new column, if not default value then all null.
- Check
  - Determines whether the value is valid or not from a logical expression.
- Auto increment
  - the starting value for AUTO_INCREMENT is 1, and it will increment by 1 for each new record.
  - UserID int NOT NULL AUTO_INCREMENT

### Create Table

- A single database can house hundreds of tables
  ```sql
  CREATE TABLE table_name
  (column_name1 data_type(size),
  column_name2 data_type(size),
  column_name3 data_type(size));
  ```
- Create Table with Constraints
  ```sql
  CREATE TABLE Users
  (
  UserID int,
  FirstName varchar(100),
  LastName varchar(100),
  City varchar(100),
  PRIMARY KEY(UserID)
  );
  ```
  ```sql
  CREATE TABLE employees
  (employee_id INT NOT NULL,
  employee_name VARCHAR(50) NOT NULL,
  department_id INT,
  job_id CHAR(3),
  birth_date DATE,
  gender CHAR(1),
  salary DECIMAL(8, 2),
  CONSTRAINT PK_employees PRIMARY KEY(employee_id),
  CONSTRAINT CK_gender CHECK(gender IN ('M', 'F')),
  CONSTRAINT CK_salary CHECK(salary >= 0),
  CONSTRAINT FK_employees_department_id_departments FOREIGN KEY(department_id) REFERENCES departments(department_id))
  ```
- Table Creation Example with IDENTITY and Constraints Specified Inline
  ```sql
  CREATE TABLE employees_with_identity
  (employee_id INT IDENTITY PRIMARY KEY,
  employee_name VARCHAR(50) NOT NULL,
  department_id INT FOREIGN KEY REFERENCES departments(department_id),
  job_id CHAR(3),
  birth_date DATE,
  gender CHAR(1) CHECK(gender IN ('M', 'F')),
  salary DECIMAL(8, 2) CHECK(salary >= 0))
  ```
- Other Examples:
  ```sql
  CREATE TABLE TableName (
  ColumnName1 DataType[(size)][not null] [DEFAULT value],
  ColumnName2 DataType[(size)][not null] [DEFAULT value],
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
  ```

### Create Index

- Create an index
  ```sql
  Create [UNIQUE][clustered] INDEX index_name
  ON table_name
  (column_name1 [ ASC/DESC ].
  ...
  column_nameN [ ASC/DESC ]
  ```
- Ex:
  ```sql
  CREATE INDEX STJ_patients_last_name
  ON patients
  (last_name ASC)
  ```

### Sequences

- A Sequence is a database object used to generate unique numbers
- CURRVAL returns the current value of the sequence
- NEXTVAL returns the next value of the sequence
- Create a sequence, `CREATE SEQUENCE sequence_name [INCREMENT BY value]`
- Access a Sequence, `sequence_name.CURRVAL`, or `sequence_name.NEXTVAL`
  - `INSERT INTO tableName VALUES(sequence_name.NEXTVAL);`

### Alter Table

- The ALTER TABLE command is used to add, delete, or modify columns and their constraints in an existing table
- Add new columns
  ```sql
  ALTER TABLE People
  ADD DateOfBirth;
  ```
- Delete columns
  ```sql
  ALTER TABLE People
  DROP COLUMN DateOfBirth;
  ```
- Delete entire table, `DROP TABLE People;`
- Rename columns
  ```sql
  ALTER TABLE People
  CHANGE FirstName name varchar(100);
  ```
- Rename tables, `RENAME TABLE People TO Users;`

## SQL Script

- the script put multiple SQL statement together one by one in a file.
- the script file has an extension of `.sql`
- each statement requires `;` in the end
- Excel can build inserts statements
- When work with scripts in database management software always select the correct table or database before execution
- Syntax
  - lexical units:
    - Identifiers – begin with a letter and may be up to 30 characters long
    - Reserved words – such as SELECT, BEGIN, END
    - Delimiters – characters with special meaning, such as `+` `-` `'` `>` `(` `:=` `||` `/*` `--` etc.
    - Literals – such as `123`, `'Hello World'`, `FALSE`
    - Comments – single line comments `--` or mutli-line comments `/* */`
  - Scope And Labels
    - Variables and other structures are scoped local to their block
    - Labels are enclosed in `<< label >>`
    - Labels can be added to the top of any blocks to improve readability and to qualify identifiers
    - The name of the block must precede the first line of executable code (BEGIN or DECLARE)
- A group of sql command is called a batch in sql script.
- `BEGIN`, `END`, is used to enclose a block of PL, like `{}`

### Useful Command

- Oracle
  - `SET SERVEROUTPUT ON;` enable output
  - `CLEAR SCREEN;` clears the output window
  - `SET VERIFY OFF;` suppress new and old impact of substitution variable
  - `SET NLS_DATE_FORMAT = 'DD-MON-YYYY` set the date input format
  - `ALTER SESSION` only make changes to the current session
    - The statement stays in effect until you disconnect from the database
    - `ALTER SESSION SET NLS_DATE_FORMAT = 'DD-MON-YYYY`
- MySQL
  - GO statements is used at the end of each batch, no `;` followed. It can be followed by an integer that repeats the batch for certain time. When a batch fails other batches will still be executed.
  - Some `CREATE` and `INSERT` statements require that they are the first statement in a batch.
  - `SET` commands can be used to change session settings.
  - Examples SQL Server:
    ```sql
    -- Suppress INSERT, UPDATE and DELETE completion messages
    SET NOCOUNT ON
    -- Set date format to YYYY-MM-DD
    SET DATEFORMAT ymd;
    -- Make the master database the current database
    USE master
    -- If database co859 exists, drop it
    IF EXISTS (SELECT * FROM sysdatabases WHERE name = 'co859')
    DROP DATABASE co859;
    GO
    -- Print statement in the script print string in console, when it is executed. For Microsoft SQL manegement output setting need to be changed to text.
    PRINT 'Verification'
    -- Create the co859 database
    CREATE DATABASE co859;
    GO
    -- Make the co859 database the current database
    USE co859;
    ```
  - SET DATEFORMAT format, format can be:
    - dmy (Preferred in much of the world)
    - mdy (Preferred in USA)
    - ymd (Unambiguous, best choice, SQL Server default)
    - ydm (Should be avoided)
    - myd (Should be avoided)
    - dym (Should be avoided)
  - CREATE User statement creates a new entry in the user table that has no privileges.
  - GRANT is then used to control the access and privileges the user has
    - `GRANT Create ON <Database> TO <Source>`
  - Sources can be
    - `smith@localhost` – this account will be granted access only when accessing the data locally, not remotely
    - `RSingh@'192.168.1.%'` – this account will be granted access only when accessing the data from a host with an IP address that begins with `192.168.1`
    - `DNguyen` – this account will be granted access from any host, local or not (translates to DNguyen@’%’)
  - `create database databaseName` create a new database.
  - `grant select on databaseName.* to userName@localhost identified by 'newPassword'` create new database user with local connection and only be allowed to select records.
  - `use databaseName` set the database as default database.
  - `describe tableName;` view details about certain table.
  - `exit;` exit the mysql interface.

### Procedural Language

- Many of the procedure languages supports variables, conditions, loops and exceptions
- It adds logic to the SQL scripts
- Each database vendor extends SQL with procedural code:
  - Microsoft uses T-SQL
  - Oracle uses Procedural Language SQL (PL/SQL)
    - Based on Ada
  - IBM uses SQL Procedural Language (SQL PL)
  - MySQL uses SQL/Persistent Stored Module (SQL/PSM)
- Data Definition Language (CREATE, DROP, ALTER, etc.) is not valid in PL/SQL
- DML (INSERT, UPDATE, DELETE) and SELECT are valid in PL/SQL

### Oracle Scripts

#### Built-in Functions

- TO_CHAR
  - TO_CHAR converts its arguments into a VARCHAR2 with optional formatting
  - TO_CHAR(value[, format_mask])
    - `TO_CHAR(AVG(cost), '$9,999.99')`
    - `TO_CHAR(SYSDATE, 'DD-MONTH-YYYY`
    - `TO_CHAR(SYSDATE, 'HH:MI:SS')`
    - `TO_CHAR(SYSDATE, 'FMDD-MONTH-YYYY')`
      - `FM` - Fill mode controls blank padding and leading zero suppression
    - `TO_CHAR(12345.678, '099,999)`
    - `TRIM(TO_CHAR(v_total, '$999G999G999D99'))`
  - TO_CHAR(character)
  - TO_CHAR(datetime)
  - TO_CHAR(number)
- TO_DATE(SYSDATE), convert `SYSDATE` to `DATE`

#### Procedural Code Blocks

- The basic unit of organization in `PL` is the block
- `PL` blocks can be named or anonymous
- Named blocks can be stored in the database
- Blocks can be nested
- END block types need to have `;`
- Structure
  ```sql
  DECLARE
    -- Declaration statements
    -- Declear Types
    v_first_name VARCHAR2(35);
    -- Use column's data type to declear (anchored variable declaration)
    v_last_name students.last_name%TYPE;
    --  Declear constant types and assign value
    id CONSTANT NUMBER := 7;
  BEGIN
    -- Mandatory, Executable statements
    -- Use || between variable names and strings
    SELECT first_name, last_name
    INTO v_first_name, v_last_name
    FROM student
    WHERE student_id = id;
    -- OUTPUT
    DBMS_OUTPUT.PUT_LINE ('Student name: '||first_name ||' '|| last_name);
  EXCEPTION
    -- Exception-handling statements
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE ('No student is found');
  END;
  ```

#### Substitution Variables

- Substitution variables get processed at run time
- Substitution Variables, prompt for input in a pop-up after execution, `i_student_id NUMBER := &input_student_id;`
- If a substitution variable appears more than once and `&` is used, substitution is prompted for each time
  - Use `&&` to prompt only once
- When prompting to fill a text variable, enclose substitution variable in quotes, `name VARCHAR2(5) := '&input_name';`

#### Conditional Structure

- IF
  ```sql
  DECLARE
    v_num1 NUMBER := &first_number;
    v_num2 NUMBER := &second_number;
    v_temp NUMBER;
  BEGIN
  -- if v_num1 is greater than v_num2 rearrange their values
    IF v_num1 > v_num2 THEN
      v_temp := v_num1;
      v_num1 := v_num2;
      v_num2 := v_temp;
    END IF;
    -- display the values of v_num1 and v_num2
    DBMS_OUTPUT.PUT_LINE ('v_num1 = '||v_num1);
    DBMS_OUTPUT.PUT_LINE ('v_num2 = '||v_num2);
  END;
  ```
- IF/ELSE statements
  ```sql
  DECLARE
    v_num NUMBER := &sv_user_num;
  BEGIN
    -- test if the number provided by the user is even
    IF MOD(v_num,2) = 0  THEN
      DBMS_OUTPUT.PUT_LINE (v_num||' is even number');
    ELSE
      DBMS_OUTPUT.PUT_LINE (v_num||' is odd number');
    END IF;
    DBMS_OUTPUT.PUT_LINE ('Done');
  END;
  ```
- ELSIF statements
  ```sql
  DECLARE
    v_num NUMBER := &sv_num;
  BEGIN
    IF v_num < 0 THEN
      DBMS_OUTPUT.PUT_LINE (v_num||' is a negative number');
    ELSIF v_num = 0 THEN
      DBMS_OUTPUT.PUT_LINE (v_num||' is equal to zero');
    ELSE
      DBMS_OUTPUT.PUT_LINE (v_num||' is a positive number');
    END IF;
  END;
  ```
- Nested If statements
  ```sql
  DECLARE
    v_num1 NUMBER := &sv_num1;
    v_num2 NUMBER := &sv_num2;
    v_total NUMBER;
  BEGIN
    IF v_num1 > v_num2 THEN
      DBMS_OUTPUT.PUT_LINE ('IF part of the outer IF');
      v_total := v_num1 - v_num2;
    ELSE
      DBMS_OUTPUT.PUT_LINE ('ELSE part of the outer IF');
      v_total := v_num1 + v_num2;
      IF v_total < 0 THEN
        DBMS_OUTPUT.PUT_LINE ('Inner IF');
        v_total := v_total * (-1);
      END IF;
    END IF;
    DBMS_OUTPUT.PUT_LINE ('v_total = '||v_total);
  END;
  ```
- Conditions with Logical Operators
  ```sql
  DECLARE
    v_letter CHAR(1) := '&sv_letter';
  BEGIN
    IF (v_letter >= 'A' AND v_letter <= 'Z')
    OR (v_letter >= 'a' AND v_letter <= 'z')
    THEN
      DBMS_OUTPUT.PUT_LINE ('This is a letter');
    ELSE
      DBMS_OUTPUT.PUT_LINE ('This is not a letter');
      IF v_letter BETWEEN '0' AND '9' THEN
        DBMS_OUTPUT.PUT_LINE ('This is a number');
      ELSE
        DBMS_OUTPUT.PUT_LINE ('This is not a number');
      END IF;
    END IF;
  END;
  ```
- CASE statements
  - CASE statements with selector after `CASE`
    ```sql
    DECLARE
      v_num NUMBER := &sv_user_num;
      v_num_flag NUMBER;
    BEGIN
      v_num_flag := MOD(v_num,2);
      -- test if the number provided by the user is even
      CASE v_num_flag
        WHEN 0 THEN
          DBMS_OUTPUT.PUT_LINE (v_num||' is even number');
        ELSE
          DBMS_OUTPUT.PUT_LINE (v_num||' is odd number');
      END CASE;
      DBMS_OUTPUT.PUT_LINE ('Done');
    END;
    ```
  - CASE statements without selector after `CASE`
    ```sql
    DECLARE
      v_student_id   NUMBER := 102;
      v_section_id   NUMBER := 89;
      v_final_grade  NUMBER;
      v_letter_grade CHAR(1);
    BEGIN
      SELECT final_grade
      INTO v_final_grade
      FROM enrollment
      WHERE student_id = v_student_id
      AND section_id = v_section_id;
      CASE
        WHEN v_final_grade >= 90 THEN v_letter_grade := 'A';
        WHEN v_final_grade >= 80 THEN v_letter_grade := 'B';
        WHEN v_final_grade >= 70 THEN v_letter_grade := 'C';
        WHEN v_final_grade >= 60 THEN v_letter_grade := 'D';
        ELSE v_letter_grade := 'F';
      END CASE;
      DBMS_OUTPUT.PUT_LINE ('Letter grade is: '||v_letter_grade);
    END;
    ```
  - Case Expression
    ```sql
    v_result :=
      CASE v_num_flag
        WHEN 0 THEN v_num||' is even number'
        ELSE v_num||' is odd number'
      END;
    ```
  - CASE Expression in a SQL Statement
    ```sql
    SELECT course_no, description,
      CASE
        WHEN prerequisite IS NULL THEN
          'No prerequisite course required'
        ELSE TO_CHAR(prerequisite)
      -- Optional label
      END prerequisite
    INTO v_course_no, v_description, v_prereq
    FROM course
    WHERE course_no = 20;
    ```
  - Case statement can be nested
- NULLIF
  - NULLIF compares two expressions, if they are equal, it returns NULL
  - Otherwise it returns the value of the first expression
  ```sql
  DECLARE
    v_num NUMBER := &sv_user_num;
    v_remainder NUMBER;
  BEGIN
    -- calculate the remainder and if it is zero return NULL
    v_remainder := NULLIF(MOD(v_num,2),0);
    DBMS_OUTPUT.PUT_LINE ('v_remainder: '||v_remainder);
  END;
  ```
- Simple Loop
  - Example
  ```sql
  DECLARE
    v_counter NUMBER := 0;
  BEGIN
    LOOP
      DBMS_OUTPUT.PUT_LINE ('v_counter = '||v_counter);
      EXIT;
    END LOOP;
  END;
  ```
  - Simple LOOP with EXIT Condition
  ```sql
  DECLARE
    v_counter BINARY_INTEGER := 0;
  BEGIN
    LOOP
      -- increment loop counter by one
      v_counter := v_counter + 1;
      DBMS_OUTPUT.PUT_LINE ('v_counter = '||v_counter);
      -- if EXIT condition yields TRUE exit the loop
      IF v_counter = 5 THEN
        EXIT;
      END IF;
    END LOOP;
  END;
  ```
  - Simple LOOP with EXIT WHEN Condition
  ```sql
  DECLARE
    v_course course.course_no%TYPE := 430;
    v_instructor_id instructor.instructor_id%TYPE := 102;
    v_sec_num section.section_no%TYPE := 0;
  BEGIN
    LOOP
      -- increment section number by one
      v_sec_num := v_sec_num + 1;
      INSERT INTO section
        (section_id, course_no, section_no, instructor_id, created_date, created_by, modified_date, modified_by)
      VALUES
        (section_id_seq.NEXTVAL, v_course, v_sec_num, v_instructor_id, SYSDATE, USER, SYSDATE, USER);
      -- if number of sections added is four exit the loop
      EXIT WHEN v_sec_num = 4;
    END LOOP;
    COMMIT;
  END;
  ```
- WHILE Loop
  ```sql
  DECLARE
    v_counter NUMBER := 1;
  BEGIN
    WHILE v_counter < 5 LOOP
      DBMS_OUTPUT.PUT_LINE ('v_counter = '||v_counter);
      v_counter := v_counter + 1;
    END LOOP;
  END;
  ```
- FOR LOOP
  ```sql
  BEGIN
    FOR v_counter IN 1..5 LOOP
      -- By Default, Loop will only increment (or decrement) by 1
      DBMS_OUTPUT.PUT_LINE ('v_counter = '|| v_counter);
    END LOOP;
  END;
  ```
- Numeric FOR LOOP IN REVERSE
  ```sql
  BEGIN
    FOR v_counter IN REVERSE 1..5 LOOP
      DBMS_OUTPUT.PUT_LINE ('v_counter = '||v_counter);
    END LOOP;
  END;
  ```
- CONTINUE - Used to advance to the next iteration of a loop
  ```sql
  DECLARE
    v_counter NUMBER := 0;
  BEGIN
    LOOP
      DBMS_OUTPUT.PUT_LINE ('v_counter = '||v_counter);
      CONTINUE;
      v_counter := v_counter + 1;
      EXIT WHEN v_counter = 5;
    END LOOP;
  END;
  ```

#### Exception Handling

- Catch Errors based on Built-in Exception types
  ```sql
  EXCEPTION
    WHEN ZERO_DIVIDE THEN
      DBMS_OUTPUT.PUT_LINE ('A number cannot be divided by zero.');
    WHEN VALUE_ERROR THEN
      DBMS_OUTPUT.PUT_LINE ('An error has occurred');
    WHEN NO_DATA_FOUND THEN
      DBMS_OUTPUT.PUT_LINE ('There is no such student');
    WHEN TOO_MANY_ROWS THEN
      DBMS_OUTPUT.PUT_LINE ('TOO_MANY_ROWS');
    WHEN PROGRAM_ERROR OR DUP_VALUE_ON_INDEX THEN
      DBMS_OUTPUT.PUT_LINE ('PROGRAM_ERROR or DUP_VALUE_ON_INDEX');
    -- Handle any exceptions
    WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE ('An error has occurred');
  ```
- EXCEPTION block works below inner blocks as well
- only 1 exception can be raised per block, until handled
- User-Defined Exceptions
  ```sql
  DECLARE
    v_student_id STUDENT.STUDENT_ID%TYPE := &sv_student_id;
    v_total_courses NUMBER;
    e_invalid_id EXCEPTION;
  BEGIN
    IF v_student_id < 0 THEN
      RAISE e_invalid_id;
    END IF;
    DBMS_OUTPUT.PUT_LINE ('No exception has been raised');
  EXCEPTION
    WHEN e_invalid_id THEN
      DBMS_OUTPUT.PUT_LINE ('An id cannot be negative');
  END;
  ```
- Reraise Exceptions - raise twice, new error replace old in the output
  ```sql
  -- outer block
  DECLARE e_exception EXCEPTION;
  BEGIN
    -- inner block
    BEGIN
      RAISE e_exception;
    EXCEPTION
      WHEN e_exception THEN
        RAISE;
    END;
  EXCEPTION
    WHEN e_exception THEN
      DBMS_OUTPUT.PUT_LINE ('An error has occurred');
  END;
  ```
- RAISE_APPLICATION_ERROR gives an error with more of an Oracle look and feel
  , `RAISE_APPLICATION_ERROR(error_number, error_message[, keep_errors])`
  - `error_number`: -20,999 to -20,000
  - `error_message`: up to 2,048 characters
  - `keep_errors`: boolean
    - If TRUE, new error is added to error stack
    - If FALSE (default), new error replaces error stack
  - Example
  ```sql
  DECLARE
    v_student_id STUDENT.STUDENT_ID%TYPE := &sv_student_id;
    v_total_courses NUMBER;
  BEGIN
    IF v_student_id < 0 THEN
      RAISE_APPLICATION_ERROR (-20000, 'An id cannot be negative');
    END IF;
  END;
  ```
  ```sql
  EXCEPTION
    WHEN NO_DATA_FOUND THEN
      RAISE_APPLICATION_ERROR (-20001, 'This ID is invalid');
  ```
- EXCEPTION_INIT Pragma
  - The exception handler only works with named errors
  - Not all Oracle errors have names
  - The EXCEPTION_INIT Pragma (compiler directive) adds an Oracle error number to the user defined error
  ```sql
  DECLARE
    v_zip ZIPCODE.ZIP%TYPE := '&sv_zip';
    e_child_exists EXCEPTION;
    PRAGMA EXCEPTION_INIT(e_child_exists, -2292);
  ```
- SQLCODE and SQLERRM
  - SQLCODE returns Oracle error number
  - SQLERRM returns error message, maximum length 512 bytes
  - Used with WHEN OTHERS exception handler
  - Example
    ```sql
    EXCEPTION
      WHEN OTHERS THEN
        v_err_code := SQLCODE;
        v_err_msg  := SUBSTR(SQLERRM, 1, 200);
        DBMS_OUTPUT.PUT_LINE ('Error code: '||v_err_code);
        DBMS_OUTPUT.PUT_LINE ('Error message: '||v_err_msg);
    ```

#### Cursor

- When Oracle processes a SQL statement, it creates an area of memory known as the context area
- Implicit Cursor - SQL engin utlize cursors internally to complete tasks
- Explicit Cursor - It returns an array of records with defines row element types
- To use a cursor, one needs to:
  - Declare the cursor (SELECT statement)
  - Open the cursor
  - Fetch the cursor (one row at a time, usually in a loop)
  - Perform desired processing
  - Close the cursor
  ```sql
  DECLARE
    CURSOR c_zip IS
      SELECT *
        FROM zipcode;
    vr_zip c_zip%ROWTYPE;
  BEGIN
    OPEN c_zip;
    LOOP
      FETCH c_zip INTO vr_zip;
      EXIT WHEN c_zip%NOTFOUND;
      DBMS_OUTPUT.PUT_LINE(vr_zip.zip||' '||vr_zip.city||' '||vr_zip.state);
    END LOOP;
  END;
  ```
- Cursor Attributes
  - `%NOTFOUND` – Boolean that returns TRUE if previous FETCH did not return a row
  - `%FOUND` – Boolean that returns TRUE if previous FETCH returned a row
  - `%ROWCOUNT` – Number of records fetched from a cursor at that point in time
  - `%ISOPEN` – Boolean that returns TRUE if the cursor is open
  ```sql
  EXCEPTION
    WHEN OTHERS THEN
      IF c_student%ISOPEN THEN
        CLOSE c_student;
      END IF;
  ```
  - Attributes are appended to name of cursor, ex. `c_zip%ROWCOUNT`
  - For implicit cursor, use `SQL%ROWCOUNT`
- Cursor FOR Loops
  ```sql
  CREATE TABLE table_log (description VARCHAR2(250));
  DECLARE
    CURSOR c_student IS
      SELECT student_id, last_name, first_name
        FROM student
        WHERE rownum <= 5;
  BEGIN
    FOR r_student IN c_student LOOP
      INSERT INTO table_log
        VALUES(r_student.last_name);
    END LOOP;
  END;
  ```
  - `ROWNUM` in cursor definition returns a number indicating the order in which a row was selected from a table
  - Cursor FOR loops handle opening, fetching and closing cursors implicitly
  - Cursor FOR Loops can be nested
  - Cursor can have variables in its definition, the value of the variable will be accessed before acessing the cursor
- Cursors with Parameters
  - Like passing a parameter to a method
  - Different values can be provided at run time
  ```sql
  DECLARE
    CURSOR c_zip(p_state IN zipcode.state%TYPE) IS
      SELECT zip, city, state
        FROM zipcode
        WHERE state = p_state;
  BEGIN
    FOR r_zip IN c_zip('NJ') LOOP
      DBMS_OUTPUT.PUT_LINE(r_zip.city||' '||r_zip.zip);
    END LOOP;
  END;
  ```
  - Cursor can have multiple parameters and separated by comma, `CURSOR c_grade(i_section_id IN section.section_id%TYPE, i_student_id IN student.student_id%TYPE) IS`
- Cursors for update
  - When cursors are used to update, `FOR UPDATE` keyword is required in declaration
  ```sql
  DECLARE
    CURSOR c_course IS
      SELECT course_no, cost
        FROM course FOR UPDATE;
  BEGIN
    FOR r_course IN c_course LOOP
      IF r_course.cost < 2500 THEN
        UPDATE course
          SET cost = r_course.cost + 10
          WHERE course_no = r_course.course_no;
      END IF;
    END LOOP;
  END;
  ```
- `FOR UPDATE` only locks a certain row during operation
- `WHERE CURRENT OF` lock and return the current row from the cursor during update
  ```sql
  DECLARE
    CURSOR c_stud_zip IS
      SELECT s.student_id, z.city
        FROM student s
        JOIN zipcode z ON s.zip = z.zip
        WHERE z.city = 'Brooklyn'
        FOR UPDATE OF phone;
  BEGIN
    FOR r_stud_zip IN c_stud_zip LOOP
    DBMS_OUTPUT.PUT_LINE(r_stud_zip.student_id);
      UPDATE student
        SET phone = '718'||SUBSTR(phone,4)
        WHERE CURRENT OF c_stud_zip;
    END LOOP;
  END;
  ```

#### Transcation

- some units of work (transactions) will change multiple tables
- Database not considered in a consistent state unless all or none of the changes are processed together
- Changes made by one database user are not visible to other users until committed
- `COMMIT` makes events within a transaction permanent
- `ROLLBACK` erases events within a transaction
- `SAVEPOINT` marks a place in a transaction to where a partial rollback may be made
  ```sql
  BEGIN
    INSERT INTO student
    (student_id, last_name, zip, registration_date, created_by, created_date, modified_by, modified_date)
    VALUES(student_id_seq.NEXTVAL, 'Tashi', 10015, '1-JAN-2019', 'STUDENTA', '1-JAN-2019', 'STUDENTA', '1-JAN-2019');
    SAVEPOINT A;
    INSERT INTO student
    (student_id, last_name, zip, registration_date, created_by, created_date, modified_by, modified_date)
    VALUES(student_id_seq.NEXTVAL, 'Sonam', 10015, '1-JAN-2019', 'STUDENTB', '1-JAN-2019', 'STUDENTB', '1-JAN-2019');
    SAVEPOINT B;
    INSERT INTO student
    (student_id, last_name, zip, registration_date, created_by, created_date, modified_by, modified_date)
    VALUES(student_id_seq.NEXTVAL, 'Norbu', 10015, '1-JAN-2019', 'STUDENTB', '1-JAN-2019', 'STUDENTB', '1-JAN-2019');
    SAVEPOINT C;
    ROLLBACK TO B;
  END;
  ```

#### Procedure

- A procedure is a named PL/SQL block
- Procedures have names and may be called from a SQL prompt, other procedures, triggers or scheduling utilities
- Procedures may accept and return parameters
- If procedure doesn't compile, inspect the Compiler Log or use the show error command `SHOW ERROR;`
- Example
  ```sql
  CREATE OR REPLACE PROCEDURE Discount
  AS
    CURSOR c_group_discount
    IS
      SELECT distinct s.course_no, c.description
        FROM section s, enrollment e, course c
        WHERE s.section_id = e.section_id
        AND c.course_no = s.course_no
        GROUP BY s.course_no, c.description,
                e.section_id, s.section_id
        HAVING COUNT(*) >= 8;
  BEGIN
    FOR r_group_discount IN c_group_discount LOOP
      UPDATE course
        SET cost = cost * .95
        WHERE course_no = r_group_discount.course_no;
      DBMS_OUTPUT.PUT_LINE
        ('A 5% discount has been given to '||
        r_group_discount.course_no||' '||
        r_group_discount.description);
    END LOOP;
  END;
  ```
- Execute Procedure
  ```sql
  BEGIN
    Discount;
  END
  ```
  - Interactively in SQL Developer, use `EXECUTE Discount;`, and `EXEC Discount;`
- Query existing procedure
  ```sql
  SELECT object_name, object_type, status
    FROM user_objects
    WHERE object_name = 'DISCOUNT';
  ```
- Procedure parameter modes:
  - `IN` - Passes a value into the programConstants, literals, expressions, cannot be changed with the program. Read-only value
  - `OUT` - Passes a value back from the program, cannot assign default values, must be a variable, a value is assigned only if the program is successful. Write-only value
  - `IN OUT` - Passes value in and also sends values back. Must be a variable
- Procedure parameter example
  ```sql
  CREATE OR REPLACE PROCEDURE find_sname
    (i_student_id IN NUMBER,
    o_first_name OUT VARCHAR2,
    o_last_name OUT VARCHAR2)
  AS
  BEGIN
    SELECT first_name, last_name
      INTO o_first_name, o_last_name
      FROM student
      WHERE student_id = i_student_id;
  EXCEPTION
    WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('Error in finding student_id: '||i_student_id);
  END find_sname;
  ```
- Calling with Positional Parameters
  ```sql
  DECLARE
    v_first student.first_name%TYPE;
    v_last student.last_name%TYPE;
  BEGIN
    find_sname (105, v_first, v_last);
    DBMS_OUTPUT.PUT_LINE(v_first ||' '|| v_last);
  END;
  ```
- Calling with Named Parameters
  ```sql
  DECLARE
    v_id student.student_id%TYPE := 110;
    v_first student.first_name%TYPE;
    v_last student.last_name%TYPE;
  BEGIN
    find_sname (o_first_name => v_first,
                o_last_name => v_last,
                i_student_id => v_id);
    DBMS_OUTPUT.PUT_LINE(v_first ||' '|| v_last);
  END;
  ```
- For debugging, login as `SYS` and issue following commands, `GRANT DEBUG CONNECT SESSION TO student;`, `GRANT DEBUG ANY PROCEDURE TO student;` and perform the following steps:
  1. Expand Procedures in explorer
  2. Right click desired procedure and select Edit…
  3. Compile for Debug by clicking dropdown of gears icon
  4. Add breakpoints as desired by clicking in gutter
  5. Click Debug icon to run
  6. Edit created anonymous block for input parameters as necessary
  7. Step through code

#### EXECUTE IMMEDIATE

- It is a statement that allows the execution of a sql statement or block stroed in a string
- It allows for creating SQL statements on the fly and executing them
- It allows things that wouldn’t normally be permissible in a PL/SQL block, such as DDL
- Syntax
  ```sql
    EXECUTE IMMEDIATE dynamic_SQL_string
    [INTO defined_variable1, defined_variable2, ...]
    [USING [IN | OUT | IN OUT] bind_argument1, bind_argument2,
    ...][{RETURNING | RETURN} field1, field2, ... INTO bind_argument1,
    bind_argument2, ...]
  ```
  - dynamic_SQL_string may be a SQL statement or a PL/SQL block
  - The INTO clause contains the list of predefined variables that hold values returned by the SELECT statement, when it returns a single row
  - The USING clause contains a list of bind arguments passed to the SQL statement or PL/SQL block
  - IN, OUT and IN OUT are modes for bind arguments, IN is default
  - RETURNING INTO or RETURN clause contains a list of bind arguments that store values returned by the dynamic SQL or PL/SQL block
  - RETURNING INTO has similar argument modes to USING, OUT is default
- Example
  ```sql
  DECLARE
    sql_stmt VARCHAR2(100);
    plsql_block VARCHAR2(300);
    v_zip VARCHAR2(5) := '11106';
    v_total_students NUMBER;
    v_new_zip VARCHAR2(5);
    v_student_id NUMBER := 151;
  BEGIN
    -- Create table MY_STUDENT
    sql_stmt := 'CREATE TABLE my_student '||
                'AS SELECT * FROM student WHERE zip = '||v_zip;
    EXECUTE IMMEDIATE sql_stmt;
    -- Select total number of records from MY_STUDENT table
    -- and display results on the screen
    EXECUTE IMMEDIATE 'SELECT COUNT(*) FROM my_student' INTO v_total_students;
    DBMS_OUTPUT.PUT_LINE ('Students added: '||v_total_students);
    -- Select current date and display it on the screen
    plsql_block := 'DECLARE ' ||
                  '  v_date DATE; ' ||
                  'BEGIN ' ||
                  '  SELECT SYSDATE INTO v_date FROM DUAL; '||
                  '  DBMS_OUTPUT.PUT_LINE (TO_CHAR(v_date, ''DD-MON-YYYY''));'||
                  'END;';
    EXECUTE IMMEDIATE plsql_block;
    -- Update record in MY_STUDENT table
    sql_stmt := 'UPDATE my_student SET zip = 11105 WHERE student_id = :1 '||
                'RETURNING zip INTO :2';
    EXECUTE IMMEDIATE sql_stmt USING v_student_id RETURNING INTO v_new_zip;
    DBMS_OUTPUT.PUT_LINE ('New zip code: '||v_new_zip);
  END;
  ```
- DDL statements cannot accept bind arguments, Names of schema objects cannot be passed as bind arguments, Both of these problems are solved by concatenation
  - Dynamic SQL statements should not be terminated with a semicolon (`;`)
  - Dynamic PL/SQL blocks should not be terminated with a slash (`/`)
- Passing NULL
  ```sql
  DECLARE
    sql_stmt VARCHAR2(100);
    v_null VARCHAR2(1);
  BEGIN
    sql_stmt := 'UPDATE course'||
                ' SET prerequisite = :some_value';
    EXECUTE IMMEDIATE sql_stmt
    USING v_null;
  END;
  ```

#### OPEN-FOR, FETCH and CLOSE

- They are statements for multi-row queries
- Very similar to cursors
  ```sql
  DECLARE
    -- REF CURSOR declares a cursor type
    TYPE student_cur_type IS REF CURSOR;
    -- student_cur is an instance of the new type
    student_cur student_cur_type;
    v_zip VARCHAR2(5) := '&sv_zip';
    v_first_name VARCHAR2(25);
    v_last_name VARCHAR2(25);
  BEGIN
    OPEN student_cur FOR
      'SELECT first_name, last_name FROM student '|| 'WHERE zip = :1'
    USING v_zip;
    LOOP
      FETCH student_cur INTO v_first_name, v_last_name;
      EXIT WHEN student_cur%NOTFOUND;
      DBMS_OUTPUT.PUT_LINE ('First Name: '||v_first_name);
      DBMS_OUTPUT.PUT_LINE ('Last Name: '||v_last_name);
    END LOOP;
    CLOSE student_cur;
  EXCEPTION
    WHEN OTHERS THEN
      IF student_cur%ISOPEN THEN
        CLOSE student_cur;
      END IF;
      DBMS_OUTPUT.PUT_LINE ('ERROR: '|| SUBSTR(SQLERRM, 1, 200));
  END;
  ```

#### Trigger

- A database trigger is a named PL/SQL block
- Triggers are "special" procedures
- Triggers may not use transaction control statements: COMMIT, SAVEPOINT or ROLLBACK with the exception of an autonomous transaction
- Triggers execute automatically (or are fired) in response to an event
- During the execution of the trigger, there are pseudorecords `:NEW` and `:OLD`, they can be used to access the new and old values, it has the type `triggering_table%TYPE`
  - Delete event has a old record
  - Insert event has a new record
  - Update event has both new and old record
- Debug trigger in SQL Develop
  1. In the Connections navigator, expand the student connection, then expand the Triggers folder, select the student_bi trigger
  2. Click the gears icon to compile the trigger
  3. The same error messages appear and the line of code in error is highlighted
  4. Fix the error and compile
- BEFORE Trigger
  ```sql
  CREATE OR REPLACE TRIGGER student_bi
  BEFORE INSERT ON student
  FOR EACH ROW
  DECLARE
    v_student_id STUDENT.STUDENT_ID%TYPE;
  BEGIN
    SELECT STUDENT_ID_SEQ.NEXTVAL
      INTO v_student_id
      FROM dual;
    :NEW.student_id    := v_student_id;
    :NEW.created_by    := USER;
    :NEW.created_date  := SYSDATE;
    :NEW.modified_by   := USER;
    :NEW.modified_date := SYSDATE;
  END;
  ```
- After Trigger
  ```sql
  CREATE OR REPLACE TRIGGER employees_au
  AFTER UPDATE ON employees
  FOR EACH ROW
  DECLARE
    v_diff NUMBER;
  BEGIN
    v_diff := :NEW.salary - :OLD.salary;
    IF v_diff > 250 THEN
      INSERT INTO salary_log (employee_id, salary_date, description)
        VALUES(:NEW.employee_id, SYSDATE, 'Raise of more than $250');
    END IF;
  END;
  ```
- A row trigger will fire the same number of times as rows that have been affected. Whereas a statement trigger will only fire once, regardless of how many rows have been affected
  - Row trigger is enabled by adding the `FOR EACH ROW` keyword
- `INSERTING`, `UPDATING` and `DELETING` are boolean functions that evaluate to `TRUE` depending on which DML statement invoked the trigger
  ```sql
  CREATE OR REPLACE TRIGGER instructor_aud
  AFTER UPDATE OR DELETE ON INSTRUCTOR
  DECLARE
    v_type VARCHAR2(10);
  BEGIN
    IF UPDATING THEN
      v_type := 'UPDATE';
    ELSIF DELETING THEN
      v_type := 'DELETE';
    END IF;
    UPDATE statistics SET transaction_user = USER, transaction_date = SYSDATE
      WHERE table_name = 'INSTRUCTOR' AND transaction_name = v_type;
    IF SQL%NOTFOUND THEN
      INSERT INTO statistics
      VALUES ('INSTRUCTOR', v_type, USER, SYSDATE);
    END IF;
  END;
  ```
- COMMIT
  ```sql
  CREATE OR REPLACE TRIGGER instructor_aud
  AFTER UPDATE OR DELETE ON INSTRUCTOR
  DECLARE
    v_type VARCHAR2(10);
    PRAGMA AUTONOMOUS_TRANSACTION;
  BEGIN
    IF UPDATING THEN
      v_type := 'UPDATE';
    ELSIF DELETING THEN
      v_type := 'DELETE';
    END IF;
    UPDATE statistics SET transaction_user = USER, transaction_date = SYSDATE
      WHERE table_name = 'INSTRUCTOR' AND transaction_name = v_type;
    IF SQL%NOTFOUND THEN
      INSERT INTO statistics VALUES ('INSTRUCTOR', v_type, USER, SYSDATE);
    END IF;
    COMMIT;
  END;
  ```
  - `ROLLBACK;` can be executed after the trigger is activated
- Raise error can cancel the trigger
  ```sql
  CREATE OR REPLACE TRIGGER instructor_biud
  BEFORE INSERT OR UPDATE OR DELETE ON INSTRUCTOR
  DECLARE
    v_day VARCHAR2(10);
  BEGIN
    v_day := RTRIM(TO_CHAR(SYSDATE, 'DAY'));
    IF v_day LIKE ('T%') THEN
      RAISE_APPLICATION_ERROR(-20000, 'A table cannot be modified during off hours');
    END IF;
  END;
  ```
- An `INSTEAD OF` trigger can operate against a view
  ```sql
  CREATE OR REPLACE TRIGGER instructor_summary_del
  INSTEAD OF DELETE ON instructor_summary_view
  FOR EACH ROW
  BEGIN
    DELETE FROM instructor WHERE instructor_id = :OLD.INSTRUCTOR_ID;
  END;
  ```
- `DROP TRIGGER instructor_biud;` delete a trigger

#### Function

- A function is another type of procedure
- Parameters are optional
- A value must be returned
- A function can be used in a SQL statement
  ```sql
  CREATE OR REPLACE FUNCTION show_description
    (i_course_no course.course_no%TYPE)
  RETURN varchar2
  AS
    v_description varchar2(50);
  BEGIN
    SELECT description
      INTO v_description
      FROM course
    WHERE course_no = i_course_no;
    RETURN v_description;
  EXCEPTION
    WHEN NO_DATA_FOUND THEN
      RETURN('The Course is not in the database');
    WHEN OTHERS THEN
      RETURN('Error in running show_description');
  END;
  ```
- Using Function
  ```sql
  DECLARE
    v_description VARCHAR2(50);
  BEGIN
    v_description := show_description(&course_number);
    dbms_output.put_line(v_description);
  END;
  ```
- Using Function in SQL Statement, `SELECT course_no, show_description(course_no) FROM course;`

#### Packages

- A package is a container that may hold procedures, functions, global variables and cursors
- When a package is first called, it is loaded into memory, making it very fast on subsequent calls
- PL/SQL is not object oriented, but using packages offer some of the concepts such as overloading
- Package specification:
  - Information about the package’s contents, but not the code
  - Global/public variables
  - Anything found in a PL/SQL DECLARE section may be placed in the specification
  - Objects in the specification are public
  ```sql
  CREATE OR REPLACE PACKAGE manage_students
  AS
    PROCEDURE find_sname
      (i_student_id IN student.student_id%TYPE,
      o_first_name OUT student.first_name%TYPE,
      o_last_name OUT student.last_name%TYPE);
    FUNCTION id_is_good
      (i_student_id IN student.student_id%TYPE)
      RETURN BOOLEAN;
  END manage_students;
  ```
  - modify packages by redefining the specification
- Package Body
  - Executable code
  - Any code for objects in body that are not in the specification are private to the package
  - Must match specification for cursor and modules
  ```sql
  CREATE OR REPLACE PACKAGE BODY manage_students
  AS
    PROCEDURE find_sname
      (i_student_id IN student.student_id%TYPE,
      o_first_name OUT student.first_name%TYPE,
      o_last_name OUT student.last_name%TYPE)
    IS
      v_student_id student.student_id%TYPE;
    BEGIN
      SELECT first_name, last_name
        INTO o_first_name, o_last_name
        FROM student
      WHERE student_id = i_student_id;
    EXCEPTION
      WHEN OTHERS THEN
        dbms_output.put_line('Error in finding student_id: ' || v_student_id);
    END find_sname;
    FUNCTION id_is_good
      (i_student_id IN student.student_id%TYPE)
      RETURN BOOLEAN
    IS
      v_id_cnt number;
    BEGIN
      SELECT COUNT(*)
        INTO v_id_cnt
        FROM student
      WHERE student_id = i_student_id;
      RETURN 1 = v_id_cnt;
    EXCEPTION
      WHEN OTHERS THEN
        RETURN FALSE;
    END id_is_good;
  END manage_students;
  ```
  - To creat packages in a single script, use `/` on a line by itself to separate the `CREATE PACKAGE` and `CREATE PACKAGE BODY` script
- Referencing Package Elements
  - From outside the package: `package_name.element`
  - From inside the package: `element`
- Using a Package
  ```sql
  DECLARE
    v_first_name student.first_name%TYPE;
    v_last_name student.last_name%TYPE;
    v_id student.student_id%TYPE := &student_id;
  BEGIN
    IF manage_students.id_is_good(v_id) THEN
      manage_students.find_sname(v_id, v_first_name, v_last_name);
      dbms_output.put_line('Student No. ' || v_id || ' is '
        || v_last_name || ', ' || v_first_name);
    ELSE
      dbms_output.put_line('Student ID: ' || v_id || ' is not in the database.');
    END IF;
  END;
  ```
  - Anything that doesn't define in the specification are private, to use private functions run `EXECUTE package_name.private_definition;`
- Package Initialization
  - The first time a package is called, the initialization section is executed, if it exists
  - Package initialization code is placed after any procedures or functions
  ```sql
  CREATE OR REPLACE PACKAGE school_api AS
    v_current_date DATE;
    PROCEDURE Discount_Cost;
    FUNCTION new_instructor_id
      RETURN instructor.instructor_id%TYPE;
  END school_api;
  /
  CREATE OR REPLACE PACKAGE BODY school_api AS
    PROCEDURE discount_cost
    IS
      CURSOR c_group_discount
      IS
        SELECT distinct s.course_no, c.description
          FROM section s, enrollment e, course c
        WHERE s.section_id = e.section_id
          AND s.course_no = c.course_no
        GROUP BY s.course_no, c.description,
                e.section_id, s.section_id
        HAVING COUNT(*) >= 8;
    BEGIN
      FOR r_group_discount IN c_group_discount LOOP
        UPDATE course
          SET cost = cost * .95
          WHERE course_no = r_group_discount.course_no;
        dbms_output.put_line
          ('A 5% discount has been given to '
          || r_group_discount.course_no || ' '
          || r_group_discount.description);
      END LOOP;
    END discount_cost;
    FUNCTION new_instructor_id
      RETURN instructor.instructor_id%TYPE
    IS
      v_new_instid instructor.instructor_id%TYPE;
    BEGIN
      SELECT INSTRUCTOR_ID_SEQ.NEXTVAL
        INTO v_new_instid
        FROM dual;
      RETURN v_new_instid;
    EXCEPTION
      WHEN OTHERS THEN
        DECLARE
          v_sqlerrm VARCHAR2(250) := SUBSTR(SQLERRM, 1, 250);
        BEGIN
          RAISE_APPLICATION_ERROR(-20003,
            'Error in instructor_id: ' || v_sqlerrm);
        END;
    END new_instructor_id;
    -- Initial starts
    BEGIN
      SELECT trunc(sysdate, 'DD')
        INTO v_current_date
        FROM dual;
  END school_api;
  ```
- Access a variable from a package
  ```sql
  DECLARE
    v_date DATE;
  BEGIN
    v_date := school_api.v_current_date;
    dbms_output.put_line('Current date from package: ' || v_date);
  END;
  ```

#### Oracle Supplied Packages

- Oracle supplies 100s of PL/SQL packages
- [Click](https://docs.oracle.com/en/database/oracle/oracle-database/18/arpls/index.html) for complete PL/SQL Packages and Types Reference
- Steps to check package content like `DBMS_OUTPUT` in SQL Developer
  1. Expand the SYS user
  2. Expand the Packages node
  3. Scroll to DBMS_OUTPUT
  4. Expand it to see its parameters
  5. Select it to see its specification
  6. Select DBMS_OUTPUT Body
- `dbms_job` package allows the scheduling of execution of PL/SQL procedures
  - `dbms_job.submit()`, Enters a PL/SQL procedure as a job into the job queue
  ```sql
  -- Example Procedure
  CREATE OR REPLACE PROCEDURE new_course
    (course_name IN course.description%TYPE)
  AS
  BEGIN
    INSERT INTO course
      (course_no, description, created_by, created_date, modified_by, modified_date)
      VALUES(course_no_seq.NEXTVAL, course_name, USER, SYSDATE, USER, SYSDATE);
  END;
  -- Submit the job
  -- Parameters
  /* job - OUT Mode, The unique number that identifies the job in the job queue
  * what - IN Mode, The PL/SQL procedure and parameters that execute as part of this job
  * next_date - IN Mode, The next execution date for the job
  * interval - IN Mode, The calculation to compute the next date of the job; this can make use of SYSDATE and any date function
  * no_parse - IN Mode, FALSE (default): Procedure is parsed for validity at submission, TRUE: procedure is parsed when job first runs
  */
  DECLARE
    v_job_no NUMBER;
  BEGIN
    dbms_job.SUBMIT(job       => v_job_no,
                    what      => 'new_course(''Oracle PL/SQL Programming'');',
                    next_date => SYSDATE,
                    interval  => 'SYSDATE + 1/4');
    COMMIT;
    dbms_output.put_line(v_job_no);
  END;
  -- See Jobs in the Queue
  SELECT job, last_date, last_sec, next_date, next_sec, broken, what
  FROM dba_jobs;
  ```
  - `dbms_job.remove()`, Removes a previously submitted PL/SQL procedure from the job queue, e.g. `EXEC dbms_job.remove(n)`
  - `dbms_job.change()`, Changes the parameters that have been set for a previously submitted job (description, next run time or interval), `EXEC dbms_job.change(n, NULL, NULL, 'SYSDATE + 1/24');` timing format are shown as follows
  ```sql
  ALTER SESSION SET NLS_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS';
  -- Now and 2 days from now
  SELECT SYSDATE, TO_CHAR(SYSDATE + 2) FROM dual;
  -- Now and 6 hours from now
  SELECT SYSDATE, TO_CHAR(SYSDATE + 1/4) FROM dual;
  -- Now and 1 hour from now
  SELECT SYSDATE, TO_CHAR(SYSDATE + 1/24) FROM dual;
  -- Now and 1 minute from now
  SELECT SYSDATE, TO_CHAR(SYSDATE + 60/86400) FROM dual;
  -- There are 86,400 seconds in 1 day
  ```
  - `dbms_job.broken()`, Disables a job in the queue, e.g. set job n to be broken `EXEC dbms_job.broken(n, TRUE);`
  - `dbms_job.interval()`, Alters the interval set for an existing job
  - `dbms_job.next_date()`, Changes the next time an existing job runs
  - `dbms_job.run()`, Forces the run of a job regardless of schedule, e.g. `EXEC dbms_job.run(n);`

#### EXPLAIN PLAN

- This statement displays execution plans chosen by the Oracle optimizer for SELECT, UPDATE, INSERT, and DELETE statements
  ```sql
  EXPLAIN PLAN FOR
  SELECT s.course_no,
        c.description,
        i.first_name,
        i.last_name,
        s.section_no,
        TO_CHAR(s.start_date_time, 'Mon-DD-YYYY HH:MIAM'),
        s.location
    FROM section s,
        course c,
        instructor i
  WHERE s.course_no     = c.course_no
  AND   s.instructor_id = i.instructor_id;
  -- To see the plan, issue this command which uses the dbms_xplan package
  SELECT * FROM TABLE(dbms_xplan.display);
  -- The TABLE function converts the output of the display procedure into a table that can be queried by SELECT
  ```
- A statement's execution plan is the sequence of operations Oracle performs to run the statement
- Cardinality is the estimated number of rows the operation will return
- Cost is not expressed in any actual units, it is relative to other execution plans
  - Cost is a numeric internal measure that represents the estimated resource usage for an execution plan
  - The lower the cost, the more efficient the plan
- When using SQL Developer, Click the `Explain Plan...` button on the toolbar, or press `F10` to see the execution plan

### MySQL Scripts

#### System Stored Procedures

- Pieces of executable code stored in the database (small programs)
- Stored procedures require procedural code
- For MySQL
  - System Stored Procedures are pre-defined stored procedures with name:
    - `sp_help <column_name>` see help about a column
    - `sp_server_info` see info about the server
  - Procedures are stored in the data dictionary `sys.procedures`, `sys.sql_modules`

#### Create Procedures

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

#### Alter a Procedure

```sql
ALTER PROCEDURE procedure_name
	@param1 DATATYPE,
	@param2 DATATYPE
AS
…SQL COMMAND WITH @param1, @param2…
```

#### Delete a Procedure

```sql
DROP PROCEDURE procedure_name;
```

#### Run Procedure

- use `EXEC` to run procedures
  ```sql
  EXEC sp_help
  EXEC procedure_name 'column_name';
  ```
- Can accept command line parameters, separated by commas
- functions are not accepted, new variables need to be declared to store values from function. `EXEC procedure_name @param1=‘value1’, @param2=‘value2’;`
- Parameters can be positional or named, `EXEC procedure_name value1 value2;`
- SET, It is used to assign value.
  ```sql
  SET @variable_name = value;
  SET @variable_name = NULL;
  SET @variable_name = <SQL Command that return a single value>
  ```

#### Conditional Structure

- IF
  ```sql
  IF @ref_error = 1
  SET @error_msg = 'NOT FOUND';
  ```
- IF/ELSE statements
  ```sql
  IF @ref_error = 0
    SET @error_msg = 'FOUND';
  ELSE
    SET @error_msg = 'NOT FOUND';
  ```
- CASE statements
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
- WHILE Loop
  ```sql
  WHILE @@FETCH_STATUS = 0
  BEGIN
    <loop processing>
  END
  ```
- BREAK
  - It is used to break the loop.
- CONTINUE
  - Used to advance to the next iteration of a loop.

#### Cursor

- Used to access a SELECT result set one row at a time
- Steps to use a cursor
  1. DECLARE a cursor with a SELECT statement
  2. OPEN the cursor
  - This executes the SELECT statement and populates the cursor
  3. FETCH one row at a time from the result set INTO variables
  - Each column fetched must have a correlating variable
  - Perform whatever processing desired for each row
  4. CLOSE the cursor
  5. DEALLOCATE the cursor
- Example
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
- `@@FETCH_STATUS`, Returns the status of the last cursor FETCH statement
  - 0 = The FETCH statement was successful
  - -1 = The FETCH statement failed or the row was beyond the result set
  - -2 = The row fetched is missing

#### Trigger

- A trigger is a special stored procedure attached to a specific table.
- It is Event-driven, it is "Fired" automatically in response to event
- Can't pass values into a trigger, values can be declared inside a trigger.
- Example
  ```sql
  CREATE TRIGGER employees_insert
  ON employees
  AFTER INSERT, UPDATE #triggered by both insert and update operation
  AS
  UPDATE company_stats
  SET number_of_employees = number_of_employees + 1;
  ```
- During trigger execution, two special tables are used: deleted and inserted
- SQL Server automatically creates and manages these tables
- They have identical schema to the table being modified
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
- Improvement for updating multiple records
  ```sql
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
  ```
- Trigger with Cursor
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
- To delete an existing trigger use: `DROP TRIGGER Trigger_Name`
- Every CREATE TRIGGER statement generates entries
  - For SQL Server
    - sys.triggers
    - sys.trigger_events
    - sys.events
    - sys.sql_modules

#### Transcation

- `COMMIT` makes events within a transaction permanent
  ```sql
  BEGIN TRANSACTION T1;
  UPDATE physicians SET specialty = 'Hematology' WHERE physician_id = 2;
  UPDATE patients SET allergies = 'Almonds' WHERE patient_id = 1251;
  SELECT * FROM physicians WHERE physician*id = 2;
  SELECT * FROM patients WHERE patient*id = 1251;
  COMMIT TRANSACTION T1;
  ```
- `ROLLBACK` erases events within a transaction
  ```sql
  BEGIN TRANSACTION;
  UPDATE physicians SET specialty = 'Hematology' WHERE physician_id = 2;
  UPDATE patients SET allergies = 'Almonds' WHERE patient_id = 1251;
  SELECT * FROM physicians WHERE physician*id = 2;SELECT * FROM patients WHERE patient*id = 1251;
  ROLLBACK TRANSACTION;
  ```
- `SAVEPOINT` marks a place in a transaction to where a partial rollback may be made

## Database Admin

### Postgres

- `VACUUM FULL ANALYZE;`
  - `ANALYZE;` collects statistics about the contents of tables in the database, and stores the results in the pg_statistic system catalog
    - It helps the query planner uses updated statistics to determine the most efficient execution plans for queries
  - `VACUUM FULL;` reclaim disk space occupied by deleted or obsolete data
- `SELECT * FROM pg_stat_activity;` return list of current activity and connections
- `SELECT pg_cancel_backend(pid) FROM pg_stat_activity;` disconnect from client by `pid`
- `CREATE EXTENSION pg_stat_statements;` install `pg_stat_statements` extension
- `SELECT query, total_exec_time, calls FROM pg_stat_statements ORDER BY total_exec_time DESC LIMIT 10` view the top 10 most time consuming queries

#### Tablespace

- A tablespace can be used to specify the disk location for storing database objects
  - The default tablespace is `pg_default`
