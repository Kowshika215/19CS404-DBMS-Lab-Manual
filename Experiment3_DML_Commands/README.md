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
--
Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

Sample table: customer

```
select * from customer
where grade is null;
```

**Output:**
<img width="1233" height="503" alt="image" src="https://github.com/user-attachments/assets/32dcb912-885d-491b-baab-fd3f443ad6f3" />


**Question 2**
---
Write a SQL query to find all employees along with the day of the week on which they were hired from the emp table

```
SELECT 
    ename, 
    hiredate, 
    CASE STRFTIME('%w', hiredate)
        WHEN '0' THEN 'Sunday'
        WHEN '1' THEN 'Monday'
        WHEN '2' THEN 'Tuesday'
        WHEN '3' THEN 'Wednesday'
        WHEN '4' THEN 'Thursday'
        WHEN '5' THEN 'Friday'
        WHEN '6' THEN 'Saturday'
    END AS day_of_week
FROM emp;
```

**Output:**
<img width="872" height="449" alt="image" src="https://github.com/user-attachments/assets/d5962062-f993-4a5b-9656-6e71f298d63f" />



**Question 3**
---

Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount.

Sample table: products
```
SELECT 
product_id,
original_price,
discount_percentage,
original_price * discount_percentage AS discount_amount
FROM products
WHERE original_price * discount_percentage > 50;
```

**Output:**

<img width="873" height="340" alt="image" src="https://github.com/user-attachments/assets/bca71e49-44b7-48d5-b729-7fdb187bd698" />


**Question 4**
---
 Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.

EmployeeInfo Table

```
SELECT SUBSTR(EmpLname, 1, 4)
FROM EmployeeInfo;
```

**Output:**

<img width="851" height="397" alt="image" src="https://github.com/user-attachments/assets/1e33b5d6-3ae9-4351-ab86-8dbbec4e0311" />


**Question 5**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.


Employees table

```
update employees
set first_name='John'
where department_id=80 and commission_pct<0.35;
```

**Output:**

<img width="1234" height="630" alt="image" src="https://github.com/user-attachments/assets/b44c297b-0ffc-4b6d-b98e-7117cebcc744" />


**Question 6**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

```
delete from doctors
where doctor_id between 2 and 4;
```

**Output:**

<img width="1238" height="916" alt="image" src="https://github.com/user-attachments/assets/cccd66c2-7aa9-4b5f-8843-6ead65388d42" />


**Question 7**
---
Write a SQL query to retrieve the details of all customers whose ID belongs to any of the values 3007, 3008 or 3009. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

```
select * from customer
where customer_id in (3007,3008,3009);

```

**Output:**
<img width="862" height="487" alt="image" src="https://github.com/user-attachments/assets/4e14af80-5dbe-4fcc-8c2f-48282b49c156" />


**Question 8**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

```
update purchases
set per_unit_price=25,total_price=quantity*25
where purchase_date='2022-08-15' and product_id=12;
```

**Output:**

<img width="852" height="602" alt="image" src="https://github.com/user-attachments/assets/f497bccb-1418-488c-a215-d5069bf24f50" />


**Question 9**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

```
DELETE FROM Doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology');
```

**Output:**

<img width="1265" height="909" alt="image" src="https://github.com/user-attachments/assets/525e5670-f127-4169-8e4c-9f19f2b872ee" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
Sample table: Customer

```
delete from customer
where grade<2;
```

**Output:**

<img width="1289" height="551" alt="image" src="https://github.com/user-attachments/assets/9c1de215-98dd-4c32-9957-3efb3f105389" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
