# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```




**Question 1**


Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table

```
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
```

```sql
UPDATE products
set reorder_lvl = reorder_lvl * 1.30
where category  = 'Food' and quantity < 50;
```

**Output:**

![image](https://github.com/user-attachments/assets/ff91c01f-1f71-4b93-846f-d48139f38233)



**Question 2**


Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'. sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)


```sql
update sales
set sell_price=sell_price*1.05
where product_id=15 and sale_date='2023-01-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/862f1130-aebc-4925-b4b4-14ed1a7eed07)



**Question 3**

Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

```
products table

---------------
product_id
product_name
category_id
availability
```


```sql
update products
set product_name = 'Grapefruit'
where product_id=4;
```

**Output:**

![image](https://github.com/user-attachments/assets/94d89807-0024-4137-b1b6-7ff80e32a9de)





**Question 4**

Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'. Sample table: Doctors attributes : doctor_id, first_name, last_name, specialization


```sql
delete from Doctors
where specialization = 'Pediatrics' and first_name = 'Michael';
```

**Output:**

![image](https://github.com/user-attachments/assets/220c983c-a8f3-40d4-b49b-b25caf66ddac)


**Question 5**

Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.


```
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSB
```

```
delete from customer
where GRADE = 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/7496fe5e-0759-454f-80f7-6a3d03281a2e)



**Question 6**
 
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1. Sample table: Doctors attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
where Doctor_id=1;
```

**Output:**

![image](https://github.com/user-attachments/assets/f5784005-bfcd-4e83-9af2-70b1b98d0e70)



**Question 7**

Write a SQL query to Delete All Doctors with a NULL Specialization Sample table: Doctors attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE specialization IS NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/18fd93ae-dff7-46aa-91f8-87d915193e04)



**Question 8**

Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

```

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```


```sql
select id,value1,
case
when value1<13 then 'Child'
when value1 between 13 and 19 then 'Teen' else 'Adult'
end as age_group
from Calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/16654538-64e4-4b15-8f8f-9253619b0e65)



**Question 9**

Write a SQL query to calculate the absolute value of the value1 column from the Calculations table.

```

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```

```sql
select id,value1,abs(value1) as absolute_value
from Calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/564d018e-d9e9-4f1d-ba25-588e062e074b)



**Question 10**

Write a SQL statement to Update the grade of all customers in Chennai city as 5. Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
update Customer
set grade = 5
where city = 'Chennai';
```

**Output:**
![image](https://github.com/user-attachments/assets/0c2cacaf-c5a8-4355-9cf3-76ad54bcaf8a)



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
