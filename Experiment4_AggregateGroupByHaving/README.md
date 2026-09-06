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
---
Write a SQL query to find the average length of names for people living in Chennai?

```
SELECT 
  AVG(LENGTH(name)) AS avg_name_length
FROM customer
WHERE city = 'Chennai';

```

**Output:**
<img width="1228" height="391" alt="image" src="https://github.com/user-attachments/assets/0f62ae44-6cc8-48de-9348-243961d3d46e" />



**Question 2**
---
Write a SQL query to find the total income of employees aged 40 or above.

```
select sum(income) as total_income
from employee
where age >= 40;
```

**Output:**

<img width="863" height="387" alt="image" src="https://github.com/user-attachments/assets/d69482ca-63b6-408c-8aec-1b2902503153" />


**Question 3**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

```
select avg(income) as avg_income
from employee
where name like 'A%';
```

**Output:**

<img width="865" height="397" alt="image" src="https://github.com/user-attachments/assets/d0924d7d-f3f0-4a14-ab46-fa6945c2c269" />


**Question 4**
---
What is the count of male and female patients?

```
select gender,count(*) as TotalPatients
from patients
group by gender;
```

**Output:**

<img width="861" height="440" alt="image" src="https://github.com/user-attachments/assets/58081b52-8118-4d61-af78-d996e9109665" />

**Question 5**
---
How many prescriptions were written by each doctor?

```
select doctorid,count(*) as TotalPrescriptions
from prescriptions
group by doctorid;
```

**Output:**

<img width="860" height="830" alt="image" src="https://github.com/user-attachments/assets/88323b2e-7fbb-4b3b-b4dd-40ba441f5f20" />


**Question 6**
---
What is the total number of appointments scheduled for each day?

```
select strftime('%Y-%m-%d',AppointmentDatetime) as AppointmentDate,count(*) as TotalAppointments
from appointments
group by appointmentdatetime;
```

**Output:**

<img width="861" height="731" alt="image" src="https://github.com/user-attachments/assets/e8f055c2-e48b-4329-bf89-133f9f52b940" />


**Question 7**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

```
select address,AVG(salary)
from customer1
group by address
having avg(salary) > 5000;
```

**Output:**

<img width="866" height="512" alt="image" src="https://github.com/user-attachments/assets/339844be-e134-4cc1-ba08-69da625ff991" />

**Question 8**
---
Write the SQL query to find how many patients have more than 3 medical records?.

```
SELECT
    PatientID,
    COUNT(*) AS TotalRecords
FROM
    MedicalRecords
GROUP BY
    PatientID
HAVING
    COUNT(*) > 3;
```

**Output:**

<img width="853" height="417" alt="image" src="https://github.com/user-attachments/assets/161db243-c5ec-4fcb-8184-96ebb60b9e7a" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

```
select jdate,max(workhour) as 'MAX(workhour)'
from employee1
group by jdate
having max(workhour) > 12;
```

**Output:**

<img width="862" height="457" alt="image" src="https://github.com/user-attachments/assets/c6c2fadd-0de6-4284-9cb6-4b516d402044" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by age groups, displays the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

```
select (age/5) * 5 as age_group,min(salary) as 'MIN(salary)'
from customer1
group by age_group
having min(salary) < 2000;
```

**Output:**

<img width="851" height="416" alt="image" src="https://github.com/user-attachments/assets/1afdc000-c657-42d9-bf98-bc90dc40c1db" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
