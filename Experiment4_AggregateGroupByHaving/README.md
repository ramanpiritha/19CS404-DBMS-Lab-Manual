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
```
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table
```
![image](https://github.com/user-attachments/assets/264ab6ab-7a09-43b0-b151-d05f20c59de6)


```
SELECT PatientID,COUNT(Medication) AS  TotalMedications 
FROM Prescriptions
GROUP BY patientID;

```

**Output:**

![image](https://github.com/user-attachments/assets/83838443-fb4f-46bf-8803-19a27e881528)

**Question 2**
```
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

id   name   age  address     salary

1    Paul   32   California  20000

4    Mark   25   Richtown    65000

5    David  27   Texas       85000

```
```
SELECT COUNT(*) AS COUNT
FROM (
    SELECT Age
    FROM employee
    GROUP BY Age
    HAVING COUNT(*) > 0
) AS AgeGroups;
```

**Output:**

![image](https://github.com/user-attachments/assets/b65ae65a-b782-4dac-8c49-45885d7d3093)

**Question 3**
```
Write a SQL query to  find the average salary of all employees?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```
```
SELECT AVG(income) AS Average_Salary
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/5c75083a-fca5-4fad-8645-5efc65d10cc1)

**Question 4**
```
Write a SQL query to calculate the total number of working hours of all employees

Sample table: employee1
```
![image](https://github.com/user-attachments/assets/05e67b74-9a3e-4ca3-bd26-2c0b57f28d3b)



```
SELECT SUM(workhour) AS 'Total working hours'
FROM  employee1;
```

**Output:**

![image](https://github.com/user-attachments/assets/f4bd85ff-3f9f-4a7b-a7f3-74b5fb8d2356)

**Question 5**
```
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002
```
```
SELECT COUNT(customer_id) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/73c5b13c-7a85-4914-a3e5-c8d59e7e0be1)

**Question 6**
```
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the
 minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Sample table: employee1
```
![image](https://github.com/user-attachments/assets/7d5971d4-b800-44a1-af5f-c1f92b609dca)


```
SELECT jdate,MIN(workhour) AS  'MIN(workhour)'
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/405919d1-5f5a-44cd-89f5-5fdff39f9bef)

**Question 7**
```
Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income
 for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

Sample table: employee
```
![image](https://github.com/user-attachments/assets/888f053e-e2bc-49d5-88b9-3646a6e8e52b)

```
SELECT age, MAX(income) AS 'MAX(income)'
FROM employee
GROUP BY age
HAVING MAX(income) > 2000000;
```

**Output:**

![image](https://github.com/user-attachments/assets/e475c37c-63ad-47bb-95b6-efe8604e9642)

**Question 8**
```
Write the SQL query that accomplishes the selection of number of products for each category from
products table which includes only those products where the category ID is greater than 2.

Sample table: products

```
![image](https://github.com/user-attachments/assets/4bdd4c58-99b5-4d60-971d-4913075c590d)


```
SELECT category_id, COUNT(*) AS COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/e536f4cf-fb3a-4c07-aa9e-0eef12079433)

**Question 9**
```
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

```
![image](https://github.com/user-attachments/assets/fd10b667-c0bb-4629-8ad9-77f4cb9a39cc)


```
SELECT PatientID,COUNT(medications) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;

```

**Output:**

![image](https://github.com/user-attachments/assets/339e7632-899a-4983-91be-da3d6c9267fe)

**Question 10**
```
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table
```
![image](https://github.com/user-attachments/assets/bdb1682b-6bda-4c1d-a01e-29c60ae7ab0b)


```
SELECT Frequency,COUNT(Frequency) AS  TotalPrescriptions
FROM Prescriptions 
GROUP BY Frequency;
```

**Output:**

![image](https://github.com/user-attachments/assets/9cb087bf-400d-4ebd-ab43-4d4f7678afa2)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
