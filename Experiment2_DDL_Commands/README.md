# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```






**Question 1**

```
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values
```



```sql
insert into
Employee(EmployeeID,Name,Position)
values(4,'Emily White','Analyst');
```

**Output:**

![image](https://github.com/user-attachments/assets/211ecd87-ea2c-4819-bf93-9aaa122d92c8)




**Question 2**

Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

```sql
ALTER TABLE employee
ADD COLUMN first_name varchar(50);

ALTER TABLE employee
ADD COLUMN last_name varchar(50);

```

**Output:**

![image](https://github.com/user-attachments/assets/bfbe3550-a583-47a7-bee1-0277fea9d822)




**Question 3**

Create a new table named products with the following specifications: product_id as INTEGER and primary key. product_name as TEXT and not NULL. list_price as DECIMAL (10, 2) and not NULL. discount as DECIMAL (10, 2) with a default value of 0 and not NULL. A CHECK constraint at the table level to ensure: list_price is greater than or equal to discount discount is greater than or equal to 0 list_price is greater than or equal to 0


```sql
create table products(
product_id INTEGER primary key,
product_name TEXT not null,
list_price DECIMAL(10,2) not null
check(list_price>=discount and
list_price>=0),
discount DECIMAL(10,2) default 0 not 
null check(discount>=0));
```

**Output:**

![image](https://github.com/user-attachments/assets/df2c3405-b166-4ba4-9b34-38a707f6608e)





**Question 4**

Insert all books from Out_of_print_books into Books Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT into Books
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM  Out_of_print_books;
```

**Output:**

![image](https://github.com/user-attachments/assets/3fa8a098-8acf-4d5a-9814-5f410e11ec9b)






**Question 5**

Create a table named Tasks with the following columns:

TaskID as INTEGER TaskName as TEXT DueDate as DATE


```sql
create table Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/bd9464e2-a491-4aff-9bee-5381ac44ec3f)




**Question 6**

Create a table named Bonuses with the following constraints: BonusID as INTEGER should be the primary key. EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID). BonusAmount as REAL should be greater than 0. BonusDate as DATE. Reason as TEXT should not be NULL.

```sql
create table Bonuses(
BonusID INTEGER primary key,
EmployeeID INTEGER,
BonusAmount REAL check(BonusAmount>0),
BonusDate DATE,
Reason TEXT not null,
foreign key(EmployeeID) references Employees(EmployeeID));
```

**Output:**

![image](https://github.com/user-attachments/assets/54d7d9df-6377-470a-a317-04df3a1ba4a2)


**Question 7**

Create a table named Invoices with the following constraints: InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. Amount as REAL should be greater than 0. DueDate as DATE should be greater than the InvoiceDate. OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
Amount REAL check(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER,
foreign key (OrderID) references Orders(OrderID));
```

**Output:**

![image](https://github.com/user-attachments/assets/a3357d44-fa7c-4249-945a-ffd9265aa3d5)


**Question 8**

Create a table named Members with the following columns:

MemberID as INTEGER MemberName as TEXT JoinDate as DATE


```sql
create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE

);
```

**Output:**

![image](https://github.com/user-attachments/assets/35fa7af7-c12d-410c-9000-b2b8cc284773)

**Question 9**

```
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```


```sql
alter table customer
add column birth_date timestamp;
```

**Output:**

![image](https://github.com/user-attachments/assets/84fadd2f-96cc-4c4c-a670-77eb008fed58)




**Question 10**

```
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.
```


```sql
insert into Student_details(RollNo,Name,Gender)
values(204,"Samuel Black","M");
```

**Output:**

![image](https://github.com/user-attachments/assets/40c27e5c-22c1-44d8-babb-b037a0d53815)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
