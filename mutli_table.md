# Handing Mutliple tables
Part 2 of getting started with SQL

1. Combine tables in SQL:
      * Get count based on your clause; returns total number of entries in a column
        * **SELECT COUNT(col_1) FROM new_table;**
      * Join two tables (t1 and t2) by a column - c1:
        * **SELECT * FROM t1 JOIN t2 ON t1.c1 = t2.c1;**
      * A normal join like above will drop the unmatched row if there is no matching.
      * An alternative is left join which keeps all the rows of table 1 but drops unmatched rows from table 2:
        * **SELECT * FROM t1 LEFT JOIN t2 ON t1.c1 = t2.c1;**
      * Combine rows from one table with other without any matching:
        * **SELECT t1.c1, t2.c2 FROM t1 CROSS JOIN t2;**
      * Stacking two tables - condition is the number of columns and their datatypes must be exactly same:
        * **SELECT * FROM t1 UNION SELECT * FROM t2**
      * Nesting queries using WITH clause:
        * **WITH previous_query AS (SELECT * FROM t2 ) SELECT * FROM previous_query JOIN t1 ON t1.c1 = t2.c2;**
 
      
