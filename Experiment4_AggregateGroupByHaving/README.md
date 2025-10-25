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
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

```sql
SELECT DoctorID , count(*) as TotalAppointments from Appointments GROUP BY DoctorID;
```

**Output:**

<img width="1000" height="563" alt="image" src="https://github.com/user-attachments/assets/90a8369d-1eb8-4a79-abb1-f943111932aa" />



**Question 2**

How many patients are there in each city?


```sql
select address ,count(*) as TotalPatients from Patients GROUP BY Address;     
```

**Output:**


<img width="766" height="375" alt="image" src="https://github.com/user-attachments/assets/4377c6f3-00cd-4871-b1c1-a8a3fb5c085e" />



**Question 3**

Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer

```sql
Select count(*) as COUNT from customer where city<>'Noida';
```

**Output:**

<img width="1176" height="285" alt="image" src="https://github.com/user-attachments/assets/6904fd93-7079-4680-b3d2-1d03f5043b4e" />



**Question 4**

Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

```sql
select count(DISTINCT salesman_id) as COUNT FROM orders;
```

**Output:**

<img width="501" height="279" alt="image" src="https://github.com/user-attachments/assets/c0e2f45d-166e-4796-b39a-25a3e46c2558" />


**Question 5**
Write a SQL query to find the youngest employee in the company?

Table: employee

```sql
select name as Employee_Name , age as Age from employee order by age ASC LIMIT 1;
```

**Output:**

<img width="573" height="280" alt="image" src="https://github.com/user-attachments/assets/a95ca1f3-fb70-4dd9-b9fe-e2afcd4c7a10" />



**Question 6**
---
Write a SQL query to  find the average salary of all employees?

Table: employee

```sql
select avg(income) as Average_Salary from employee ;
```

**Output:**


<img width="472" height="288" alt="image" src="https://github.com/user-attachments/assets/22b15d82-dd4c-4e78-8d99-154f169459b6" />


**Question 7**
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1

```sql
select jdate, MAX(workhour)  from employee1 group by jdate HAVING MAX(workhour) > 12;
```

**Output:**

<img width="704" height="363" alt="image" src="https://github.com/user-attachments/assets/16591201-d08c-4572-9f05-c104da6448ae" />

**Question 8**

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1

```sql
select jdate,SUM(workhour) from employee1 group by jdate HAVING SUM(workhour) > 40;
```

**Output:**

<img width="585" height="340" alt="image" src="https://github.com/user-attachments/assets/1384e38e-3c2d-40f9-86db-cc6fb1997481" />

**Question 9**

Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

```sql

select occupation,AVG(workhour) from employee1 group by occupation having AVG(workhour) between 10 and 12;

```

**Output:**

<img width="578" height="365" alt="image" src="https://github.com/user-attachments/assets/80df6bde-fed6-4afd-9f72-4271f956221b" />


**Question 10**

What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table


```sql
SELECT DoctorID , count(*) as TotalAppointments from Appointments GROUP BY DoctorID;
```

**Output:**

<img width="703" height="636" alt="image" src="https://github.com/user-attachments/assets/4aca33c0-ffff-4ca6-bf7b-534fc3685fcf" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
