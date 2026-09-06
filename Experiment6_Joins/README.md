# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;
```

**Output:**

<img width="857" height="858" alt="image" src="https://github.com/user-attachments/assets/b0f8c874-eb5d-4393-a1eb-aa2f09af4a51" />


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'.
```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

**Output:**

<img width="858" height="492" alt="image" src="https://github.com/user-attachments/assets/f5e61b9d-dc06-472e-a97d-bdb4cbe361ad" />


**Question 3**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```
SELECT p.first_name AS patient_name,t.test_name AS test_name
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id;
```

**Output:**

<img width="857" height="620" alt="image" src="https://github.com/user-attachments/assets/d4778475-f84e-41ae-996a-4ba190e6b139" />


**Question 4**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.

```
select p.first_name as patient_name, d.first_name as doctor_name
from patients p
join doctors d on p.doctor_id=d.doctor_id
where p.discharge_date is not null;
```

**Output:**

<img width="875" height="477" alt="image" src="https://github.com/user-attachments/assets/3561beb1-5c25-401d-83b0-6f145a9c5ee0" />


**Question 5**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.
```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="855" height="500" alt="image" src="https://github.com/user-attachments/assets/6639a554-d11e-4de8-ae9f-8df592b80a98" />


**Question 6**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

```
SELECT 
    n.*
FROM 
    nurses AS n
INNER JOIN 
    departments AS d ON n.department_id = d.department_id
WHERE 
    d.department_name = 'Pediatrics';
```

**Output:**

<img width="863" height="497" alt="image" src="https://github.com/user-attachments/assets/06e53515-09eb-4838-a674-e7456b793c43" />


**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a ON p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="837" height="498" alt="image" src="https://github.com/user-attachments/assets/ea83f473-e45f-4660-b2d7-713e8e86adb8" />


**Question 8**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city,
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12
    AND c.city <> s.city;
```

**Output:**


<img width="853" height="718" alt="image" src="https://github.com/user-attachments/assets/aa96dd4e-eee1-4379-9d29-f6034d9ca5dc" />


**Question 9**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column.

```
select s.name, c.cust_name, c.city, c.grade, c.salesman_id
from salesman s
left join customer c on s.salesman_id= c.salesman_id

```

**Output:**


<img width="1257" height="912" alt="image" src="https://github.com/user-attachments/assets/24e2cdac-9c21-46ae-9c04-6c3c934d514e" />


**Question 10**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

```
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**


<img width="728" height="552" alt="image" src="https://github.com/user-attachments/assets/f4f3968d-ab73-4095-a41e-0ba89dafd28a" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
