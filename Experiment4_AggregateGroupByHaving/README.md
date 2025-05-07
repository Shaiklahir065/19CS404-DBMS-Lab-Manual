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
--
-- How many prescriptions were written for each medication?

Sample tablePrescriptions Table



For example:

Result
Medication     TotalPrescriptions
-------------  ------------------
Ciprofloxacin  1
Doxorubicin    1
Ibuprofen      1
Levothyroxine  1
Lisinopril     1
MMR            1
Pending        1
Prenatal vita  1
Sertraline     1
Topiramate     1

```sql
-- SELECT Medication,COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/1e99dc23-d1e9-4e3e-9f77-f3903c8e03f7)


**Question 2**
---
--How many appointments are scheduled for each patient?

Sample table: Appointments Table

name                  type
--------------------  ----------
AppointmentID         INTEGER
PatientID             INTEGER
DoctorID              INTEGER
AppointmentDateTime   DATETIME
Purpose               TEXT
Status                TEXT
For example:

Result
PatientID   TotalAppointments
----------  -----------------
3           3
5           2
6           1
7           1
10          3

```sql
-- SELECT PatientID, COUNT(AppointmentID) AS TotalAppointments
FROM Appointments
GROUP BY PatientID
ORDER BY PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/51f84df6-2f3a-4e47-af9d-4d6a410c7307)


**Question 3**
---
-- What is the total number of appointments scheduled for each day?

Table: Appointments

name                 type
-------------------  ----------
AppointmentID        INTEGER
PatientID            INTEGER
DoctorID             INTEGER
AppointmentDateTime  DATETIME
Purpose              TEXT
Status               TEXT
 

For example:

Result
AppointmentDate  TotalAppointments
---------------  -----------------
2024-02-16       4
2024-02-18       1
2024-02-20       1
2024-02-21       1
2024-02-22       1
2024-02-23       2
```sql
-- SELECT DATE(AppointmentDateTime) AS AppointmentDate, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY DATE(AppointmentDateTime);
```

**Output:**

![image](https://github.com/user-attachments/assets/b097a3f0-88a7-436f-94f0-e226787a81ce)

**Question 4**
---
-- Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
employees_count
---------------
8


```sql
-- SELECT COUNT(*) AS employees_count
FROM employee
WHERE income>50000;
```

**Output:**

![image](https://github.com/user-attachments/assets/0a1c7db7-8708-41c7-bd70-57affb6b69da)


**Question 5**
---
--Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18


```sql
-- SELECT SUM(purch_amt) AS TOTAL
FROM orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/9349a8f0-772d-471c-a826-3afe2f6bdec8)


**Question 6**
---
-- Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

 

For example:

Result
COUNT
----------
8

```sql
-- SELECT COUNT(*) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/e61081d5-0023-4e24-ac10-09029bae5e98)


**Question 7**
---
--Write a SQL query to find Who has the highest income among employee living in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
name        max(income)
----------  -----------
Adam        5000000


```sql
-- SELECT name, max(income)
FROM employee
WHERE city = 'California';
```

**Output:**

![image](https://github.com/user-attachments/assets/2502cd0c-a9d5-49a0-b99f-825a1b9245d3)


**Question 8**
---
--Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products



For example:

Result
category_id  COUNT
-----------  ----------
3            3


```sql
-- SELECT category_id, COUNT(*) AS COUNT
FROM products
WHERE category_id>2
GROUP BY category_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/c2575633-35d0-43fe-ac96-9429d4e75e48)

**Question 9**
---
-- Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.

Sample table: customer1



For example:

Result
age_group   MIN(age)
----------  ----------
20          22


```sql
-- SELECT(age / 5) * 5 AS age_group , MIN(age)
FROM customer1
GROUP BY age_group
HAVING MIN(age) < 25;
```

**Output:**

![image](https://github.com/user-attachments/assets/26006464-b845-4f52-8c9b-c8abe66ba5c2)

**Question 10**
---
--Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1



For example:

Result
occupation  MIN(workhour)
----------  -------------
Business    10
Doctor      15
Engineer    12
Teacher     9


```sql
-- SELECT occupation, MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8;
```

**Output:**

![image](https://github.com/user-attachments/assets/a7cfafc0-6aaa-4ee8-b436-0681e467d6ca)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
