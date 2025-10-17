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
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

```sql
SELECT DoctorID , count(*) as TotalAppointments from Appointments GROUP BY DoctorID;
```

**Output:**

<img width="1264" height="616" alt="image" src="https://github.com/user-attachments/assets/ae2f84b7-d93f-4725-84bd-a49bc5d22a9b" />

**Question 2**

How many patients are there in each city?

Sample table: Patients Table
```sql
--select address ,count(*) as TotalPatients from Patients GROUP BY Address;
```

**Output:**

<img width="1271" height="460" alt="image" src="https://github.com/user-attachments/assets/caa0801f-629d-4a94-9de7-f635082acf13" />


**Question 3**
---
How many patients are there in each city?

Sample table: Patients Table



```sql
select address ,count(*) as TotalPatients from Patients GROUP BY Address;
```

**Output:**


<img width="638" height="441" alt="image" src="https://github.com/user-attachments/assets/94499a86-e50d-4f36-bd52-1f88aa107e9d" />

**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer
```sql
Select count(*) as COUNT from customer where city<>'Noida';
```

**Output:**

<img width="996" height="286" alt="image" src="https://github.com/user-attachments/assets/317c4cc0-e187-4e48-93c3-e818d86dd3bd" />


**Question 5**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
select count(DISTINCT salesman_id) as COUNT FROM orders;
```

**Output:**

<img width="544" height="307" alt="image" src="https://github.com/user-attachments/assets/ec716483-1d00-4620-8b92-497ad8b343e9" />


**Question 6**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select name as Employee_Name , age as Age from employee order by age ASC LIMIT 1;
```

**Output:**

<img width="695" height="276" alt="image" src="https://github.com/user-attachments/assets/2496da0f-2d95-4b71-9848-1d833131bdda" />


**Question 7**
---
Write a SQL query to  find the average salary of all employees?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

```sql
select avg(income) as Average_Salary from employee ;
```

**Output:**

<img width="907" height="350" alt="image" src="https://github.com/user-attachments/assets/df53a212-d946-4242-93e1-30227d34cda7" />

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1

```sql
select jdate, MAX(workhour)  from employee1 group by jdate HAVING MAX(workhour) > 12;
```

**Output:**

<img width="683" height="422" alt="image" src="https://github.com/user-attachments/assets/81a5f18d-8aec-4b8f-b45d-add1379ac126" />

**Question 9**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1
```sql
select jdate,SUM(workhour) from employee1 group by jdate HAVING SUM(workhour) > 40;
```

**Output:**


<img width="654" height="429" alt="image" src="https://github.com/user-attachments/assets/1b334efb-fc9b-470c-b404-e1ffcc56e685" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

```sql
select occupation,AVG(workhour) from employee1 group by occupation having AVG(workhour) between 10 and 12;
```

**Output:**


<img width="712" height="436" alt="image" src="https://github.com/user-attachments/assets/7c7467d9-8b7b-4182-99f0-7c263f855118" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
