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
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

```
ALTER TABLE student_details
ADD email TEXT DEFAULT 'Invalid' NOT NULL;

```

**Output:**

<img width="1238" height="327" alt="image" src="https://github.com/user-attachments/assets/eb8b8617-bf8d-4db6-89de-f53610aa6c85" />


**Question 2**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);

```

**Output:**

<img width="1246" height="369" alt="image" src="https://github.com/user-attachments/assets/70896b05-af7a-4081-b199-bda68c2081ce" />


**Question 3**
---
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

```
ALTER TABLE employee ADD COLUMN department_id INTEGER;
ALTER TABLE employee ADD COLUMN manager_id INTEGER DEFAULT NULL;

```

**Output:**

<img width="1231" height="394" alt="image" src="https://github.com/user-attachments/assets/81cb479e-03b7-40c1-9cdc-1b9cdb0fad77" />


**Question 4**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

<img width="1222" height="461" alt="image" src="https://github.com/user-attachments/assets/c196bf17-08bb-4048-8bae-62f4db0fbf3e" />

**Question 5**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT NOT NULL UNIQUE,
Price REAL CHECK (Price>0),
StockQuantity INTEGER CHECK (StockQuantity >=0)
);

```

**Output:**

<img width="1235" height="366" alt="image" src="https://github.com/user-attachments/assets/976419c6-af50-40e9-b8c1-9bc961cb636e" />


**Question 6**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```
INSERT INTO Products SELECT * FROM Discontinued_Products;
```

**Output:**

<img width="1208" height="371" alt="image" src="https://github.com/user-attachments/assets/8ee4a94b-df1f-474c-8b8f-5edf24a5caae" />


**Question 7**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.
```
INSERT INTO Customers(CustomerID,Name,Address,City,Zipcode)
VALUES (301,'Michael Jordan','123 Maple St','Chicago',60616);
```

**Output:**

<img width="1215" height="308" alt="image" src="https://github.com/user-attachments/assets/53ae6957-3c44-4515-ac22-506a40e1af5f" />


**Question 8**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```
CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL(10,2) DEFAULT 0 NOT NULL,
CHECK (list_price >= discount AND discount >= 0 AND list_price >=0)
);
```

**Output:**

<img width="1226" height="369" alt="image" src="https://github.com/user-attachments/assets/ec9bb909-4f4d-4e85-b3d9-1ba59ef3a9ea" />


**Question 9**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```
INSERT INTO Student_details (RollNo,Name,Gender,Subject,MARKS)
VALUES (201,'David Lee','M','Physics',92);
```

**Output:**
<img width="1214" height="313" alt="image" src="https://github.com/user-attachments/assets/05fdbd62-131f-4adb-b925-160000d64100" />


**Question 10**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```
CREATE TABLE Employees(
EmployeeID INT PRIMARY KEY,
FirstName VARCHAR (50) NOT NULL,
LastName VARCHAR (50) NOT NULL,
Email VARCHAR(100) UNIQUE,
Salary DECIMAL (10,2) CHECK (Salary>0),
DepartmentID INT,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1232" height="506" alt="image" src="https://github.com/user-attachments/assets/773c8972-8660-4dae-ac82-3bd6afa836ef" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
