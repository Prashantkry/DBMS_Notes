# DMS_Notes
> To run in CMD -> mysql -u root -p

SQL
```
 Structured Query Language, used to access and manipulate data.
 SQL used CRUD operations to communicate with DB.
 SQL is not DB, is a query language.
```
Few Commands 
```
1. CREATE - execute INSERT statements to insert new tuple into the relation.
2. READ - Read data already in the relations.
3. UPDATE - Modify already inserted data in the relation.
4. DELETE - Delete specific data point/tuple/row or multiple rows.
```
What is RDBMS? (Relational Database Management System)
```
1. Software that enable us to implement designed relational model.
2. e.g., MySQL, MS SQL, Oracle, IBM etc.
3. Table/Relation is the simplest form of data storage object in R-DB.
4. MySQL is open-source RDBMS, and it uses SQL for all CRUD operations
5. MySQL used client-server model, where client is CLI or frontend that used services provided by MySQL server.
```
Difference between SQL and MySQL
```
SQL is Structured Query language used to perform CRUD operations in R-DB, while MySQL 	  is a RDBMS used to store, manage and administrate DB (provided by itself) using SQL.
SQL DATA TYPES (Ref: https://www.w3schools.com/sql/sql_datatypes.asp)
	1. In SQL DB, data is stored in the form of tables.
	2. Data can be of different types, like INT, CHAR etc.
```
DATATYPE Description
```
CHAR 		string(0-255), string with size = (0, 255], e.g., CHAR(251)
			It occupy complete space 255 byte even blank space will be occupied
			 _______________________________________
			|	|	|	|	|	|
			|   R	|   A	|   M	|	|	|
			|_______|_______|_______|_______|_______|

VARCHAR 	string(0-255)
			It occupy complete space 3 byte
			 ________________________
			|	|	|	|
			|   R	|   A	|   M	|
			|_______|_______|_______|

TINYTEXT 	String(0-255)
TEXT 		string(0-65535)
BLOB 		string(0-65535)	-> stroes audio video files in bytes (Binary Large Object)
MEDIUMTEXT 	string(0-16777215)
MEDIUMBLOB 	string(0-16777215)
LONGTEXT 	string(0-4294967295)
LONGBLOB 	string(0-4294967295)
TINYINT 	integer(-128 to 127)
SMALLINT 	integer(-32768 to 32767)
MEDIUMINT 	integer(-8388608 to 8388607)
INT 		integer(-2147483648 to 2147483647)
BIGINT 		integer (-9223372036854775808 to 9223372036854775807)
FLOAT 		Decimal with precision to 23 digits
DOUBLE		Decimal with 24 to 53 digits

DECIMAL 	Double stored as string
DATE 		YYYY-MM-DD
DATETIME 	YYYY-MM-DD HH:MM:SS
TIMESTAMP 	YYYYMMDDHHMMSS
TIME 		HH:MM:SS
ENUM 		One of the preset values
SET 		One or many of the preset values
BOOLEAN 	0/1
BIT 		e.g., BIT(n), n upto 64, store values in bits.
```

Signed / UnSigned
```
Ex- 
	by default Its signed but when we unsigned it we can increase its size
	TINYINT 	integer(-128 to 127)
	UNSIGNED TINYINT 	integer(0 to 255)

	create TABLE Table_Name(
		For creating it
		col INT,
		col2 INT UNSIGNED,
		col3 JSON	-- can also be used as data type
	);
```

Create Table 
```
create database College;
```

Select Database Name 
```
USE college;
```

Create Table
```
CREATE table Student(
	**-- 	keyword should be in capital  letter**
	id INT PRIMARY KEY,	  
    name VARCHAR(255)	-- 255 is length here
);
```

-- Inserting data in table 
> addding data in table is called entity  or tuple 
```
INSERT INTO Student VALUES(1,'Prasahnt');
```

-- show data available in table 
```
SELECT * FROM student;
```

Few Important command of DBMS SQL
```
1. DDL (data definition language): defining relation schema.
	1. CREATE: create table, DB, view.
	2. ALTER TABLE: modification in table structure. e.g, change column datatype or add/remove columns.
	3. DROP: delete table, DB, view.
	4. TRUNCATE: remove all the tuples from the table.
	5. RENAME: rename DB name, table name, column name etc.
2. DRL/DQL (data retrieval language / data query language): retrieve data from the tables.
	1. SELECT
3. DML (data modification language): use to perform modifications in the DB
	1. INSERT: insert data into a relation
	2. UPDATE: update relation data.
	3. DELETE: delete row(s) from the relation.
4. DCL (Data Control language): grant or revoke authorities from user.
	1. GRANT: access privileges to the DB
	2. REVOKE: revoke user access privileges.
5. TCL (Transaction control language): to manage transactions done in the DB
	1. START TRANSACTION: begin a transaction
	2. COMMIT: apply all the changes and end transaction
	3. ROLLBACK: discard changes and end transaction
	4. SAVEPOINT: checkout within the group of transactions in which to rollback.
 ```
MANAGING DB (DDL)
```
1. Creation of DB
1. CREATE DATABASE IF NOT EXISTS db-name;
2. USE db-name; //need to execute to choose on which DB CREATE TABLE etc commands will be executed. //make switching between DBs possible.
3. DROP DATABASE IF EXISTS db-name; //dropping database.
4. SHOW DATABASES; //list all the DBs in the server.
5. SHOW TABLES; //list tables in the selected DB.
```

