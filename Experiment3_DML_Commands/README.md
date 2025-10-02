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

<img width="1416" height="640" alt="Screenshot 2025-10-02 141515" src="https://github.com/user-attachments/assets/ef8fa5b2-ebb5-4b96-9080-4ce9e026a973" />

```sql
UPDATE employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```

**Output:**

<img width="881" height="387" alt="image" src="https://github.com/user-attachments/assets/bfa6a5a9-ac2e-46a5-b7cf-f2a7fb52e965" />


**Question 2**
---

<img width="1410" height="585" alt="Screenshot 2025-10-02 141535" src="https://github.com/user-attachments/assets/d664494a-0a58-45e4-9ce7-3fc0dd7fbbd0" />

```sql
UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 1.3 AS INT)
WHERE category = 'Food'
  AND quantity < (0.5 * reorder_lvl);
```

**Output:**

<img width="880" height="527" alt="image" src="https://github.com/user-attachments/assets/3695c103-5fec-4960-a248-3141bda2f6b8" />


**Question 3**
---

<img width="1404" height="632" alt="Screenshot 2025-10-02 141548" src="https://github.com/user-attachments/assets/f2685467-9899-4891-8c43-807b2576db7d" />

```sql
-- Paste your SQL code below for Question 3UPDATE employees
SET salary = salary * 2
WHERE department_id = 20
  AND job_id LIKE '%MAN';
```

**Output:**
<img width="890" height="458" alt="image" src="https://github.com/user-attachments/assets/1f2c4e44-bbc6-4d7e-9af7-5e726ec9ce0d" />


**Question 4**
---

<img width="1422" height="509" alt="Screenshot 2025-10-02 141601" src="https://github.com/user-attachments/assets/548c6c34-84e8-4769-8bd8-b077209712ce" />

```sql
UPDATE sales
SET total_sell_price = quantity * sell_price
WHERE product_id = 10;
```

**Output:**

<img width="883" height="611" alt="image" src="https://github.com/user-attachments/assets/ad61ae7f-f94f-4986-95f2-3c28a3362c11" />


**Question 5**
---
<img width="916" height="285" alt="Screenshot 2025-10-02 141609" src="https://github.com/user-attachments/assets/584d7451-3709-4439-b28a-bdba8d0d3f07" />

```sql
UPDATE products
SET availability = availability*2
WHERE product_id =1;
```

**Output:**

<img width="888" height="346" alt="image" src="https://github.com/user-attachments/assets/50c83858-dcbc-49f3-abf0-316060910c08" />


**Question 6**
---

<img width="1405" height="387" alt="Screenshot 2025-10-02 141621" src="https://github.com/user-attachments/assets/7ef75ec5-feff-4ce5-80ad-c90f84121806" />

```sql
DELETE FROM customer
WHERE cust_country = 'India'
  AND cust_city <> 'Chennai';
```

**Output:**

<img width="1230" height="813" alt="image" src="https://github.com/user-attachments/assets/147b4c7b-6d21-4288-a0a4-b3b0b3bcd0d4" />


**Question 7**
---
<img width="1436" height="635" alt="Screenshot 2025-10-02 141637" src="https://github.com/user-attachments/assets/003580e4-a83d-4154-8aa4-be03b9b41172" />


```sql
DELETE FROM customer 
WHERE WORKING_AREA ='New York';
```

**Output:**

<img width="1238" height="784" alt="image" src="https://github.com/user-attachments/assets/064b869f-8a8d-44c8-b8aa-776245233a60" />


**Question 8**

<img width="1184" height="500" alt="Screenshot 2025-10-02 141646" src="https://github.com/user-attachments/assets/81f3db84-a2d9-4c2f-9815-2719034f168d" />

```sql
DELETE FROM surgeries
WHERE surgery_id=3;
```

**Output:**

<img width="906" height="499" alt="image" src="https://github.com/user-attachments/assets/f3ee663b-7495-4778-a7a2-648236b397a0" />


**Question 9**
---
<img width="1427" height="522" alt="Screenshot 2025-10-02 141656" src="https://github.com/user-attachments/assets/e3cf077e-29cb-4393-a3b3-0b0ed80c2b78" />


```sql
DELETE FROM customer
WHERE cust_country NOT IN ('India', 'USA');
```

**Output:**

<img width="890" height="636" alt="image" src="https://github.com/user-attachments/assets/ad90dd6b-4d80-4359-8e7f-976223e66fcb" />


**Question 10**
---
<img width="1427" height="522" alt="Screenshot 2025-10-02 141656" src="https://github.com/user-attachments/assets/11a4906d-fb6e-457c-a497-caa4e6a92bf2" />


```sql
DELETE FROM customer
WHERE grade = 3
  AND cust_name LIKE '%BBB%'
  AND payment_amt > 2000;
```

**Output:**

<img width="945" height="579" alt="image" src="https://github.com/user-attachments/assets/606e877c-28a3-4306-a7e7-4df2aeee7823" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
