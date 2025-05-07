# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

*Types:*
- *Single-row subquery*:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- *Multiple-row subquery*:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- *Correlated subquery*:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

*Example:*
sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

### Views
A view is a virtual table based on the result of an SQL SELECT query.
*Create View:*
sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;

*Drop View:*
sql
DROP VIEW view_name;


*Question 1*
--
![Screenshot 2025-04-29 141038](https://github.com/user-attachments/assets/c35dd010-6f7b-41ec-81c3-2563667a3b40)

```
sql
select * from CUSTOMERS
where ADDRESS = 'Delhi';
```

*Output:*

![Screenshot 2025-04-29 141049](https://github.com/user-attachments/assets/39392372-2706-45e7-8153-968c7ba2e34d)


*Question 2*
---
![Screenshot 2025-04-29 141107](https://github.com/user-attachments/assets/75113eda-b685-4c99-ab69-cff61cdb14c4)

```
sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN customer c ON s.salesman_id = c.salesman_id
GROUP BY s.salesman_id, s.name
HAVING COUNT(c.customer_id) > 1;
```

*Output:*

![Screenshot 2025-04-29 141116](https://github.com/user-attachments/assets/5c0a6297-ead0-4ce5-a086-6df1694318df)


*Question 3*
---
![Screenshot 2025-04-29 141127](https://github.com/user-attachments/assets/525060e6-0f85-4b02-bed6-e78cb5e010b9)

```
sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.name='Paul Adam';
```

*Output:*

![Screenshot 2025-04-29 141137](https://github.com/user-attachments/assets/25363768-e7d8-4025-b003-b5f6095f07c4)


*Question 4*
---
![Screenshot 2025-04-29 141146](https://github.com/user-attachments/assets/4c2365c6-ecec-4c5c-9759-4ce01b1b4459)

```
sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

*Output:*

![Screenshot 2025-04-29 141159](https://github.com/user-attachments/assets/dd030e9c-9b01-46c3-8419-b6605399ddd9)


*Question 5*
---
![Screenshot 2025-04-29 141211](https://github.com/user-attachments/assets/42ab71b9-eb56-457f-ae98-f4b412edd8c2)

```
sql
select * from CUSTOMERS
where SALARY = 1500;
```

*Output:*

![Screenshot 2025-04-29 141221](https://github.com/user-attachments/assets/a9f928d4-2b00-453a-9f66-6dd019242608)


*Question 6*
---
![Screenshot 2025-04-29 141230](https://github.com/user-attachments/assets/7662c4f1-4b50-4296-ae13-75a966ef12e2)

```
sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM ORDERS
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM ORDERS
    WHERE ord_date ='2012-10-10'
);
```

*Output:*

![Screenshot 2025-04-29 141238](https://github.com/user-attachments/assets/e5f7efa8-0f3e-4e72-b5ff-196ca827a0e2)


*Question 7*
---
![Screenshot 2025-04-29 141245](https://github.com/user-attachments/assets/712bf45c-d7cd-4128-97c1-b66680adb209)

```
sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3,7)
);
```

*Output:*
![Screenshot 2025-04-29 141252](https://github.com/user-attachments/assets/d1dd3642-3746-4fbe-a5d4-79fd03b778b7)


*Question 8*
---
![Screenshot 2025-04-29 141303](https://github.com/user-attachments/assets/37ea3736-54c7-4d85-8952-0dcbf43e3d2b)

```
sql
SELECT student_name, grade
FROM GRADES g1
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES g2
    WHERE g2.subject = g1.subject
);

```
*Output:*

![Screenshot 2025-04-29 141312](https://github.com/user-attachments/assets/dc46652f-18a9-4e62-8001-5c4ee513cd44)


*Question 9*
---
![Screenshot 2025-04-29 141324](https://github.com/user-attachments/assets/2a6b5c7d-fda0-4984-8441-0a84af9465b1)
```
sql
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);

```
*Output:*

![Screenshot 2025-04-29 141332](https://github.com/user-attachments/assets/17931586-0016-4576-991a-e2887f36ed6f)


*Question 10*
---
![Screenshot 2025-04-29 141342](https://github.com/user-attachments/assets/77ce1581-266f-48e9-8f3a-2dbfd8195218)

```
sql
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);
```

*Output:*

![Screenshot 2025-04-29 141348](https://github.com/user-attachments/assets/2c7782ad-7eff-45e2-9218-210a5691d27f)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
