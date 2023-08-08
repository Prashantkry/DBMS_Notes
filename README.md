# DMS_Notes
Create Table 
```create database College;```
USE college;

CREATE table Student(
	-- 	keyword should be in capital  letter
	id INT PRIMARY KEY,	  
    name VARCHAR(255)	-- 255 is length here
);

-- Inserting data in table 
INSERT INTO Student VALUES(1,'Prasahnt');

-- show data available in table 
SELECT * FROM student;
