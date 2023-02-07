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

What is SQL injection?

    They are the most common web hacking techniques. An SQL injection attack consists of insertion or "Injection" of malicious code 
    via the SQL query input from the client to the application. 
    
Example of SQL injection: 

        "SELECT * FROM users WHERE name ='" + userName + "'";
        This is the SQL query to retrieve the user information from the database.
        
        The variable userName holds the input from the client and injects it into the query.
        If the input would be Smith the query then looks like:
        
        "SELECT * FROM users WHERE name = 'Smith'";
        And would retrieve all data from the user with the name Smith.
Examples of malicious actions used for having access to DB and retreiving information for all the users stored in the DB.

    - Smith' OR '1'='1 - used to provide all the entries from the users table
    - Smith' OR 1 = 1; -- used for the same reason
    - Smith' ; DROP TABLE users; TRUNCATE audit_log; -- chains multiple SQL commands and deletes the users table as well as entries from 
    the audit_log.
    
AUDIT_LOG

    Audit logging is the process of documenting activity within the software systems used across your organization. Audit logs record 
    the occurrence of an event, the time at which it occurred, the responsible user or service, and the impacted entity. All of the 
    devices in your network, your cloud services, and your applications emit logs that may be used for auditing purposes. A series of 
    audit logs is called an audit trail because it shows a sequential record of all the activity on a specific system. By reviewing 
    audit logs, systems administrators can track user activity, and security teams can investigate breaches and ensure compliance with 
    regulatory requirements. Audit logs capture the following types of information:

Event name as identified in the system
 - Easy-to-understand description of the event
 - Event timestamp
 - Actor or service that created, edited, or deleted the event (user ID or API ID)
 - Application, device, system, or object that was impacted (IP address, device ID, etc.)
 - Source from where the actor or service originated (country, host name, IP address, device ID, etc.)
 - Custom tags specified by the user, such as severity level of the event
 - While audit logs can take the form of a physical file, the term usually refers to digital records that you can store in a log management 
 platform.
    
CONSEQUENCES OF SQL INJECTION

    A SUCCESSFUL SQL INJECTION EXPLOIT CAN:
     - Read and modify sensitive data from the database
     - Execute administration operations on the database
         - Shutdown auditing or the DBMS
         - Truncate tables and logs
         - Add users
     - Recover the content of a given file present on the DBMS file system 
     - Issue commands to the operating system
     
     SQL INJECTION ATTACKS ALLOW ATTACKERS TO
     - Spoof identity
     - Tamper with existing data 
     - Cause repudiation issues such as voiding transactions or changing balances
     - Allow the complete disclosure of all data in the system
     - Destroy the data or make it otherwise unavailable
     - Become administrator of the database server.
     
 SEVERITY OF SQL INJECTION 
 
    THE SEVERITY OF SQL INJECTION ATTACKS IS LIMITED BY
    - Attacker's skill and imagination 
    - Defense in depth countermeasures
        - Input validation
        - Least priviledge
    - Database technology
    
    NOT ALL DATABASES SUPPORT COMMAND CHAINING
    - Microsoft Access
    - MySQL Connector/J and C
    - Oracle
    
    SQL injection is more common in PHP, Classic ASP, Cold Fusion and other languages
    - Languages that do not provide  parameterized query support
    - Parameterized queries have been added to newer versions
    - Early adopters of web technology (i.e Old Code)
    
    NOT All databases are equal (SQL server)
    - Comamand shell: master.dbo.xp_cmdshell 'cmd.exe dir c:'
    - Registry commands: xp_regread, xp_regdeletekey, ...
    
Special characters for SQL injection

    /* */ are inline comments
    -- , # are line comments
    
    Example: SELECT * FROM users WHERE name = 'admin' --AND pass = 'pass'

    ; allows query chaining
    Example: SELECT * FROM users; DROP TABLE users;
    
    ' , + , || allows string concatenation 
    Char()     strings without quotes
    Example: SELECT * FROM users WHERE name = '+ char(27) OR 1=1
    
    
