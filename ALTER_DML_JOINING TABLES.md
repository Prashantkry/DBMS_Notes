ALTER OPERATIONS

1. Changes schema
2. ADD
1. Add new column.
2. ALTER TABLE table_name ADD new_col_name datatype ADD new_col_name_2 datatype;
3. e.g., ALTER TABLE customer ADD age INT NOT NULL;
3. MODIFY
1. Change datatype of an attribute.
2. ALTER TABLE table-name MODIFY col-name col-datatype;
3. E.g., VARCHAR TO CHAR
ALTER TABLE customer MODIFY name CHAR(1024);
4. CHANGE COLUMN
1. Rename column name.
2. ALTER TABLE table-name CHANGE COLUMN old-col-name new-col-name new-col-datatype;
3. e.g., ALTER TABLE customer CHANGE COLUMN name customer-name VARCHAR(1024);
5. DROP COLUMN
1. Drop a column completely.
2. ALTER TABLE table-name DROP COLUMN col-name;
3. e.g., ALTER TABLE customer DROP COLUMN middle-name;
6. RENAME
1. Rename table name itself.
2. ALTER TABLE table-name RENAME TO new-table-name;
3. e.g., ALTER TABLE customer RENAME TO customer-details;
DATA MANIPULATION LANGUAGE (DML)
1. INSERT
1. INSERT INTO table-name(col1, col2, col3) VALUES (v1, v2, v3), (val1, val2, val3);
2. UPDATE
1. UPDATE table-name SET col1 = 1, col2 = ‘abc’ WHERE id = 1;
2. Update multiple rows e.g.,
1. UPDATE student SET standard = standard + 1;
3. ON UPDATE CASCADE
1. Can be added to the table while creating constraints. Suppose there is a situation where we have two tables
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
