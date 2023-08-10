

__Constraints__
```
Primary Key
	Not NULL
	Unique
	only 1 primary key per table
	try to put int mostly

	Syntax:
	CREATE TABLE Customer(
		id int PRIMARY KEY,
		F_Name CHAR(30),
		L_Name CHAR(20),
		DOB    DATE,
		Gender  char(10)
	    --	PRIMARY KEY(id)		// way 2nd to set 
	);

Foreign Key
	FK refers to PK of other table.
	Each relation can having any number of FK.
	CREATE TABLE ORDER (
		id INT PRIMARY KEY,
		delivery_date DATE,
		order_placed_date DATE,
		cust_id INT,
		FOREIGN KEY (cust_id) REFERENCES customer(id)
	);

				OR
	
	-- adding another table with forign key 
	CREATE TABLE staff(
		satff_id INT PRIMARY KEY ,
	    name VARCHAR(30),
	    address VARCHAR(100),
	    phone INT,
	    FOREIGN KEY(phone) REFERENCES TEACHER(id)
	);



UNIQUE
	Unique, can be null, table can have multiple unique atributes.
	CREATE TABLE customer (
		…
		email VARCHAR(1024) UNIQUE,
		…
	);



CHECK
	CREATE TABLE customer (
		…
		CONSTRAINT age_check CHECK (age > 12),
		…
	);
	“age_check”, can also avoid this, MySQL generates name of constraint automatically
	
		
	
	-- unique and check 
	CREATE TABLE profile(
		reg_no INT PRIMARY KEY,
	    name VARCHAR(250) UNIQUE,
	    marks INT ,
	    CONSTRAINT minScore CHECK(marks>45)
	);

	
	-- Inserting in Unique and Check
	INSERT INTO profile VALUES(102,'Prashant',93);

```
