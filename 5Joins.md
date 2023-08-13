Joins
```
JOINING TABLES
1. All RDBMS are relational in nature, we refer to other tables to get meaningful outcomes.


2. FK are used to do reference to other table.

```

```
3. INNER JOIN
    1. Returns a resultant table that has matching values from both the tables or all the tables.
        There should be a common attribute b/w both table.
    2. SELECT column-list FROM table1 INNER JOIN table2 ON condition1
        INNER JOIN table3 ON condition2 ... ;
    3. Alias in MySQL (AS)
        1. Aliases in MySQL is used to give a temporary name to a table or a column in a table for the purpose of
            a particular query. It works as a nickname for expressing the tables or column names.
            It makes the query short and neat.
        3. SELECT col_name AS alias_name FROM table_name;
        4. SELECT col_name1, col_name2,... FROM table_name AS alias_name;
```
<img width="271" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/c16bf89b-9791-455d-b5e5-6ad02a85a7dd">

  
4. OUTER JOIN
```
    1. LEFT JOIN
        1. This returns a resulting table that all the data from left table and the matched data from the right table.
        2. SELECT columns FROM table LEFT JOIN table2 ON Join_Condition;
    
    2. RIGHT JOIN
        1. This returns a resulting table that all the data from right table and the matched data from the left table.
        2. SELECT columns FROM table RIGHT JOIN table2 ON join_cond;
    
    3. FULL JOIN
        1. This returns a resulting table that contains all data when there is a match on left or right table data.
        2. Emulated in MySQL using LEFT and RIGHT JOIN.
        3. LEFT JOIN UNION RIGHT JOIN.
        4. SELECT columns FROM table1 as t1 LEFT JOIN table2 as t2 ON t1.id = t2.id
        UNION
        SELECT columns FROM table1 as t1 RIGHT JOIN table2 as t2 ON t1.id = t2.id;
        5. UNION ALL, can also be used this will duplicate values as well while UNION gives unique values.
```

<img width="283" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/95fd9a6c-afef-4202-8df1-832887e20f87">

<img width="270" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/aadb1c41-b888-4a2e-b585-8111b345db62">

<img width="294" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/e17eb541-cba1-496e-989c-94cfc78084fd">


5. CROSS JOIN
```
        1. This returns all the cartesian products of the data present in both tables. Hence, all possible variations
        are reflected in the output.
        2. Used rarely in practical purpose.
        3. Table-1 has 10 rows and table-2 has 5, then resultant would have 50 rows.
        4. SELECT column-lists FROM table1 CROSS JOIN table2;
```
<img width="338" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/d8e49652-ddd0-41b3-9715-bc92ad650140">



6. SELF JOIN
```
        1. It is used to get the output from a particular table when the same table is joined to itself.
        2. Used very less.
        3. Emulated using INNER JOIN.
        4. SELECT columns FROM table as t1 INNER JOIN table as t2 ON t1.id = t2.id;
```


7. Join without using join keywords.
```
        1. SELECT * FROM table1, table2 WHERE condition;
        2. e.g., SELECT artist_name, album_name, year_recordedFROM artist, albumWHERE artist.id = album.artist_id;

```

<img width="497" alt="joints" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/7d88d559-a25d-4ae3-a2d6-72e5601fcacf">



All Code of JOINS
```
-- Joins 
CREATE DATABASE joinsConcept;
USE joinsConcept;
DROP DATABASE company;

CREATE TABLE company(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(40),
    salary INT,
    age INT,
    phone_No BIGINT
);

INSERT INTO company VALUES
						(1,'Sam',20000,23,7991132070),
                        (2,'Ram',400000,43,7991132071),
                        (3,'Mohan',34000,53,7991132072),
                        (4,'Dam',2000,13,7991132073),
                        (5,'Leela',10000,83,7991132074);

SELECT * FROM company;
DROP TABLE company;

CREATE TABLE staff(
	staff_id INT PRIMARY KEY,
    staff_name VARCHAR(30),
    address VARCHAR(70),
    job VARCHAR(40),
    staff_salary INT,
    FOREIGN KEY (staff_id) REFERENCES company(id)
);

INSERT INTO staff VALUES 
					(1,'Mohan','Patna',10000,53),
					(2,'Sohan','Delhi',300000,23),
					(3,'Rohan','Kolkata',24000,63),
					(4,'Jhon','Up',400,43),
					(5,'Sameera','Kerla',3000,13);

DROP TABLE staff;
SELECT * FROM staff;

CREATE TABLE project(
	clientId INT PRIMARY KEY,
    clientName VARCHAR(80),
    project VARCHAR(90),
    FOREIGN KEY (clientId) REFERENCES company(id)
);

INSERT INTO project VALUES 
					(1,'A','C++'),
					(2,'B','DSA'),
					(3,'F','WEB');
					-- (4,'R','PYTHON'),
					-- (5,'S','C'), 
                    -- (6,'T','Js');
                    
INSERT INTO project VALUES(6,'T','Js');
DROP TABLE project;
SELECT *FROM project;

-- Joins -> It will give sum of column of both table 
SELECT * FROM company as co
INNER JOIN project as p ON co.id=P.clientId;

-- Inner Join 
-- Q. Enlist all the employee ID's name along with Project allocated to them
SELECT co.id,co.name,co.salary,p.clientId,p.project from company as co
INNER JOIN project as p ON co.id=p.clientId;

-- Q. Fetch out all the employee ID's & their contact detail who have
-- been working in Delhi with client having project DSA  
SELECT s.staff_id , s.staff_name , s.staff_salary , p.clientName , p.project from staff as s 
INNER JOIN project as p on s.staff_id=p.clientId WHERE project ='DSA' AND s.address='Delhi';

-- Q. Can we get data same as INNER JOIN without using keyword inner join 
SELECT co.id,co.name,co.salary,p.clientId,p.project from company as co,
project as p WHERE co.id=p.clientId;

-- left join
-- Q. Fetch out each project allocated to each employee .
SELECT * FROM staff as s
LEFT JOIN project as p ON s.staff_id = p.clientId;


-- right join
-- Q. List out all the project along with staff name and their location 
SELECT p.clientId , p.clientName ,s.staff_name FROM staff as s
RIGHT JOIN project as p ON s.staff_id = p.clientId;


-- Client name -> to get the maximum combination 
-- Q. List out all combination possible for employee's name & project that can exist 
SELECT s.staff_name,p.clientId,p.clientName from staff AS s
CROSS JOIN project AS p;
```



**Set**
```
       SET OPERATIONS
        1. Used to combine multiple select statements.
        2. Always gives distinct rows.


        3. UNION
            1. Combines two or more SELECT statements.
            2. SELECT * FROM table1
            UNION
            SELECT * FROM table2;
            3. Number of column, order of column must be same for table1 and table2.


	-- Union vS Joins 
		Union works on rows as it will find out the distnict rows by combining both table.
		Full Joins find out columns a/q to requirement that are matching 

        4. INTERSECT
            1. Returns common values of the tables.
            2. Emulated.
            3. SELECT DISTINCT column-list FROM table-1 INNER JOIN table-2 USING(join_cond);
            4. SELECT DISTINCT * FROM table1 INNER JOIN table2 ON USING(id);



        5. MINUS
            1. This operator returns the distinct row from the first table that does not occur in the second table.
            2. Emulated.
            3. SELECT column_list FROM table1 LEFT JOIN table2 ON condition WHERE table2.column_name IS NULL;
            4. e.g., SELECT id FROM table-1 LEFT JOIN table-2 USING(id) WHERE table-2.id IS NULL;

```


All Code of Set Operations
```
-- Set Operations
CREATE DATABASE library;
SHOW DATABASES;
CREATE TABLE books(
	id INT PRIMARY KEY,
    name VARCHAR(120),
    type VARCHAR(50)
);
INSERT INTO books VALUES(1,'C++','Computer'),
						(2,'DSA','Computer'),
                        (3,'Math','Math'),
                        (4,'Human Life','kids'),
                        (5,'Calculus','Math'),
						(6,'ABC','kids');
SELECT * FROM books;
DROP TABLE books;

CREATE TABLE magzine(
	id INT PRIMARY KEY,
    name VARCHAR(120),
    type VARCHAR(50)
);
INSERT INTO magzine VALUES(1,'Star Lord','Adult'),
                        (3,'Champak','Kids'),
                        (5,'Balhansh','Kids');
INSERT INTO magzine VALUES(7,'Java','Computer');
SELECT * FROM magzine;
DROP TABLE magzine;

-- Union
SELECT * FROM books 
UNION 
SELECT * FROM magzine; 

-- Q. List out all name who read kids book
SELECT * FROM books WHERE type ='kids'
UNION
SELECT * FROM books WHERE type ='kids';

-- Intersection
	-- INTERSECT will not work directly so we had to emulate it using inner join 
-- Q. List all pepole who read both books & magzine ?
SELECT * FROM magzine INNER JOIN books using (id); 
SELECT books.* FROM magzine INNER JOIN books using (id); 

-- Minus Here we had to put NULL which we are not choosing 
-- List all people who read books but not magzine
SELECT books .* FROM books LEFT JOIN magzine using (id)
WHERE magzine.id is NULL;

-- List all people who read magzine but not books
SELECT magzine .* FROM magzine LEFT JOIN books using (id)
WHERE books.id is NULL;
```


SUB QUERIES
```
    1. Outer query depends on inner query.
    2. Alternative to joins.
    3. Nested queries.
    4. SELECT column_list (s) FROM table_name WHERE column_name OPERATOR
    (SELECT column_list (s) FROM table_name [WHERE]);
    5. e.g., SELECT * FROM table1 WHERE col1 IN (SELECT col1 FROM table1);
    6. Sub queries exist mainly in 3 clauses
	1. Inside a WHERE clause.
	2. Inside a FROM clause.
	3. Inside a SELECT clause

    7. Subquery using FROM clause
	1. SELECT MAX(rating) FROM (SELECT * FROM movie WHERE country = ‘India’) as temp;

    8. Subquery using SELECT
	1. SELECT (SELECT column_list(s) FROM T_name WHERE condition), columnList(s) FROM T2_name WHERE
    condition;

    9. Derived Subquery
	1. SELECT columnLists(s) FROM (SELECT columnLists(s) FROM table_name WHERE [condition]) as new_table_name;

    10. Co-related sub-queries
	1. With a normal nested subquery, the inner SELECT query
	    runs first and executes once, returning values to be used by
	    the main query. A correlated subquery, however, executes
	    once for each candidate row considered by the outer query.
	    In other words, the inner query is driven by the outer query
```
<img width="385" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/60b3a8fc-1121-4186-9acf-23f0f1c61a4e">

 Co-related sub-queries
 
<img width="389" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/4bfe0cc2-f301-4358-a1c7-8bcf8aa33a96">

</br>

<img width="515" alt="image" src="https://github.com/Prashantkry/DMS_Notes/assets/71703153/f65f1110-3c05-42bf-9591-4b8477c5b801">



