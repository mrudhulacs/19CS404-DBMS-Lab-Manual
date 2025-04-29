# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

Write a SQL query to find the average salary of all employees?
```

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```

```sql
SELECT AVG(income) AS Average_Salary
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/e29f5f31-8e62-446c-81dc-c975e2c64399)



**Question 2**

Write a SQL query to calculate the total number of working hours of all employees

![image](https://github.com/user-attachments/assets/ee701637-fc60-4ac0-8d31-a931909cef8c)

```sql
SELECT SUM(workhour) AS 'Total working hours'
FROM  employee1;
```

**Output:**

![image](https://github.com/user-attachments/assets/f983626c-9a25-45d1-aa1a-e95d4bd905bb)



**Question 3**

Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer
```

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002
```

```sql
SELECT COUNT(customer_id) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/90c63189-508b-4c9f-98f0-bd9a37133101)



**Question 4**

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10. Sample table: employee1

```sql
SELECT jdate,MIN(workhour) AS  'MIN(workhour)'
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/f7076c21-6821-4b85-8253-65f6aa23827b)




**Question 5**

Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

Sample table: employee

![image](https://github.com/user-attachments/assets/e3ef698a-7763-4945-9947-b2451e1a0db8)


```sql
SELECT age, MAX(income) AS 'MAX(income)'
FROM employee
GROUP BY age
HAVING MAX(income) > 2000000;
```

**Output:**

![image](https://github.com/user-attachments/assets/fabbcbe8-45e6-4c6e-bbee-79257ffeb89b)


**Question 6**

Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than Sample table: products.
![image](https://github.com/user-attachments/assets/80bc611f-6d6b-4c15-ad0f-1d77f774dcbf)


```sql
SELECT category_id, COUNT(*) AS COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/fa7342ca-0218-4451-8b20-c568c45a1dcb)


**Question 7**

Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table
![image](https://github.com/user-attachments/assets/53228280-d53d-4eca-9d39-6c19b46be4c5)

```sql
SELECT PatientID,COUNT(medications) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/65793ad9-5060-469c-bb11-862cfaa4024d)


**Question 8**

How many prescriptions were written in each frequency category (e.g., once daily, twice daily)? Sample tablePrescriptions Table

![image](https://github.com/user-attachments/assets/a8a3befe-5012-4a52-9b0c-b057bad7609d)

```sql
SELECT Frequency,COUNT(Frequency) AS  TotalPrescriptions
FROM Prescriptions 
GROUP BY Frequency;
```

**Output:**

![image](https://github.com/user-attachments/assets/fefbee5c-9e10-4a72-82d3-bee366c6a446)


**Question 9**

What is the total number of appointments scheduled by each doctor?
Sample table:Appointments Table
![image](https://github.com/user-attachments/assets/d572f778-dc87-4759-9542-fbee0e289762)

```sql
SELECT DoctorID,COUNT(*) AS TotalAppointments
FROM Appointments 
GROUP BY DoctorID;
```

**Output:**

![image](https://github.com/user-attachments/assets/b61bf1ba-ead4-4dc5-bf38-d7a9db3113a4)


**Question 10**

Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida. Sample table: customer
![image](https://github.com/user-attachments/assets/120481cd-444b-450e-b834-56a76a768d9a)


```sql
select count(city)as COUNT
from customer
where city='Noida';
```

**Output:**
![image](https://github.com/user-attachments/assets/34daca4d-2068-4317-9961-d0c7958f404e)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
