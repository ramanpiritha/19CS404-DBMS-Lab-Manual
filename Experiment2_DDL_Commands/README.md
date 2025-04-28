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
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.
```
alter table Student_details
add column Email varchar(50);
alter table Student_details
add column MARKS INT default 0;

```

**Output:**

![image](https://github.com/user-attachments/assets/c240767d-9a76-4fc5-9680-33e7b396caab)


**Question 2**

Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```
create table Attendance(AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT check(status in('Present', 'Absent', 'Leave')),
foreign key (EmployeeID) references Employees(EmployeeID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/b67fd78a-ecad-4b0a-aa83-858d7d7627a3)

**Question 3**
In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

CustomerID  Name          Address      City        ZipCode
----------  ------------  ----------   ----------  ----------
306         Diana Prince  Themyscira
307         Bruce Wayne   Wayne Manor  Gotham      10007
308         Peter Parker  Queens                   11375
 
```
insert into Customers(CustomerID,Name,Address,City,ZipCode)values(306,"Diana Prince","Themyscira",NULL,NULL);
insert into Customers(CustomerID,Name,Address,City,ZipCode)values(307,"Bruce Wayne","Wayne Manor","Gotham",10007);
insert into Customers(CustomerID,Name,Address,City,ZipCode)values(308,"Peter Parker","Queens",NULL,11375);
```

**Output:**

![image](https://github.com/user-attachments/assets/9d91b677-d3b2-4962-ac5b-3c013bc22611)

**Question 4**
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```
create table contacts(contact_id INTEGER primary key,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT not NULL check(length(phone)>=10)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/d7b01c56-81b2-48e0-9b0c-5661598b601b)

**Question 5**
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

 
```
alter table employee
add column department_id INTEGER;
alter table employee
add column manager_id INTEGER default NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/1cecb8c5-5b55-4fde-8910-0ee1191bd1c3)


**Question 6**
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
```
insert into Student_details
select * from Archived_students;
```

**Output:**

![image](https://github.com/user-attachments/assets/c9974ca8-ec1f-4dc2-b07d-433cb5a692a9)

**Question 7**
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```
create table Members(MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/ef43c0c0-825b-42ee-9d80-c5f07fc23699)

**Question 8**
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```
create table item(item_id TEXT primary key,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT(4),
foreign key (icom_id)references company(com_id) on update set NULL on delete set NULL
);
```

**Output:**

![image](https://github.com/user-attachments/assets/51a84dbb-62b1-49ed-99ef-9b254ce3be04)

**Question 9**
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```
create table ProjectAssignments(AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
foreign key (EmployeeID)references Employees(EmployeeID),
foreign key (ProjectID)references Projects(ProjectID)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/bdb0a3ac-260d-4f64-b9a1-74ad508a7a03)

**Question 10**
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.



```
insert into Student_details(RollNo,Name,Gender,Subject,MARKS)values(201,"David Lee","M","Physics",92);
```

**Output:**

![image](https://github.com/user-attachments/assets/76eafbae-cb30-4f6b-85b9-ce12ff259aee)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
