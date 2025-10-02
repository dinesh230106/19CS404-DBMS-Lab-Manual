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
--

<img width="1301" height="558" alt="Screenshot 2025-10-02 144002" src="https://github.com/user-attachments/assets/d2d9e380-8b68-4556-805d-460fec86d778" />

```sql
SELECT DoctorID, 
       COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**

<img width="878" height="669" alt="image" src="https://github.com/user-attachments/assets/b80e1ab7-bfa6-4468-b003-672dae38fc3e" />


**Question 2**
---
<img width="1275" height="550" alt="Screenshot 2025-10-02 144011" src="https://github.com/user-attachments/assets/8ab8605a-aea0-4120-b45a-ee4373dbdc54" />


```sql
SELECT DoctorID, 
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID;
```

**Output:**

<img width="886" height="682" alt="image" src="https://github.com/user-attachments/assets/7269dd6c-66f4-4cea-8dd0-0f651d70ed67" />


**Question 3**
---
<img width="1386" height="474" alt="Screenshot 2025-10-02 144020" src="https://github.com/user-attachments/assets/48049c9a-d101-497e-a70a-5120fa441e1f" />


```sql
SELECT Gender, 
       COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="873" height="483" alt="image" src="https://github.com/user-attachments/assets/9dabc2e7-0171-4e84-be73-61a112781d17" />


**Question 4**
---
<img width="1352" height="484" alt="Screenshot 2025-10-02 144029" src="https://github.com/user-attachments/assets/5a17f8d3-277b-47be-9aff-05bc9ad35c94" />


```sql
SELECT AVG(LENGTH(name)) AS avg_name_length
FROM customer
WHERE city = 'Chennai';
```

**Output:**

<img width="883" height="473" alt="image" src="https://github.com/user-attachments/assets/cc343faf-90e2-4327-ab4d-20cd7904f224" />


**Question 5**
---
<img width="1143" height="556" alt="Screenshot 2025-10-02 144035" src="https://github.com/user-attachments/assets/7479313a-4555-4f9a-9392-61d578143d7f" />


```sql
SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';
```

**Output:**

<img width="894" height="454" alt="image" src="https://github.com/user-attachments/assets/4eddd7c4-46bc-4c72-9ab4-eb90842958ca" />


**Question 6**
---
<img width="1265" height="535" alt="Screenshot 2025-10-02 144043" src="https://github.com/user-attachments/assets/c04bc13e-46c3-48b1-9651-387577aa9b30" />


```sql
SELECT MIN(purch_amt) AS MINIMUM
FROM orders;
```

**Output:**
<img width="888" height="477" alt="image" src="https://github.com/user-attachments/assets/151d30d6-5a26-40be-87cb-ef6b5f342e3f" />


**Question 7**
---
<img width="1420" height="553" alt="Screenshot 2025-10-02 144052" src="https://github.com/user-attachments/assets/737ef59d-cd36-4ae6-9dfd-91529cfd4157" />


```sql
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="879" height="444" alt="image" src="https://github.com/user-attachments/assets/4b5469a7-248c-46d1-9534-011a46f5ad87" />


**Question 8**
---
<img width="1415" height="495" alt="Screenshot 2025-10-02 144102" src="https://github.com/user-attachments/assets/05a9de38-fccc-4cf7-ac3e-dc710af4e24e" />


```sql
SELECT (age/5)*5 AS age_group,
       MIN(age) 
FROM customer1
GROUP BY (age/5)*5
HAVING MIN(age) < 25;
```

**Output:**

<img width="885" height="424" alt="image" src="https://github.com/user-attachments/assets/5a1b7aee-e87c-4125-9e35-4cd6c619430b" />


**Question 9**
---
<img width="1421" height="513" alt="Screenshot 2025-10-02 144111" src="https://github.com/user-attachments/assets/0c073c6e-5122-4d9e-993b-43a64e0fb05d" />


```sql
SELECT jdate,
       MAX(workhour)
FROM employee1
GROUP BY jdate
HAVING MAX(workhour) > 12;
```

**Output:**

<img width="860" height="503" alt="image" src="https://github.com/user-attachments/assets/e43d7874-616d-4fa0-9792-fbfd48237c81" />


**Question 10**
---
<img width="1428" height="575" alt="Screenshot 2025-10-02 144122" src="https://github.com/user-attachments/assets/5493c4ef-a7c9-42eb-a575-2be6996820b4" />


```sql
SELECT occupation,
       SUM(workhour)
FROM employee1
GROUP BY occupation
HAVING SUM(workhour) > 20;
```

**Output:**

<img width="862" height="553" alt="image" src="https://github.com/user-attachments/assets/fed42d9d-90e7-4731-9217-f4c2928c12f7" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
