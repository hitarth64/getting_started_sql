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
    * **CREATE TABLE new_table (col_1 dtype_1, col_2 dtype_2, col_3 dtype_3)**

3. Adding new entries to the table created:
    * To add a new entry to *new_table*, we have the following generic command:
      * INSERT INTO new_table (col_1, col_2, col_3) VALUES (20,'MYNAME','@3')
      
4. 
