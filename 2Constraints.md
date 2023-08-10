

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



Default
	1. Set default value of the column.
	2. CREATE TABLE account (
		…
		saving-rate DOUBLE NOT NULL DEFAULT 4.25,
		…
	)



```

All code till now 
```
show databases;
use school;
show tables;
INSERT INTO TEACHER VALUE(2,'Prashant');
INSERT INTO TEACHER VALUE(3,'BOOK'),
						 (4,'COPY')	;
SELECT * FROM TEACHER;

-- add column 
ALTER TABLE teacher
ADD salary int;

-- adding data in column of salary 
-- UPDATE teacher
-- SET salary=values(2000),(30000),(40000),(50000)
-- WHERE id=1,2,3,4;


-- adding another table 
CREATE TABLE student(
	student_id INT PRIMARY KEY,
    name VARCHAR(255),
    roll INT
);

-- deleting table 
DROP TABLE student;

-- adding another table with forign key 
CREATE TABLE staff(
	satff_id INT PRIMARY KEY ,
    name VARCHAR(30),
    address VARCHAR(100),
    phone INT,
    FOREIGN KEY(phone) REFERENCES TEACHER(id)
);


-- unique and check 
CREATE TABLE profile(
	reg_no INT PRIMARY KEY,
    name VARCHAR(250) UNIQUE,
    marks INT ,
    CONSTRAINT minScore CHECK(marks>45),
    roll_no INT NOT NULL DEFAULT 10
);

-- Inserting in Unique and Check
INSERT INTO profile VALUES(102,'Prashant',93);

SELECT *FROM profile;

DROP TABLE profile;

-- Default




```

