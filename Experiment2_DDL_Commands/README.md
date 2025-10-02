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
<img width="1135" height="382" alt="Screenshot 2025-10-02 135439" src="https://github.com/user-attachments/assets/8bfc2901-7eae-4f6c-88ea-45c1a174cb1f" />

```
INSERT INTO Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```

**Output:**

<img width="1266" height="410" alt="Screenshot 2025-10-02 135510" src="https://github.com/user-attachments/assets/a129a332-e616-4bdd-81ee-6380a4881cce" />


**Question 2**
---
<img width="1317" height="495" alt="Screenshot 2025-10-02 135616" src="https://github.com/user-attachments/assets/b5074b49-aab4-46ff-a2a9-0df185378ce0" />


```sql
INSERT INTO Books (ISBN, Title, Author)
VALUES ('978-6655443321', 'Big Data Analytics', 'Karen Adams');
```

**Output:**

<img width="883" height="419" alt="image" src="https://github.com/user-attachments/assets/8cbc03bf-8f25-4d64-86d6-cfc90e61f380" />


**Question 3**
---

<img width="1426" height="429" alt="Screenshot 2025-10-02 135648" src="https://github.com/user-attachments/assets/e08e7991-4efa-4e41-aa6d-512df409540c" />

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    Amount REAL CHECK (Amount > 0),
    DueDate DATE,
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    CHECK (DueDate > InvoiceDate)
);
```

**Output:**

<img width="890" height="383" alt="image" src="https://github.com/user-attachments/assets/56639bfb-13dc-474b-8974-7b935c7e49fa" />


**Question 4**
---

<img width="1435" height="301" alt="Screenshot 2025-10-02 135708" src="https://github.com/user-attachments/assets/b6dcf547-a55a-44e9-ba8c-deb32539e499" />

```sql
CREATE TABLE jobs (
    job_id INTEGER,
    job_title TEXT DEFAULT '',
    min_salary INTEGER DEFAULT 8000,
    max_salary INTEGER DEFAULT NULL
);
```

**Output:**

<img width="895" height="431" alt="image" src="https://github.com/user-attachments/assets/bd983daf-6ca5-4eca-baa1-a9d30591edbd" />


**Question 5**
---

<img width="1415" height="383" alt="Screenshot 2025-10-02 135717" src="https://github.com/user-attachments/assets/76b02326-70b9-484b-9eac-f33ae20c5f17" />

```sql
CREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

<img width="889" height="388" alt="image" src="https://github.com/user-attachments/assets/486f6fd7-a297-4109-ba34-046cde96286a" />


**Question 6**
---
<img width="1423" height="481" alt="Screenshot 2025-10-02 135728" src="https://github.com/user-attachments/assets/b3713750-088c-4fe6-984b-efa8493ed40b" />


```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;

ALTER TABLE Companies ADD COLUMN mobilenumber number;

ALTER TABLE Companies ADD COLUMN DOB Date;

ALTER TABLE Companies ADD COLUMN State varchar(30);
```

**Output:**

<img width="892" height="492" alt="image" src="https://github.com/user-attachments/assets/999b76e0-2be5-4287-9525-1a5ddac31491" />


**Question 7**
---
<img width="1401" height="513" alt="Screenshot 2025-10-02 135735" src="https://github.com/user-attachments/assets/2b7ee64f-8c9b-49c7-813a-68b2437acdd8" />


```sql
INSERT INTO Employee (EmployeeID, Name, Position)
VALUES (5, 'George Clark', 'Consultant');

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (7, 'Noah Davis', 'Manager', 'HR', 60000);

INSERT INTO Employee (EmployeeID, Name, Position, Department)
VALUES (8, 'Ava Miller', 'Consultant', 'IT');
```

**Output:**

<img width="879" height="383" alt="image" src="https://github.com/user-attachments/assets/d678cf22-d9d4-46eb-b3a4-c97f4fcab178" />


**Question 8**
---

<img width="1411" height="369" alt="Screenshot 2025-10-02 135744" src="https://github.com/user-attachments/assets/c7d9c604-0a3e-442d-b02d-94983f837a93" />

```sql
ALTER TABLE Student_details
ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**

<img width="901" height="366" alt="image" src="https://github.com/user-attachments/assets/e2948149-37a5-4b8e-a739-ee2f6aa32bc0" />


**Question 9**
---

<img width="1418" height="433" alt="Screenshot 2025-10-02 135756" src="https://github.com/user-attachments/assets/f4cde11c-1a1f-4a59-845e-28ba93e4e1dc" />

```sql
CREATE TABLE Events (
    EventID INTEGER,
    EventName TEXT,
    EventDate DATE
);
```

**Output:**

<img width="907" height="473" alt="image" src="https://github.com/user-attachments/assets/1783deec-1fd4-4be6-85ac-20236751a41c" />


**Question 10**
---

<img width="1387" height="403" alt="Screenshot 2025-10-02 135809" src="https://github.com/user-attachments/assets/76731ab3-509c-4f79-b79c-1d8fe99ed8c3" />

```sql
CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="883" height="391" alt="image" src="https://github.com/user-attachments/assets/743bcf24-c57b-435c-a52b-557f2107d384" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
