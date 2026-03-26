# Mysql-Syntax-with-examples-and-practice-questions

### MySQL Syntax 


# DDL command- Data definition language 
## CREATE ,USE and DROP functions 
Create DATABASE database_name;
USE database_name; 
DROP DATABASE database_name; ( To delete it) 
USE Sales; ( the sales database will be selected)
 

The above syntax only creates a structure of the table doesn’t add the values inside
CREATE TABLE table_name(
                     column_name 1 datatype constraints ,
                     column_name 2 datatype constraints,
                     column_name 3 datatype constraints

. 
. 
);

Constraints tells whether it should have null value, unique value on each row , binary or truer false value

Datatype = varchar,int
 Varchar(50) can take 50 characters inside

Constraints - Primary key , not null 

If we don’t add constraints the column contain any value like blank 

Example  ID INT PRIMARY KEY

Approach 1

INSERT INTO Table_name VALUES( value1, value2, value3,…)

Approach 2 
INSERT INTO Table_name (column1, column2)
                       Values (value1, value 2, value3) , (Value 4, value 5 , value 6)


Example 

INSERT INTO customers (customer_id, customer_name, city, age)
VALUES (5, “John”, “London”, 44)

Assignment 1 

* Create an Employee table 
       Employee id, employee name, department, salary, date of joining



Solution

CREATE TABLE Employee(
                              Employee_Id INT PRIMARY KEY,
                              Employee_name VARCHAR(50) NOT NULL,
                              Department VARCHAR(50),
                              Date_of_joining  DATE NOT NULL
);

INSERT INTO Employee VALUES (1, ‘John’, ‘IT’ ,’2025-01-01’);


CREATE TABLE Employee(
                              Employee_Id INT PRIMARY KEY,
                              Employee_name VARCHAR(50) NOT NULL,
                              Department VARCHAR(50),
                              Date_of_joining  DATE NOT NULL
);

INSERT INTO Employee VALUES (1, ‘John’, ‘IT’ ,’2025-01-01’);


## Data Types

DATATYPE	  Description	                USAGE
INT	 --Integer values(Ids,counts)	 -- INT
BIGINT --	Large integer Values -- 	BIGINT
VARCHAR --	Variable-length string	 -- VARCHAR(255)
CHAR	Fixed-length String	CHAR (10)
TEXT	Long text data	TEXT
DECIMAL	Exact decimal values(money)	DECIMAL(10,2)
FLOAT	Approx decimal values	FLOAT 
BOOLEAN	True/False (0 or 1)	BOOLEAN
DATE	Date in YYYY-MM-DD format	DATE
DATETIME	Date & Time	DATETIME
TIMESTAMP	Auto date-time tracking(hr min &single)	TIMESTAMP
ENUM	Single value from list(preselected values )	ENUM(‘Active’,’Inactive’)
BLOB	Binary data (files/images) rarely used	BLOB 


DESCRIBE TABLE_NAME ( helps to check the data type)

Example: 
Describe customers

Give you of the data types , null values, key  etc


CONSTRAINTS 

Restrictions or rules on data 

Example : Name - cannot be empty
Roll number  - must be unique
Age - must be positive


CREATE TABLE table_name
(Column_name1  datatype constraints) 


Without constraints 
- Duplicate IDs
- Empty names
- Wrong values 
- Dirty data 

With constraints 
 - Clean data 
 - Accurate data
 - No duplicates 
 - More reliable database 


Types of constraints 

  1 . NOT NULL  - column cannot be empty 
       Example : name VARCHAR(50) NOT NULL 

2. UNIQUE - No duplicate values allowed.  Is not same as Primary key because it can take null value
      Example : email VARCHAR(100) UNIQUE 
  
  3. PRIMARY KEY(PK): UNIQUE. + NOT NULL together 
 
     Example: customer_id INT PRIMARY KEY 

  4.  DEFAULT : Sets default value automatically 
        
       Example: city VARCHAR(50) DEFAULT(‘Delhi’)

  5. CHECK : allow only valid values in a column
      
       Example: Age INT CHECK (age>=18)

 6.  FOREIGN KEY(FK): A foreign key a link to another table 

     

SYNTAX 
       
 CREATE TABLE table_name
(column_name1 datatype constraints)


CREATE TABLE customer_information(

Customer_ID INT PRIMARY KEY,


CREATE TABLE employee_information(
     Employee_id INT Primary key,
     Employee_Name VARCHAR(50) NOT NULL,
     Email  VARCHAR(100) UNIQUE,
     age INT CHECK(age>=18),
     City VARCHAR(50) DEFAULT 'London'
);

Select * 
From employee_information;

INSERT INTO employee_information VALUES (1, 'Rachel','Rachel123@gmail.com','36','London');
INSERT INTO employee_information VALUES (2, 'John','Rachel1234@gmail.com','20');

INSERT INTO employee_information (employee_id,employee_name,email,age)
VALUES(5, 'John','john1@hotmail.co.uk', 20)


**SQL COMMANDS 
<img width="1353" height="547" alt="image" src="https://github.com/user-attachments/assets/945283cc-1e14-4cb0-ae7e-8a2221ea720a" />





