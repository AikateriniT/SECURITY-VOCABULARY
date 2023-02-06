# SECURITY-VOCABULARY
This is useful vocabulary for security matters to help out during the Security Lab 

SQL

    It is a standardized programming language which is used for managing relational databases and performing various operations on 
    the data in them. As a database we name the collection of data which is organized into rows, columns, tables and it is indexed 
    to make it easier to find information. The three main protection goals in information security are confidentiality, integrity 
    and availability, are considered the three most crucial components of information security. 

DML
  
    Data Manipulation Language, deals with the manipulation of data and includes the most common SQL statements such as SELECT, 
    INSERT, UPDATE, DELETE etc,and it is used for requesting a result set of records from database tables (select), adding(insert), 
    deleting and modyfing (update) data in a database. By using DML type for an SQL injection the hacker will violate two of the 
    three CIA triad protection goals: confidentiality and integrity (update). (Only authorized people can read the data.)
    
DDL

    Data definition language, includes commands for defining data structures, especially database schemas which tell how the data 
    should reside in the database. By using the DDL for the SQL injection the user violates the integrity (alter) and the availability 
    (drop) (Only authorized users can manipulate data such as deleting/changing.) 
    
DCL

    Data control language, is used to create priviledges to allow users to access and manipulate a database. By SQL injection 
    which uses DCL type, the perpetrator violates the confidentiality (grant) and the availability (revoke)(Unwanted people could 
    grand themselves admin priviledges or revoke the admin rights from an administrator.)
