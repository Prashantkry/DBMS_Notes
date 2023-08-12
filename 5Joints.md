Joints
JOINING TABLES
1. All RDBMS are relational in nature, we refer to other tables to get meaningful outcomes.


2. FK are used to do reference to other table.


3. INNER JOIN
    1. Returns a resultant table that has matching values from both the tables or all the tables.
    2. SELECT column-list FROM table1 INNER JOIN table2 ON condition1
        INNER JOIN table3 ON condition2
          …;
    3. Alias in MySQL (AS)
        1. Aliases in MySQL is used to give a temporary name to a table or a column in a table for the purpose of
            a particular query. It works as a nickname for expressing the tables or column names.
             It makes the query short and neat.
        3. SELECT col_name AS alias_name FROM table_name;
        4. SELECT col_name1, col_name2,... FROM table_name AS alias_name;

  

4. OUTER JOIN
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



5. CROSS JOIN
        1. This returns all the cartesian products of the data present in both tables. Hence, all possible variations
        are reflected in the output.
        2. Used rarely in practical purpose.
        3. Table-1 has 10 rows and table-2 has 5, then resultant would have 50 rows.
        4. SELECT column-lists FROM table1 CROSS JOIN table2;



6. SELF JOIN
        1. It is used to get the output from a particular table when the same table is joined to itself.
        2. Used very less.
        3. Emulated using INNER JOIN.
        4. SELECT columns FROM table as t1 INNER JOIN table as t2 ON t1.id = t2.id;



7. Join without using join keywords.
        1. SELECT * FROM table1, table2 WHERE condition;
        2. e.g., SELECT artist_name, album_name, year_recordedFROM artist, albumWHERE artist.id = album.artist_id;

   SET OPERATIONS
        1. Used to combine multiple select statements.
        2. Always gives distinct rows.