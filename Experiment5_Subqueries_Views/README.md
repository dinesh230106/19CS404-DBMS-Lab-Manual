# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1321" height="583" alt="Screenshot 2025-10-02 145011" src="https://github.com/user-attachments/assets/8b1010f4-ac19-4bd1-833b-35e17af48ada" />


```sql
SELECT name
FROM customer
WHERE phone IN (
    SELECT phone
    FROM customer
    GROUP BY phone
    HAVING COUNT(*) = 1
);

```

**Output:**

<img width="909" height="549" alt="image" src="https://github.com/user-attachments/assets/3dc5d796-1d30-4abd-bf84-03a20f5d5c78" />


**Question 2**
---
<img width="1464" height="782" alt="Screenshot 2025-10-02 145029" src="https://github.com/user-attachments/assets/49c21b21-8253-4049-81b3-9815f65255c8" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**
<img width="924" height="555" alt="image" src="https://github.com/user-attachments/assets/0d72ab29-2ee1-4a37-951a-bb50c5bc9028" />


**Question 3**
---
<img width="1493" height="674" alt="Screenshot 2025-10-02 145100" src="https://github.com/user-attachments/assets/5e1b99a4-d94f-4532-a17f-68870c464b30" />


```sql
SELECT g.student_name, g.grade
FROM GRADES g
WHERE g.grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="911" height="524" alt="image" src="https://github.com/user-attachments/assets/92b72626-0ec2-42a5-8892-ba18b758be2f" />


**Question 4**
---
<img width="1483" height="678" alt="Screenshot 2025-10-02 145113" src="https://github.com/user-attachments/assets/66dcaf9e-ae57-4686-a87a-0b2f719c23f3" />


```sql
SELECT g.student_name, g.grade
FROM GRADES g
WHERE g.grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="921" height="543" alt="image" src="https://github.com/user-attachments/assets/2bd3d431-d0ae-4e8a-8b3d-07711304b33d" />


**Question 5**
---
<img width="1465" height="775" alt="Screenshot 2025-10-02 145126" src="https://github.com/user-attachments/assets/ba7bc72a-5995-4001-8195-a187596d53ec" />


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id 
    FROM salesman 
    WHERE name = 'Paul Adam'
);

```

**Output:**

<img width="935" height="525" alt="image" src="https://github.com/user-attachments/assets/05e99992-aa64-48fe-97a9-11af9f5fef84" />


**Question 6**
---
<img width="1478" height="704" alt="Screenshot 2025-10-02 145140" src="https://github.com/user-attachments/assets/46a911e6-9241-456d-a27c-1d5f1bf5436f" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;
```

**Output:**

<img width="902" height="560" alt="image" src="https://github.com/user-attachments/assets/67c4abd6-79a5-461e-ac5c-983fc596f332" />


**Question 7**
---
<img width="1484" height="807" alt="Screenshot 2025-10-02 145153" src="https://github.com/user-attachments/assets/5441a108-4ec8-42af-af66-5b3350b371bf" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM ORDERS o
INNER JOIN SALESMAN s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**
<img width="904" height="584" alt="image" src="https://github.com/user-attachments/assets/d9ff4f05-f003-4458-ac24-b1e035ea60d1" />


**Question 8**
---
<img width="1482" height="715" alt="Screenshot 2025-10-02 145206" src="https://github.com/user-attachments/assets/a8963576-6764-47e8-b8dc-740653109599" />


```sql
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);

```

**Output:**

<img width="923" height="629" alt="image" src="https://github.com/user-attachments/assets/7ee3bd24-2ac2-42df-812e-6fb27be593fc" />


**Question 9**
---
<img width="1480" height="638" alt="Screenshot 2025-10-02 145218" src="https://github.com/user-attachments/assets/e14f75d4-8b9b-4aef-b574-008559ad5114" />


```sql
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="922" height="540" alt="image" src="https://github.com/user-attachments/assets/a06f9312-d556-47c4-b274-e3e3765ded13" />


**Question 10**
---
<img width="1477" height="809" alt="Screenshot 2025-10-02 145232" src="https://github.com/user-attachments/assets/b4a2104e-1df0-4826-a266-477247d346de" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission) FROM salesman
);

```

**Output:**

<img width="927" height="580" alt="image" src="https://github.com/user-attachments/assets/d4c50ac2-5ea2-4774-8d14-a6d91813ae22" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
