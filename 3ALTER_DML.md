ALTER OPERATIONS
```
1. Changes schema


2. ADD
    1. Add new column.
    2. ALTER TABLE table_name ADD new_col_name datatype ADD new_col_name_2 datatype;
        ALTER TABLE customer ADD age INT NOT NULL;


3. MODIFY
    1. Change datatype of an attribute.
    2. ALTER TABLE table-name MODIFY col-name col-datatype;
        VARCHAR TO CHAR
    ALTER TABLE customer MODIFY name CHAR(1024);


4. CHANGE COLUMN
    1. Rename column name.
    2. ALTER TABLE table-name CHANGE COLUMN old-col-name new-col-name new-col-datatype;
        ALTER TABLE customer CHANGE COLUMN name customer-name VARCHAR(1024);


5. DROP COLUMN
    1. Drop a column completely.
    2. ALTER TABLE table-name DROP COLUMN col-name;
        ALTER TABLE customer DROP COLUMN middle-name;


6. RENAME
1. Rename table name itself.
2. ALTER TABLE table-name RENAME TO new-table-name;
    ALTER TABLE customer RENAME TO customer-details;

```

All code of alter table 
```
SHOW DATABASES;
USE SCHOOL;
SHOW TABLES;
SELECT * FROM teacher;

-- modify data or add data in coln salary 
ALTER TABLE teacher MODIFY salary DOUBLE NOT NULL DEFAULT 0;

-- describe details of table 
DESC teacher;

-- rename table 
ALTER TABLE teacher RENAME TO guru_Ji;


-- rename coln *HERE WE HAD TO TELL DATA TYPE ALSO IN COMMAND 
ALTER TABLE teacher CHANGE COLUMN salary salary_teacher INT;


-- DROP COLUMN 
ALTER TABLE teacher DROP salary_teacher;
```

DATA MANIPULATION LANGUAGE (DML)
```

1. INSERT
    INSERT INTO table-name(col1, col2, col3) VALUES (v1, v2, v3), (val1, val2, val3);


2. UPDATE
    1. UPDATE table-name SET col1 = 1, col2 = ‘abc’ WHERE id = 1;
    2. Update multiple rows e.g.,
          UPDATE student SET standard = standard + 1;
    3. ON UPDATE CASCADE
          Can be added to the table while creating constraints. Suppose there is a situation where we have two tables
          such that primary key of one table is the foreign key for another table. if we update the primary key of the first
          table then using the ON UPDATE CASCADE foreign key of the second table automatically get updated.



3. DELETE
    1. DELETE FROM table-name WHERE id = 1;
    2. DELETE FROM table-name; //all rows will be deleted.
    3. DELETE CASCADE - (to overcome DELETE constraint of Referential constraints)
          1. What would happen to child entry if parent table’s entry is deleted?
          2. CREATE TABLE ORDER (
                order_id int PRIMARY KEY,
                delivery_date DATE,
                cust_id INT,
                FOREIGN KEY(cust_id) REFERENCES customer(id) ON DELETE CASCADE
            );


     4. ON DELETE NULL - (can FK have null values?)
        CREATE TABLE ORDER (
            order_id int PRIMARY KEY,
            delivery_date DATE,
            cust_id INT,
            FOREIGN KEY(cust_id) REFERENCES customer(id) ON DELETE SET NULL
        );




4. REPLACE
        1. Primarily used for already present tuple in a table.
        2. As UPDATE, using REPLACE with the help of WHERE clause in PK, then that row will be replaced.
        3. As INSERT, if there is no duplicate data new tuple will be inserted.
        4. REPLACE INTO student (id, class) VALUES(4, 3);
        5. REPLACE INTO table SET col1 = val1, col2 = val2;

```

