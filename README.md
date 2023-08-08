# DMS_Notes
Create Table 

```create database College;```

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
