# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
```
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
```
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1,
 value_2, ...);
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
```
Write a SQL statement to change the first_name column of employees table with 'John' for
 those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```
update employees set first_name="John" where department_id=80 and commission_pct<0.35;
```

**Output:**

![image](https://github.com/user-attachments/assets/4a57a58a-1262-402b-8cab-aed55148cb07)

**Question 2**
```
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity
 in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```

```
update Products set reorder_lvl=reorder_lvl*0.7
where lower(product_name) LIKE '%cream%'
and quantity>reorder_lvl;
```

**Output:**
![image](https://github.com/user-attachments/assets/d93a57f8-6dfc-44d0-9cb4-3d725e1750c6)


**Question 3**
```
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```
update employees set HIRE_DATE="2024-01-24";
```

**Output:**

![image](https://github.com/user-attachments/assets/0b1870a6-bae1-441f-803b-c5a398175730)

**Question 4**
```
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```

```
update suppliers set address='58 Lakeview, Magnolia' where supplier_id=5;
```

**Output:**

![image](https://github.com/user-attachments/assets/166b73ec-491d-4bc2-b001-65adc5642a7b)

**Question 5**
```
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```
```
update products
set reorder_lvl=40
where category='Grocery';
```

**Output:**

![image](https://github.com/user-attachments/assets/9eb038db-23b4-4b2d-8d67-62020cfc3539)

**Question 6**
```
Write a SQL statement to retrieve city(column name) of all customers from customers table without any repeats.

```
```
select distinct city
from customers
```

**Output:**

![image](https://github.com/user-attachments/assets/3f5703a4-c4e5-4ff7-b1c1-c732c31ff093)

**Question 7**
```
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100,
between 50 and 100, or less than 50 in the Calculations table

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
```
select id,decimal,case
when decimal>100 then 'High'
when decimal>=50 and decimal<=100 then 'Medium'
else 'Low'
end as category
from calculations;
```

**Output:**

![image](https://github.com/user-attachments/assets/6623b276-97e5-4582-a541-a820431de96e)

**Question 8**
```
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater
 than 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```
```
select customer_id, cust_name,city, grade,salesman_id
from customer where city='New York' or grade<=100;
```

**Output:**

![image](https://github.com/user-attachments/assets/a97c7d42-39fc-4310-942e-2c16bb6c0a2c)

**Question 9**
```
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200.
 Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```
```
select customer_id, cust_name, city, grade,salesman_id
from customer where city='London' and grade>200;
```

**Output:**

![image](https://github.com/user-attachments/assets/f28b6a74-e53d-4bb1-9e25-76509557c897)

**Question 10**
```
Write a SQL query to identify the top 3 most expensive discounted products. Return product_id,
 original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

 ------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 150.00 | 0.15 

103 | 200.00 | 0.20 

104 | 300.00 | 0.25
```
```
select product_id,original_price,discount_percentage,
original_price*(1-discount_percentage) as discounted_price
from products
order by original_price desc
limit 3;
```

**Output:**

![image](https://github.com/user-attachments/assets/cc1cbf63-2366-4d6e-b9e9-d68b6bc2a892)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
