# DMS_Notes
> To run in CMD -> mysql -u root -p

```
Database is a collections of data in a format that can be easily accessed 
A software applications that is used to manage DB is called DBMS
		User -> (SQL) -> DBMS   ->  DB
```

SQL
```ruby
 Structured Query Language, used to access and manipulate data.
 SQL used CRUD operations to communicate with DB.
 SQL is not DB, is a query language.
```
Few Commands 
```ruby
1. CREATE - execute INSERT statements to insert new tuple into the relation.
2. READ - Read data already in the relations.
3. UPDATE - Modify already inserted data in the relation.
4. DELETE - Delete specific data point/tuple/row or multiple rows.
```
What is RDBMS? (Relational Database Management System)
```ruby
1. Software that enable us to implement designed relational model.
2. e.g., MySQL, MS SQL, Oracle, IBM etc.
3. Table/Relation is the simplest form of data storage object in R-DB.
4. MySQL is open-source RDBMS, and it uses SQL for all CRUD operations
5. MySQL used client-server model, where client is CLI or frontend that used services provided by MySQL server.
```
Difference between SQL and MySQL
```ruby
SQL is Structured Query language used to perform CRUD operations in R-DB, while MySQL is a RDBMS used to store, manage and administrate DB (provided by itself) using SQL.
SQL DATA TYPES (Ref: https://www.w3schools.com/sql/sql_datatypes.asp)
	1. In SQL DB, data is stored in the form of tables.
	2. Data can be of different types, like INT, CHAR etc.
```
DATATYPE Description
```ruby
CHAR 		string(0-255), string with size = (0, 255], e.g., CHAR(251)
			It occupy complete space 255 byte even blank space will be occupied
			 _______________________________________
			|	|	|	|	|	|	|		|		|
			|   R	|   A	|   M	|		|		|
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
```ruby
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

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/953f75cf-10f3-4020-b471-be3448856ae1)

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/d6c98d38-8352-4ea5-870c-614d87e3a6c0)


Create Table 
```ruby
create database College;
```

Select Database Name 
```ruby
USE college;
```

Create Table
```ruby
CREATE table Student(
	**keyword should be in capital  letter**
	id INT PRIMARY KEY,	  
    name VARCHAR(255)	-- 255 is length here
);
```

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/c7382cbf-9c8a-4a0f-8800-cb60ac86b360)


Inserting data in table 
> addding data in table is called entity  or tuple 
```ruby
INSERT INTO Student VALUES(1,'Prasahnt');
INSERT INTO Worker VALUES(5,"Sweety","",20000,'28-08-23 09.00.00','Front-End Developer');
INSERT INTO Worker VALUES(6,"Rahul","Kr",20000,null,'Front-End Developer');
```

Deleting data in database 
```ruby
DROP database IF EXISTS Data_base_name;
	-- deleting table 
	DROP TABLE student;
```

show data available in table 
```ruby
SELECT * FROM Data_base_name;
```

Few Important command of DBMS SQL
```ruby
1. DDL (data definition language): defining relation schema.
	1. CREATE: create table, DB, view.
	2. ALTER TABLE: modification in table structure. e.g, change column datatype or add/remove columns.
	3. DROP: delete complete table, DB, view.
	4. TRUNCATE: remove all the tuples from the table.
		WE will not delete schema just all entries or user 
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
```ruby
1. Creation of DB
	1. CREATE DATABASE IF NOT EXISTS db-name;
		IF NOT EXISTS -> agar ni h tasb hi banana h DataBase ko
	2. USE db-name; //need to execute to choose on which DB CREATE TABLE etc commands will be executed. //make switching between DBs possible.
	3. DROP DATABASE IF EXISTS db-name; //dropping database.
	4. SHOW DATABASES; //list all the DBs in the server.
	5. SHOW TABLES; //list tables in the selected DB.
```

__Making a complete Database of an Organization__
```
create database Organization;
USE Organization;
create table Worker(
	Worker_Id INT NOT NULL primary KEY auto_increment,
	First_Name CHAR(25),
    Last_Name CHAR(25),
    Salary int(15),
    Joining_Date datetime,
    Department char(25)
);

INSERT INTO Worker
	(Worker_Id , First_Name , Last_Name , Salary , Joining_Date , Department)
	VALUES (1,"Sweety","Reddi",100000,'28-08-23 09.00.00','TRA'),
			(2,"Prashant","kr",12000,'28-09-23 08.00.00','Front-End Developer'),
            (3,"Sagarika","Reddi",300000,'18-08-23 19.00.00','TRA'),
            (4,"Bittu","kr",80000,'18-08-23 10.00.00','Full Stack Developer');
            
create table Bonus(		-- making foriegn key
	Worker_Ref_Id INT,
    Bonus_Amount int(15),
    Bonus_Date datetime,
    foreign key (Worker_Ref_Id)
		references Worker(Worker_Id)
        ON delete cascade
);

INSERT INTO Bonus
	(Worker_Ref_Id , Bonus_Amount , Bonus_Date)
	VALUES (1,100000,'28-08-23'),
			(2,50000,'12-08-23'),
            (3,5600,'04-08-23'),
            (4,20000,'05-08-23');

create table Title(		-- making foriegn key
	Worker_Ref_Id INT,
    Worker_Title CHAR(25),
    Affected_from datetime,
    foreign key (Worker_Ref_Id)
		references Worker(Worker_Id)
        ON delete cascade
);

INSERT INTO Title
	(Worker_Ref_Id , Worker_Title , Affected_from)
	VALUES (1,'TRA','28-08-23'),
			(2,'web developer' ,'12-08-23'),
            (3,'front-end','04-08-23'),
            (4,'back-end','05-08-23');
            
show databases;
show tables;
select *from Worker;
select *from bonus;
select *from title;
DROP database IF EXISTS Orgainzations;

```

To know single particular field data  
```ruby
Select First_Name from worker;
```

To know multiple particular field data  
```ruby
Select First_Name ,Salary from worker;
```

__DATA RETRIEVAL LANGUAGE (DRL)__

```ruby
1. Syntax: SELECT <set of column names> FROM <table_name>;
2. Order of execution from RIGHT to LEFT.
3. Q. Can we use SELECT keyword without using FROM clause?
	1. Yes, using DUAL Tables.
	2. Dual tables are dummy tables created by MySQL, help users to do certain obvious actions without referring to user
	defined tables.
	3. e.g., SELECT 55 + 11;

	
	SELECT now();	-- -> to know current time and  date
	
	select ucase("cse");	-- convert to upper case
	
	select lcase("CSE");	-- convert to lower case


4. WHERE
	1. Reduce rows based on given conditions.
		E.g., 	select *from WORKER WHERE salary>50000;
			select *from WORKER WHERE department='TRA';

5. BETWEEN
	1. SELECT * FROM customer WHERE age between 0 AND 100;
		0 and 100 are inclusive
	2. select *from WORKER WHERE salary between 80000 and 300000;


6. IN
	1. Reduces OR conditions;
		SELECT * FROM officers WHERE officer_name IN ('Lakshay', ‘Maharana Pratap', ‘Deepika’);
		select * from Worker WHERE DEPARTMENT in ('TRA','Front-End Developer');

7. AND/OR/NOT
	1. AND: WHERE cond1 AND cond2
		select * from Worker WHERE DEPARTMENT = 'TRA' and DEPARTMENT = 'Front-End Developer';
	2. OR: WHERE cond1 OR cond2
		select * from Worker WHERE DEPARTMENT = 'TRA' OR DEPARTMENT = 'Front-End Developer';
	3. NOT: WHERE col_name NOT IN (1,2,3,4);
		select * from Worker WHERE DEPARTMENT NOT IN ('TRA','Front-End Developer');

8. IS NULL
	SELECT * FROM customer WHERE prime_status is NULL;
	select *from Worker where Joining_Date is Null;

9. Pattern Searching / Wildcard (‘%’, ‘_’)
	1. ‘%’, any number of character from 0 to n. Similar to ‘*’ asterisk in regex.
	2. ‘_’, only one character.
		SELECT * FROM customer WHERE name LIKE ‘%p_’;
		-- wild card 
		select *from Worker where First_Name LIKE '%i%';
		select *from Worker where First_Name LIKE '___t%';


10. ORDER BY
	1. Sorting the data retrieved using WHERE clause.
	2. ORDER BY <column-name> DESC;
	3. DESC = Descending and ASC = Ascending
		SELECT * FROM customer ORDER BY name DESC;
		-- sorting by default ascending use dec for descending 
		select *from Worker order by salary;
		select *from Worker order by salary desc;

11. GROUP BY
	1. GROUP BY Clause is used to collect data from multiple records and group the result by one or more column. It is
	generally used in a SELECT statement.
	2. Groups into category based on column given.
	3. SELECT c1, c2, c3 FROM sample_table WHERE cond GROUP BY c1, c2, c3.
	4. All the column names mentioned after SELECT statement shall be repeated in GROUP BY, in order to successfully
	execute the query.
	5. Used with aggregation functions to perform various actions.
		1. COUNT()
		2. SUM()
		3. AVG()
		4. MIN()
		5. MAX()

12. DISTINCT
	1. Find distinct values in the table.
		SELECT DISTINCT(col_name) FROM table_name;
		-- distnict or unique value 
		select distinct department from Worker ;
	2. GROUP BY can also be used for the same
		1. “Select col_name from table GROUP BY col_name;” same output as above DISTINCT query
		2. SQL is smart enough to realise that if you are using GROUP BY and not using any aggregation function, then
		you mean “DISTINCT”
		
		-- group by	-> to know no of emoployee in  different department
		select department, count(department) from worker group by department;
	AVG
		-- AVG salary per department 
		select department, AVG(salary) from worker group by department;

	Min
	-- Min salary per department 
		select department, MIN(salary) from worker group by department;
	
	Max
	-- Max salary per department 
		select department, MAX(salary) from worker group by department;
	
	Sum
	-- Sum salary per department 
		select department, SUM(salary) from worker group by department;


13. GROUP BY HAVING
	1. Out of the categories made by GROUP BY, we would like to know only particular thing (cond).
	2. Similar to WHERE.
	3. Select COUNT(cust_id), country from customer GROUP BY country HAVING COUNT(cust_id) > 50;
	4. WHERE vs HAVING
		1. Both have same function of filtering the row base on certain conditions.
		2. WHERE clause is used to filter the rows from the table based on specified condition
		3. HAVING clause is used to filter the rows from the groups based on the specified condition.
		4. HAVING is used after GROUP BY while WHERE is used before GROUP BY clause.
		5. If you are using HAVING, GROUP BY is necessary.
		6. WHERE can be used with SELECT, UPDATE & DELETE keywords while GROUP BY used with SELECT
	
	-- group by having 
	select department, COUNT(department) FROM Worker group by department HAVING COUNT(department)>2;
```
![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/7b442e8c-7d01-4275-b8fd-f727809f5b27)

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/6cb4b4e5-69aa-4278-89a9-26dd1e30c0e8)

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/bf2e1524-f971-4dd7-8bd7-2f92964c9026)

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/5b4bc318-9ab1-402f-a773-76cab4b6ab27)

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/d184872c-4aca-444f-b61e-1506034a1455)

![image](https://github.com/Prashantkry/DBMS_Notes/assets/71703153/644cfaa2-c7dc-406d-831a-626e94e689cb)




All Code Till Now 
```
create database Organization;
USE Organization;
create table Worker(
	Worker_Id INT NOT NULL primary KEY auto_increment,
	First_Name CHAR(25),
    Last_Name CHAR(25),
    Salary int(15),
    Joining_Date datetime,
    Department char(25)
);

INSERT INTO Worker
	(Worker_Id , First_Name , Last_Name , Salary , Joining_Date , Department)
	VALUES  (1,"Sweety","Reddi",100000,'28-08-23 09.00.00','TRA'),
			(2,"Prashant","kr",12000,'28-09-23 08.00.00','Front-End Developer'),
            (3,"Sagarika","Reddi",300000,'18-08-23 19.00.00','TRA'),
            (4,"Bittu","kr",80000,'18-08-23 10.00.00','Full Stack Developer');
            
create table Bonus(		-- making foriegn key
	Worker_Ref_Id INT,
    Bonus_Amount int(15),
    Bonus_Date datetime,
    foreign key (Worker_Ref_Id)
		references Worker(Worker_Id)
        ON delete cascade
);

INSERT INTO Bonus
	(Worker_Ref_Id , Bonus_Amount , Bonus_Date)
	VALUES (1,100000,'28-08-23'),
			(2,50000,'12-08-23'),
            (3,5600,'04-08-23'),
            (4,20000,'05-08-23');

create table Title(		-- making foriegn key
	Worker_Ref_Id INT,
    Worker_Title CHAR(25),
    Affected_from datetime,
    foreign key (Worker_Ref_Id)
		references Worker(Worker_Id)
        ON delete cascade
);

INSERT INTO Title
	(Worker_Ref_Id , Worker_Title , Affected_from)
	VALUES (1,'TRA','28-08-23'),
			(2,'web developer' ,'12-08-23'),
            (3,'front-end','04-08-23'),
            (4,'back-end','05-08-23');
            
show databases;
show tables;
select *from Worker;
select *from bonus;
select *from title;
DROP database IF EXISTS OrEgainzations;

Select First_Name from worker;
Select First_Name ,Salary from worker;

select 44+55;

SELECT now();	-- -> to know current time and  date

select ucase("cse");	-- convert to upper case

select lcase("CSE");	-- convert to lower case

select *from WORKER WHERE salary>50000;
select *from WORKER WHERE department='TRA';


select *from WORKER WHERE salary between 80000 and 300000;

select * from Worker WHERE DEPARTMENT = 'TRA' OR DEPARTMENT = 'Front-End Developer';
select * from Worker WHERE DEPARTMENT = 'TRA' and DEPARTMENT = 'Front-End Developer';
INSERT INTO Worker VALUES(5,"Sweety","",20000,'28-08-23 09.00.00','Front-End Developer');
select * from Worker WHERE DEPARTMENT in ('TRA','Front-End Developer');
select * from Worker WHERE DEPARTMENT NOT IN ('TRA','Front-End Developer');
INSERT INTO Worker VALUES(6,"Rahul","Kr",20000,null,'Front-End Developer');
select *from Worker where Joining_Date is Null;

-- wild card 
select *from Worker where First_Name LIKE '%i%';
select *from Worker where First_Name LIKE '___t%';


-- sorting by default ascending use dec for descending 
select *from Worker order by salary;
select *from Worker order by salary desc;

-- distnict or unique value 
select distinct department from Worker ;

-- group by	-> to know no of emoployee in  different department
select department, count(department) from worker group by department;

-- AVG salary per department 
select department, AVG(salary) from worker group by department;

-- Min salary per department 
select department, MIN(salary) from worker group by department;


-- Max salary per department 
select department, MAX(salary) from worker group by department;


-- Sum salary per department 
select department, SUM(salary) from worker group by department;

-- group by having 
select department, COUNT(department) FROM Worker group by department HAVING COUNT(department)>2;


```
