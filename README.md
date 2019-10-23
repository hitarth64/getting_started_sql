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

5. Modifying exisiting table structurally:
    * ALTER TABLE clause lets you modify structure of the table
    * ADD COLUMN is another clause for addition of a new column
    * A case in example - addition of a new column
      * **ALTER TABLE new_table ADD COLUMN col_4 TEXT;**
      
6. Modifying existing entries / rows:
    * **UPDATE celebs SET col_4 = 'nikolaj' WHERE col_1 = 20**
    * Above statement updates col_4 attribute of the entry corresponding to col_1=20
    * In general, **UPDATE** clause is used to update a row and **SET** clause is used to update columns
    * To delete a row / entry, we have **DELETE FROM** clause. 
        * DELETE FROM celebs WHERE col_4 IS NULL
 
7. Constraining your columns:
    * Introducing a primary key which will be unique to each entry and be used as an identifier
    * UNIQUE clause allows us to impose the constraint that the values in that particular column are all unique; no repitition. 
    * An example is shown below:
        * **CREATE TABLE mtab (col_1 INTEGER PRIMARY KEY, col_2 TEXT NOT NULL, col_3 INTEGER NOT NULL, col_4 DEFAULT "GotG2")**
    * It creates a table with 4 columns; column 1 is the primary key, column 2 & 3's constraint won't allow us to insert any row with missing value for field col_2 or col_3, col_4 has a default value assigned for each new entry if not specified.
    
 
    
      
