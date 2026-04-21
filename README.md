

# SQL -Standard Query Language


# DDL command- Data definition language 
## CREATE ,USE and DROP functions


---

#### Syntax 

Create DATABASE database_name;

USE database_name; 

DROP DATABASE database_name; (Deletes database) 

#### Example :

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

* Create an Employee table with the following columns:  
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

# How to check data types within a table 
#### Syntax 

DESCRIBE TABLE_NAME ( helps to check the data type)

#### Example: 
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

#### Example :

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

SELECT , FROM 

SELECT  - It is a command 

FROM - It is a clause(helpers) not command . 

DQL - has only one command, SELECT , Other terms like FROM, WHERE, GROUP BY, HAVING, ORDER BY, DISTINCT and LIMIT are clauses of SELECT, 
not separate commands.


SYNTAX 
SELECT Column_Name FROM Table_Name   

SELECT *  From Table_Name ( brings up all the data which can impact the performance)

SELECT * From Table_Name LIMIT 10   ( this only brings up 10 rows but all columns will appear)

 # Example: 

SELECT * From Sales_data 
SELECT order_id, customer_name, segement, Profit From sales_data 


# WHERE 
filters each and every rows for a conditions. 
It gives only those records that match the condition 

Syntax 

SELECT column_names
FROM Table_name
WHERE condition; 


### Example

1. SELECT *
    FROM customers 
    WHERE city = 'Delhi';

2. SELECT *
   From sales_data
   WHERE region = 'east';

3. SELECT *
   FROM Sales_data 
WHERE quantity = 5;


# Operators

Comparsion Operators 
= (equal) - matches exact value 
#### Syntax 
WHERE column = value

!= (Not Equal) - not equal to 
or <> (Not Equal) 

#### Example  - To get all regions data except Central 

SELECT * FROM 'Sales_data.csv' 
WHERE region <> 'Central';

>(Greater than) ; Works only on Numeric Field

#### Example 
SELECT * FROM 'Sales_data.csv' 
WHERE sales > 1000;

#### Please note : = and != or <> can work on both numeric fields and dimension fields

<(less than) - works with numeric field 
>= ( greater than equal to ) -works with numeric field 
<= (greater than equal to ) - works with numeric field

Logical Operators 

AND : both conditions must be true for output to be true

SYNTAX : 

WHERE condition1 AND condition2


OR: Anyone condition needs be true for output to be true 

SYNTAX: 

WHERE condition1 or condition2
 

NOT: Reverses the condition

SYNTAX: 
 
WHERE NOT condition 




EXAMPLE: 

AND 

SELECT * FROM Sales_data
WHERE segment =‘Corporate’ AND state = ‘Texas ‘


OR

SELECT *  FROM sales_data
WHERE quality >=4  OR sales >1500 OR profit > 500 

( If any of the conditions are true , the record will be pulled)

SELECT * FROM sales_data 
WHERE (Quantity >=4 AND sales > 1500) OR profit >500 

( In this case all profit > 500 will be executed because of the or operator , for the other conditions connected with AND both conditions need to be satisfied )


SELECT * FROM sales_data 
WHERE (Quantity >=4 OR sales > 1500) AND (profit >500 OR discount = 1)


NOT


SELECT * FROM sales_data

WHERE NOT region = ‘South’

( it will bring record where region is not south)



SELECT * FROM sales_data

WHERE NOT quantity >=4 AND NOT sales > 1500

Or can be written as if we don’t want to write NOT twice 

SELECT * FROM sales_data
WHERE NOT (quantity >=4 AND sales > 1500)



Range Operators 

BETWEEN : value inside a range(inclusive) 

SYNTAX: 
WHERE column BETWEEN value1 AND value2 


Example: 

SELECT * FROM sales_data 
WHERE sales BETWEEN 1000 AND 1500 

( this will display all records sales >=1000 and <= 1500 ) 


List Operators


 IN:  this is advance or operator 
Match any value from list 

IN works like multiple OR conditions, but it’s cleaner and more readable

SYNTAX: 

WHERE column IN (value1, value2, value3) 

Examples: 

SELECT * FROM sales_data 
WHERE city IN(‘Delhi’, ‘Mumbai’,’Prune’)

SELECT * FROM sales_data 
WHERE region IN(‘East’, ‘Central’)

SELECT * FROM sales_data 
WHERE region IN (‘East’, ‘Central’) AND sub_category IN (‘Phones’ , ‘Art’)



Pattern Operators

Only works with string, text fields

LIKE: Pattern matching  - Also called as Wildcard operator 


Examples 

WHERE name LIKE ‘A%’ - starts with A 
WHERE name LIKE ‘%n’ -  ends with n
WHERE name LIKE ‘%mit%’ - contains text ‘mit’
WHERE name LIKE ‘____’ - Exactly have 4 letters(any letters)
WHERE name NOT LIKE ‘A%’ - does not start with A 


PLEASE NOTE:  symbols used are %( any number of characters , _( for a single character)



SELECT * FROM Sales_data
WHERE customer_name LIKE ‘A%’

SELECT * FROM Sales_data
WHERE customer_name LIKE ‘%S’

#### PLEASE NOTE: 
That it is not case sensitive the character can be lower case or upper case on the code

SELECT * FROM sales_data 
WHERE customer_name LIKE ‘%aa%’

(It is not necessary that it will have a character at the beginning or at the end as long as aa is present )


SELECT * FROM sales_data 
WHERE customer_name LIKE ‘%oo’) 

( here name must end with oo)


SELECT * FROM sales_data 
WHERE customer_name LIKE ‘________________’


#### Output : 

Benjamin Venier 
#### PLEASE NOTE: space is also considered , in the above code customer name with 15 characters will be displaced as the number _ is 15 

SELECT * FROM  sales_data
WHERE customer_name LIKE ‘A____________’

(Brings up all the customers starting with A)

SELECT * FROM  sales_data
WHERE customer_name LIKE ‘__n____________’


(here 3rd letter must be n before n there should be two characters and after n there should be 12 characters)

SELECT * FROM  sales_data

#### NULL Operators

IS NULL and IS NOT NULL 
Checks empty values 

#### SYNTAX:
WHERE column IS NULL

#### EXAMPLE : 

SELECT * FROM sales _data
WHERE Segment IS NULL

( will display all null values ) 



SELECT *. FROM sales_data
WHERE  order_id IS NOT NULL 

( can be used for data cleaning, show me records without null)


#### Arithmetic Operators

Performs mathematical operations like addition , substraction,multoplication
Division, remainder on numeric values or columns 

PLEASE NOTE that this only works for numeric values not dimensional fields or values 

#### Examples : 

SELECT * FROM sales_data
WHERE sales +100 > 1000 

OFFSET

Select *
From table_name
Limit x OFFset y; 
 Or 

Select *
From table_name;
Limit Y,X 



X - Number of rows to return
Y- Number of rows to skip 


Example 

Select * From sales_data 
Order by Profit desc
Limit 10 OFFSET 3 

(This skips the first 3 records)


Or 


Select * From sales_data
Order by Profit desc
Limit 3, 10 

(This skips the first 3 records)


Question : print only the second max profit

Select *  From Sales_data
Order by profit Desc
Limit 1 offset 1



Question : print only the third max profit


Select *  From Sales_data
Order by profit Desc
Limit 1 offset 2

Or

Select *  From Sales_data
Order by profit Desc
Limit 2,1


Question : print only the fifth max profit

Select *  From Sales_data
Order by profit Desc
Limit 4,1


GROUP BY AND HAVING 

Group by - combines rows that have the same value into a single group 

Use group by when you need aggregation (sum, count, avg, max, min)

Syntax 

Select column_name, aggregate_function(column)
From table_name
Group by column_name;


Multiple columns 

Syntax 

Selection col1, col2 , aggregate_function(column)
From table_name
Group by col1 , col2 


￼

Example

Select category, sub_category, sum(sales) as total sales
From sales_data
Group by category, sub_category
Order by category
Limit 1

Or 

Select category, sub_category, sum(sales) as total sales
From sales_data
Group by 1,2
Order by 3 dec
Limit 1

( we can use number to represent column 1 , 2 and 3 from the first line of code)


HAVING 

- Filters grouped results after aggregation
- Sql having clause


Select category, sub_category, sum(sales) as Total_Sales
From sales_data
Group by 1,2 
Having sum(sales) > 150000


Where clause would only work for raw by raw occasions but not for aggregate 


Example: 

Where should be written before group by 

Select Category, sub_category, sum(sales) as Total_Sales
From sales_data
Where category =‘Furniture’
Group by 1,2
Having sum(sales) > 100000
Order by sum(sales) Desc
Limit 1 offset 1 


￼

￼


￼
Please note: Count(1) is the same as count(*)

Example count(region) - this will not count NULL values


* SELECT region, count(region) FROM 'Sales_data.csv'
group by region

The above code will show each sell from region would be counted


Average

Avg()

= sum() / count()


￼
Max

Max() 

Example: Select Max(sales) from sales_data 



Min 
Min()

￼


Foreign key
￼


INNER JOIN

￼
￼
NULL  won’t be joined  - as null is not a value 
Any time of join 

The name of the column table 1 and table the name might not be the same but til have the same record




￼


INNER JOIN and JOIN 
 The Default: INNER is the default join type in SQL. Per the ANSI SQL 92 specification, if you specify a join but do not specify a type, INNER is implicit.
* Readability: Many developers prefer using the explicit INNER JOIN keyword because it makes the query's intent clearer, especially when the query also includes other join types like LEFT or RIGHT.


Left Join /left outer join

￼
￼



￼

￼

RIGHT JOIN/ right outer join 

￼
￼



FULL OUTER JOIN

￼


￼


Please note: in inner join/outer the position of the tables in the code doesn’t matter . I will only have an impact for left or right join



Subquery / nested query 

Inner query runs first 
Outer query uses its result

Select column
From table 
Where column OPERATOR
            (Select column From table 
                        Where condition); 

Example : 

— subquery 
 - - 1. Orders with sales above average 
   
Select * 
From sales_data
Where sales > (
       Select Avg(sales) from sales_data  )

  - - 2. Highest sales orders 
Select * 
From sales_data 
Where sales = (select max(sales) from sales_data)


- - 3 lowest profit
 Select * 
From sales_data
Where profit = (
            Select  min(profit) from sales_data) 

- - 4 . Orders with minimum discount
 
Select * 
From sales_data
Where discount = 
          (select min(discount) from sales_data) 

- - 5 Orders from states that belong to west region 

Select * 
From sales_data 
WHERE states IN ( SELECT * from sales_ data WHERE region =‘west’); 

 =  - would only match with one single value 

 IN  - would match with multiple values 

Key Differences
* Single vs. Multiple:
    * =: Used for exact matches against one value (e.g., WHERE ID = 5).
    * IN: Used to check if a value exists within a specific set (e.g., WHERE ID IN (5, 6, 7)).
* Readability:
    * Using IN is much cleaner than chaining multiple OR statements. For instance, WHERE City IN ('London', 'Paris') is preferred over WHERE City = 'London' OR City = 'Paris'.
* Subqueries:
    * =: Can only be used with a subquery if that subquery returns exactly one row and one column.
    * IN: Can be used with subqueries that return multiple rows, checking if the outer value matches any result from the subquery.

 - - 6 sales greater than ALL sales in South 

Select * 
From sales_data 
Where sales > ALL( 
               Select sales from sales_data 
              Where region =‘South’);




ALL - is an opposite of IN - 
All will work as  multiple AND condition ( Everything must be satisfied) 
IN - works as multiple condition like OR 


OR 

Select * 
From sales_data 
Where sales >( 
               Select max(sales) from  sales_data 
              Where region =‘South’);

* Use IN when filtering rows based on a specific list or static set of values.
* Use ANY to match rows against at least one value in a subquery result.
* Use ALL when comparisons need to hold true for all values in a list or subquery.



Correlated Subquery

- Executes once for each row of the outer query 
- Subquery uses values from the outer query 
- Ideal for ranking, row -specific calculations and conditional logic

Syntax
Select * 
From table1 t1
Where column OPERATOR(
              SELECT aggregate
              FROM table2 t2
              WHERE t1.col = t2.col
         ); 

Example :

- - Find the highest sales order in each state

Select * 
From sales_data s1
Where sales = (
      Select MAX (sales) 
From sales_data s2 
Where s1.state = s2.state

Drawbacks of correlated subquery

- Slow performance
- 
￼

Window Functions

Row level calculations - normal SELECT & WHERE clause

Group level calulations
Group by 


Window functions are needs for ROW +Group calculation together

Example: running total, ranking, previous row comparison, moving average, ToP N per category 

** Group by reduces row
** Window functions keep rows 

A window function performs a calculation across a set of related rows while still keeping every row in the result ( it groups but brings up all /every row) 


Syntax

SELECT 
     Column, 	
    Window_function_name() OVER(
     PARTITION BY column 
    ORDER BY column
 ) 
FROM table ; 

PLEASE NOTE: Without OVER() it becomes normal aggregate 
With OVER () becomes window function


 



















