# Mysql

### MySQL Syntax 


# DDL command- Data definition language 
## CREATE ,USE and DROP functions


---
Create DATABASE database_name;

USE database_name; 

DROP DATABASE database_name; (Deletes database) 

USE Sales; ( To select database - In this case the sales database will be selected)

 
---
PLEASE NOTE : The below syntax only creates a structure of the table doesn’t add the values inside

CREATE TABLE table_name(
                     column_name 1 datatype constraints ,
                     column_name 2 datatype constraints,
                     column_name 3 datatype constraints
);


## INSERT VALUES TO A TABLE 


## Approach 1

INSERT INTO Table_name VALUES( value1, value2, value3,…)

## Approach 2 

INSERT INTO Table_name (column1, column2)
                       Values (value1, value 2, value3) , (Value 4, value 5 , value 6)


## Example 

INSERT INTO customers (customer_id, customer_name, city, age)
VALUES (5, “John”, “London”, 44)

---
## Practice 1 

* Create an Employee table 
       Employee id, employee name, department, salary, date of joining

---

## Solution


CREATE TABLE Employee(
                              Employee_Id INT PRIMARY KEY,
                              Employee_name VARCHAR(50) NOT NULL,
                              Department VARCHAR(50),
                              Date_of_joining  DATE NOT NULL
);

INSERT INTO Employee VALUES (1, ‘John’, ‘IT’ ,’2025-01-01’);


## Data Types


INT	 --Integer values(Ids,counts)	 -- INT

BIGINT --	Large integer Values -- 	BIGINT

VARCHAR --	Variable-length string	 -- VARCHAR(255)

CHAR --	Fixed-length String	CHAR (10)

TEXT	 ---Long text data	TEXT

DECIMAL	 ---Exact decimal values(money)	DECIMAL(10,2)

FLOAT	--Approx decimal values	FLOAT 

BOOLEAN	---True/False (0 or 1) --	BOOLEAN

DATE	---Date in YYYY-MM-DD format	---DATE

DATETIME	--Date & Time---	DATETIME

TIMESTAMP	---Auto date-time tracking(hr min &single)--	TIMESTAMP

ENUM---	Single value from list(preselected values )---ENUM(‘Active’,’Inactive’)

BLOB---	Binary data (files/images) rarely used--	BLOB 

---

# How to check datatypes within a table 

DESCRIBE TABLE_NAME ( helps to check the data type)

# Example: 
Describe customers

generates the data types , null values, key  etc as an output

---
# CONSTRAINTS 
 - are restrictions or rules on data 

# Example : 
Name - cannot be empty

Roll number  - must be unique

Age - must be positive

SYNTAX 

CREATE TABLE table_name

(Column_name1  datatype constraints) 


Without constraints 
- Duplicate Ids
- Empty names
- Wrong values 
- messy data 

With constraints 
 - Clean data 
 - Accurate data
 - No duplicates 
 - More reliable database 
---

# Types of constraints 

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


## DIFFERENT TYPES OF SQL COMMANDS 
<img width="1353" height="547" alt="image" src="https://github.com/user-attachments/assets/945283cc-1e14-4cb0-ae7e-8a2221ea720a" />

---


## 1. CREATE (can be used for both database & table)

CREATE DATABASE database_name; 
CREATE TABLE table_name( column1 datatype constraints)

---
## Example 

Create database hospital; 

USE hospital
Create table patients(patient_id INT Primary key,
                                     patient_name VARCHAR(50) NOT NULL, 
                                     Age INT NOT NULL); 

---

## Practice 2 

Create a table for Doctors under the database hospital with columns of the following Doctor id, name, department, specialist, age defining the constraints 



## Solution 2 
TBC 


## 2. ALTER  - Modifies structure of a table ( only used for tables and can't be used for databases) 
  
ALTER TABLE table_name  ADD column_name datatype; 
ALTER TABLE table_name DROP COLUMN  column_name;


## Example :

ALTER TABLE patients ADD address VARCHAR(50);

ALTER TABLE patients DROP COLUMN address; 

ALTER TABLE patients ADD age INT;

ALTER TABLE patients ADD email VARCHAR(50); 


---

## 3. DROP ( both for table and database ) it completely deletes a given database or table

Syntax 

DROP TABLE table _name; 
DROP DATABASE database_name;

## Examples: 

DROP TABLE patients ;

DROP DATABASE Employee ; 


## 4. TRUNCATE
( only works on table) ( This function only deletes the records of rows doesn’t delete the structure like the DROP functions) the structure of the table will stay the same including column names 

Syntax : 

TRUNCATE  TABLE Table_name;

Example: TRUNCATE TABLE patients 

## 5. RENAME ( renames the object ) ( can be used to rename tables)

Syntax : 

RENAME TABLE old_name TO new_name; 

## Example: 

RENAME TABLE patients TO patients_info;

---

# DATA QUERY LANGUAGE (DQL)









