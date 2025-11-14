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
Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column. Include conditions to filter for patients discharged between '2024-03-01' and '2024-03-31' but not admitted during the same period.

```sql
select 
      p.first_name,
      s.*
from 
      patients p
inner join 
      surgeries s
on 
     p.patient_id = s.patient_id
where 
     p.discharge_date between '2024-03-01' and '2024-03-31' 
     and(
          p.admission_date < '2024-03-01'
          or p.discharge_date >'2024-03-31' 
        );
```

**Output:**


<img width="1040" height="369" alt="image" src="https://github.com/user-attachments/assets/df8b0083-33a2-4d80-8dd2-fdfe96e2dfc1" />


**Question 2**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

```sql
select c.cust_name,o.ord_no,o.ord_date,o.purch_amt
from customer c
left join orders o on c.customer_id = o.customer_id;

```

**Output:**


<img width="1230" height="396" alt="image" src="https://github.com/user-attachments/assets/8f67d28d-07fd-44ec-9afe-87c62c2d388b" />


**Question 3**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```sql
select o.ord_no,o.purch_amt,o.ord_date,c.cust_name,c.city as customer_city,c.grade,s.name as salesman_name , s.city as salesman_city ,s.commission
from orders o
inner join customer c on o.customer_id  = c.customer_id 
inner join salesman s on  c.salesman_id = s.salesman_id;

```

**Output:**


<img width="1131" height="409" alt="image" src="https://github.com/user-attachments/assets/1673798b-dfab-4b3e-a5cb-d96830e12acf" />

**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test name 'X-Ray' and a result of 'Normal'.

```sql
select p.*
from patients p
inner join test_results t on p.patient_id = t.patient_id 
where t.test_name = 'X-Ray' and  
       t.result ='Normal';
```

**Output:**


<img width="863" height="327" alt="image" src="https://github.com/user-attachments/assets/f57e9b82-ece6-4ad4-ac3e-c70fab789400" />


**Question 5**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT 
    c.cust_name,
    c.city ,
    c.grade,
    s.name AS Salesman,
    s.city 
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**


<img width="1341" height="270" alt="image" src="https://github.com/user-attachments/assets/099898e6-a7ec-4b1f-9565-b97004a50d4f" />


**Question 6**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
INNER JOIN 
    customer c 
ON 
    o.customer_id = c.customer_id
INNER JOIN 
    salesman s 
ON 
    o.salesman_id = s.salesman_id;

```

**Output:**


<img width="1325" height="398" alt="image" src="https://github.com/user-attachments/assets/d3f00c92-e440-4aa9-afa3-91eb5ded8777" />


**Question 7**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city ,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**


<img width="1230" height="255" alt="image" src="https://github.com/user-attachments/assets/9463d5b1-6172-4403-b7e9-24b1bef40af3" />

**Question 8**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city ,
    s.name AS "Salesman",
    s.city ,
    s.commission
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.city <> c.city
    AND s.commission > 0.12;

```

**Output:**


<img width="1006" height="235" alt="image" src="https://github.com/user-attachments/assets/440191c5-dff1-4e68-9e7a-12b97b38862a" />


**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

```sql
SELECT 
    n.*
FROM 
    nurses n
INNER JOIN 
    departments d
ON 
    n.department_id = d.department_id
WHERE 
    d.department_name = 'Pediatrics';

```

**Output:**


<img width="1270" height="359" alt="image" src="https://github.com/user-attachments/assets/74d59ad5-3a38-4754-ac7c-88ccb65d5f70" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.

```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.name = 'Mc Lyon';

```

**Output:**


<img width="1320" height="329" alt="image" src="https://github.com/user-attachments/assets/8265083b-19f3-46b1-8a32-5c8adad28358" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
