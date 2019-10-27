# getting_started_sql
Guide to get started with SQL

1. Setup a user with privileges locally

   * Get sudo access to MYSQL server on your machine
     * **sudo mysql -u root**
   * Execute the following command:
     * **GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' IDENTIFIED BY 'password';**
   * Close the window and log on to the server with the new privileges as:
     * **mysql -u user -p password**

2. Creation of tables:
    * Following command creates a new table with name *new_table* and 3 columns each with data type specified next to it
    * Examples of data types are - INTEGER, TEXT, STRING, etc.
    * **CREATE TABLE new_table (col_1 dtype_1, col_2 dtype_2, col_3 dtype_3)**;

3. Adding new entries to the table created:
    * To add a new entry to *new_table*, we have the following generic command:
      * INSERT INTO new_table (col_1, col_2, col_3) VALUES (20,'MYNAME','@3');
      
4. Accessing data from your table:
    * SELECT statement allows one to extract information from each column
      * Extracting all the columns:
        * **SELECT * FROM new_table**;
      * Extracting information from specific column:
        * **SELECT col_1 FROM new_table**;
      * Setting aliases for columns in the result output:
        * **SELECT col_1 AS 'c1' FROM new_table**
      * Getting list of all the distinct values of a column:
        * **SELECT DISTINCT col_3 FROM new_table**
      * Selection based on a screening criteria:
        * **SELECT * FROM new_table WHERE col_1 < 15**
      * Selection based on similarity of values:
        * **SELECT * FROM new_table WHERE col_2 LIKE 'MYNA_E'**
        * **SELECT * FROM new_table WHERE col_2 LIKE 'M%'**
      * Dropping entries with a null field
        * **SELECT * FROM new_table WHERE col_2 IS NOT NULL**
      * Selection based on lexographic order or range of numbers:
        * **SELECT * FROM new_table WHERE col_1 BETWEEN 0 AND 1999**
        * **SELECT * FROM new_table WHERE col_3 BETWEEN 'A' AND 'M'** 
        * *BETWEEN 'A' AND 'M'* will include rows where col_3 == 'M' but not anything with trails after M
        * **SELECT * FROM new_table WHERE col_3 BETWEEN 'A' AND 'M' AND col_1 BETWEEN 0 AND 20**
        * **SELECT * FROM new_table WHERE col_3 BETWEEN 'A' AND 'M' OR col_1 BETWEEN 0 AND 20**
      * Sorting the outputs:
        * **SELECT * FROM new_table WHERE col_1 > 20 ORDER BY col_2 DESC;** 
        * Can replace DESC with ASC to get ascending order 
        * Works for both numerical and text data types
      * Limiting screen output 
        * **SELECT * FROM new_table LIMIT 5**
        * Limits the output to 5 results. 
        * Limit always goes at the very end of the query

5. Functions in SQL:
      * Get count based on your clause; returns total number of entries in a column
        * **SELECT COUNT(col_1) FROM new_table;**
      * Get sum of all the entries in a column using:
        * **SELECT SUM(col_2) FROM new_table;**
      * Get maximum / minimum of a column using the following functions:
        * **SELECT MAX(col_1) FROM new_table;**
        * **SELECT MIN(col_1) FROM new_table;**
      * Get average value of a column:
        * **SELECT AVG(col_1) FROM new_table;**
      * Round the results to decimal precision required. Example rounds the value to first decimal. 
        * **SELECT ROUND(col_1,1) FROM new_table;**
      * Grouping for aggregate values using - **GROUP BY**. It is used after *WHERE* statement & comes before *ORDER BY* and *LIMIT*
        * **SELECT col_1, AVG(col_2) FROM new_table GROUP BY col_3;**
      * Column references: Queried columns can be replaced by the order in which they occur in our syntax:
        * **SELECT col_1, col_3, avg(col_2) FROM new_table ORDER BY 2 == SELECT col_1, col_3, avg(col_2) FROM new_table ORDER BY col_3**
      * When we want to limit the results of a query based on values of the individual rows, use WHERE. When we want to limit the results of a query based on an aggregate property, use HAVING. An example with HAVING is shown below:
        * ** SELECT col_1, round(avg(col_2)), count(col_3) from fake_apps group by 1 having count(col_3) > 10;**
      * 
5. if-else loop equivalent for SQL:
    ``` 
    SELECT *, 
      case 
        when cat_3 = 'v1' then 'o1'
        when cat_3 = 'v2' then 'o2'
        else 'o3'
      end as 'Alias_for_field'
    from new_table 
      

6. Modifying exisiting table structurally:
    * ALTER TABLE clause lets you modify structure of the table
    * ADD COLUMN is another clause for addition of a new column
    * A case in example - addition of a new column
      * **ALTER TABLE new_table ADD COLUMN col_4 TEXT;**
      
7. Modifying existing entries / rows:
    * **UPDATE celebs SET col_4 = 'nikolaj' WHERE col_1 = 20**
    * Above statement updates col_4 attribute of the entry corresponding to col_1=20
    * In general, **UPDATE** clause is used to update a row and **SET** clause is used to update columns
    * To delete a row / entry, we have **DELETE FROM** clause. 
        * DELETE FROM celebs WHERE col_4 IS NULL
 
8. Constraining your columns:
    * Introducing a primary key which will be unique to each entry and be used as an identifier
    * UNIQUE clause allows us to impose the constraint that the values in that particular column are all unique; no repitition. 
    * An example is shown below:
        * **CREATE TABLE mtab (col_1 INTEGER PRIMARY KEY, col_2 TEXT NOT NULL, col_3 INTEGER NOT NULL, col_4 DEFAULT "GotG2")**
    * It creates a table with 4 columns; column 1 is the primary key, column 2 & 3's constraint won't allow us to insert any row with missing value for field col_2 or col_3, col_4 has a default value assigned for each new entry if not specified.
    
 
    
      
