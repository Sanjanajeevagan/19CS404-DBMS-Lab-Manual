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

Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL

```sql
create table orders(
ord_id TEXT CHECK(LENGTH(ord_id)=4),
item_id TEXT NOT NULL,
ord_date DATE NOT NULL,
ord_qty INTEGER,
cost INTEGER,
PRIMARY KEY(item_id,ord_date)
)
```

**Output:**

<img width="1247" height="372" alt="Screenshot 2025-09-27 091638" src="https://github.com/user-attachments/assets/4fa6fb34-a615-499f-9117-b2ba2bd301a8" />


**Question 2**

In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES('5','George Clark','Consultant',NULL,NULL),
      ('7','Noah Davis','Manager','HR','60000'),
      ('8','Ava Miller','Consultant','IT',NULL);
```

**Output:**

<img width="1260" height="314" alt="Screenshot 2025-09-27 091757" src="https://github.com/user-attachments/assets/6a4cc826-eec5-4cd6-883b-6690580320d2" />


**Question 3**

Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.


```sql
create table contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(LENGTH(phone)>=10)
)

```

**Output:**

<img width="1263" height="370" alt="Screenshot 2025-09-27 092131" src="https://github.com/user-attachments/assets/6f80c6f7-491b-47e1-9595-fccaf02ef82b" />


**Question 4**

Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
)
```

**Output:**

<img width="1264" height="404" alt="Screenshot 2025-09-27 092151" src="https://github.com/user-attachments/assets/649741f6-ffb8-4cfd-b1c3-19382e9536d3" />


**Question 5**

Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

```sql

alter table Student_details
add column Email VARCHAR(50);
alter table Student_details
add column MARKS DEFAULT 0;

```

**Output:**
<img width="1255" height="286" alt="Screenshot 2025-09-27 092220" src="https://github.com/user-attachments/assets/65977e06-17df-42f4-8f6e-5123f11d3688" />



**Question 6**

Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql

create table Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
)

```

**Output:**

<img width="1259" height="334" alt="Screenshot 2025-09-27 092246" src="https://github.com/user-attachments/assets/e4362d56-9724-4b51-bd36-0b0535d0953e" />


**Question 7**

Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql

create table Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
)

```

**Output:**

<img width="1261" height="337" alt="Screenshot 2025-09-27 092311" src="https://github.com/user-attachments/assets/a3439b31-f9fd-4052-9368-9f6054b73f2d" />


**Question 8**

Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

For example:

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES('1','Sarah Parker','Manager','HR','60000');


```

**Output:**

<img width="1265" height="305" alt="Screenshot 2025-09-27 092332" src="https://github.com/user-attachments/assets/4613e9c3-40a4-4270-80d0-3875786e2538" />


**Question 9**

Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

```sql
alter table books
add column ISBN varchar(30);
alter table books
add column domain_dept varchar(30);
```

**Output:**
<img width="1258" height="422" alt="Screenshot 2025-09-27 092355" src="https://github.com/user-attachments/assets/f6a9f82a-38cd-4d59-88dd-630978809603" />



**Question 10**

Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

```sql
  
create table Attendance(AttendanceID INTEGER primary key,EmployeeID INTEGER,AttendanceDate DATE,
Status TEXT CHECK(Status in('Present','Absent','Leave')),FOREIGN KEY (EmployeeID) references Employees(EmployeeID)  );


```

**Output:**

<img width="1268" height="343" alt="Screenshot 2025-09-27 092458" src="https://github.com/user-attachments/assets/3e8a78b1-2bbf-4c16-afc0-19252ac39d55" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
