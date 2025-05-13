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
--
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
create table ProjectAssignments(

AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)


);
```

**Output:**

![Screenshot 2025-05-13 134518](https://github.com/user-attachments/assets/cd425635-c63a-414d-8cc2-9d8c1f17278c)


**Question 2**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
create table jobs(

job_id INT,
job_title VARCHAR(255) DEFAULT '',
min_salary INT DEFAULT 8000,
max_salary INT DEFAULT NULL

);
```

**Output:**

![Screenshot 2025-05-13 134648](https://github.com/user-attachments/assets/9c8d24ac-c6f9-4b27-ba5f-b6ecdffb46e1)


**Question 3**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
insert into Customers(CustomerID, Name, Address, City, ZipCode)
VALUES (301,'Michael Jordan','123 Maple St','Chicago',60616);
```

**Output:**

![Screenshot 2025-05-13 134748](https://github.com/user-attachments/assets/1b7b88b3-0fcf-46a3-b07f-2ee67a85fa6a)


**Question 4**
---
Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000

```sql
insert into Customers(ID,NAME,AGE,ADDRESS,SALARY)
VALUES 
(1,'Ramesh',32,'Ahmedabad',2000),
(2,'Khilan',25,'Delhi',1500),
(3,'Kaushik',23,'Kota',2000);
```

**Output:**

![Screenshot 2025-05-13 134835](https://github.com/user-attachments/assets/e348d64e-54bf-4c4d-ab25-ebb59d0ede2a)


**Question 5**
---
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```sql
alter table Student_details
add column Date_of_birth Date;
```

**Output:**

![Screenshot 2025-05-13 134924](https://github.com/user-attachments/assets/4018bc11-4e12-40c8-88ca-4643cdee702b)


**Question 6**
---
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

```sql
alter table employee
add column department_id INTEGER;

alter table employee
add column manager_id INTEGER default NULL;
```

**Output:**

![Screenshot 2025-05-13 135146](https://github.com/user-attachments/assets/9c62358e-7344-41f0-9577-059a80a0eca7)


**Question 7**
---
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
create table Members
(

MemberID INTEGER,
MemberName TEXT,
JoinDate DATE

);
```

**Output:**

![Screenshot 2025-05-13 135249](https://github.com/user-attachments/assets/0c53b1e4-da6f-400d-8440-eb1bd493b5c7)


**Question 8**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price should be greater than 0.
Stock should be greater than or equal to 0.

```sql
create table Products
(

ProductID primary key,
ProductName NOT NULL,
Price REAL CHECK (Price > 0),
Stock INTEGER CHECK (Stock >= 0)

);
```

**Output:**

![Screenshot 2025-05-13 135433](https://github.com/user-attachments/assets/7bc25c44-35e6-416c-bd84-827db0c5a18f)


**Question 9**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
insert into Customers(CustomerID, Name, Address, Email)
select CustomerID,Name,Address,Email
from Old_customers;
```

**Output:**

![Screenshot 2025-05-13 135617](https://github.com/user-attachments/assets/e3f698f7-0129-47b5-8878-58031025031d)


**Question 10**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
create table Orders
(

OrderID INTEGER primary key,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) references Customers(CustomerID)
);
```

**Output:**

![Screenshot 2025-05-13 135746](https://github.com/user-attachments/assets/5ce89e52-82ec-4dbb-ab7f-f5e59bf3c940)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
