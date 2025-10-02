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
<img width="1462" height="795" alt="Screenshot 2025-10-02 150258" src="https://github.com/user-attachments/assets/1bd985fa-7d12-4a0d-b7e1-c5dabc0deaf7" />


```sql
SELECT 
    c.cust_name,
    c.city,        -- customer city, keep as 'city'
    c.grade,
    s.name AS Salesman,
    s.city         -- salesman city, keep as 'city'
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="893" height="776" alt="image" src="https://github.com/user-attachments/assets/4ed89ab0-71a1-43e2-bc72-b59d03a85655" />


**Question 2**
---
<img width="1473" height="758" alt="Screenshot 2025-10-02 150314" src="https://github.com/user-attachments/assets/5b0c9bcc-ed3c-4935-88a9-c3b48b377ed7" />


```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id;
```

**Output:**

<img width="917" height="646" alt="image" src="https://github.com/user-attachments/assets/9f38d419-820e-429b-a2f8-5149b6267594" />


**Question 3**
---
<img width="1428" height="800" alt="Screenshot 2025-10-02 150327" src="https://github.com/user-attachments/assets/af9a1fec-b187-43e4-99f3-3201c6c2fd79" />


```sql
SELECT 
    s.name AS "Salesman",
    c.cust_name AS "cust_name",
    s.city AS "city"
FROM salesman s
JOIN customer c 
    ON s.city = c.city;
```

**Output:**

<img width="900" height="738" alt="image" src="https://github.com/user-attachments/assets/236b5d9e-77eb-4d21-9892-d8158e031146" />


**Question 4**
---
<img width="1460" height="760" alt="Screenshot 2025-10-02 150338" src="https://github.com/user-attachments/assets/388d43ec-10e5-41ec-97af-9ef1ab5e8fac" />


```sql
SELECT 
    p.date_of_birth,
    a.appointment_id,
    a.patient_id,
    a.doctor_id,
    a.appointment_date
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';

```

**Output:**

<img width="926" height="536" alt="image" src="https://github.com/user-attachments/assets/eeb88614-1380-4656-a986-938197a7da35" />


**Question 5**
---
<img width="1474" height="435" alt="Screenshot 2025-10-02 150347" src="https://github.com/user-attachments/assets/672e8886-c916-417a-9050-c8b3a3d44b19" />


```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM customer c
LEFT JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE c.grade <= 100;

```

**Output:**

<img width="917" height="658" alt="image" src="https://github.com/user-attachments/assets/c19ee104-0805-473a-a603-de15307fac11" />

**Question 6**
---
<img width="1502" height="755" alt="Screenshot 2025-10-02 150356" src="https://github.com/user-attachments/assets/412a1d50-4002-4e3a-894e-0a33e5233d24" />


```sql
SELECT 
    patient_id,
    first_name,
    last_name,
    date_of_birth,
    admission_date,
    discharge_date,
    doctor_id
FROM 
    patients
WHERE 
    first_name = 'Alice';
```

**Output:**

<img width="922" height="525" alt="image" src="https://github.com/user-attachments/assets/37b2a6a2-ef17-41f3-b7be-6af48ce4397f" />


**Question 7**
---
<img width="1465" height="814" alt="Screenshot 2025-10-02 150411" src="https://github.com/user-attachments/assets/9cb30d1c-fda1-4423-abae-44d2aa5ddd2f" />


```sql
SELECT 
    c.cust_name,
    c.city,
    COALESCE(c.grade, 100) AS grade,
    s.name AS Salesman,
    s.city
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    COALESCE(c.grade, 100) < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="914" height="806" alt="image" src="https://github.com/user-attachments/assets/044f3d21-68e0-4d02-a69c-5a152decbd1f" />


**Question 8**
---
<img width="1467" height="762" alt="Screenshot 2025-10-02 150424" src="https://github.com/user-attachments/assets/18673426-c794-46af-84bc-493a97e77dd6" />


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**
<img width="899" height="757" alt="image" src="https://github.com/user-attachments/assets/5780d56f-bdfa-4506-895e-fca8549f8925" />


**Question 9**
---
<img width="1495" height="400" alt="Screenshot 2025-10-02 150434" src="https://github.com/user-attachments/assets/47ced2d3-3d57-4a3f-87d4-be4b5a37e2db" />


```sql
SELECT s.name
FROM salesman s
LEFT JOIN customer c
    ON s.salesman_id = c.salesman_id
WHERE c.city = 'New York';
```

**Output:**

<img width="570" height="410" alt="image" src="https://github.com/user-attachments/assets/37a09303-0af7-4950-b049-2504a771360b" />


**Question 10**
---
<img width="1456" height="804" alt="Screenshot 2025-10-02 150447" src="https://github.com/user-attachments/assets/6866b86d-1993-4b64-a184-67eb6e650b04" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s 
    ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="905" height="802" alt="image" src="https://github.com/user-attachments/assets/ce97d06b-cf44-43c1-9221-ac0fa1522a47" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
