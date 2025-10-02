# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

## program:

```

DECLARE
   num1 NUMBER := 50; 
   num2 NUMBER := 80;  
   greater NUMBER;    
BEGIN
   IF num1 > num2 THEN
      greater := num1;
   ELSE
      greater := num2;
   END IF;

   DBMS_OUTPUT.PUT_LINE('Greater number is: ' || greater);
END;
/
```

**Expected Output:**  
Greater number is: 80

## output:
<img width="1920" height="1080" alt="Screenshot (76)" src="https://github.com/user-attachments/assets/fa0f3587-78e1-431e-a92d-e747d43d3a3b" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

## program:
```

-- PL/SQL Program to Calculate Sum of First N Natural Numbers

DECLARE
   n NUMBER := 10;      -- Number up to which sum is calculated
   sum NUMBER := 0;     -- Variable to store sum
   i NUMBER := 1;       -- Loop counter
BEGIN
   -- Loop from 1 to n
   WHILE i <= n LOOP
      sum := sum + i;   -- Add current number to sum
      i := i + 1;       -- Increment counter
   END LOOP;

   -- Display the result
   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```
  

**Expected Output:**  
Sum of first 10 natural numbers is: 55

## output:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2e737a92-6fad-427b-be2f-c54337ef5c50" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

## program:
```
-- PL/SQL Program to Generate Fibonacci Series

DECLARE
   n NUMBER := 7;       -- Number of terms to generate
   a NUMBER := 0;       -- First term
   b NUMBER := 1;       -- Second term
   c NUMBER;            -- Next term
   i NUMBER := 3;       -- Loop counter starts from 3 because first two terms are already defined
BEGIN
   -- Print first two terms
   DBMS_OUTPUT.PUT(a || ', ' || b);

   -- Generate remaining terms
   WHILE i <= n LOOP
      c := a + b;                     -- Calculate next term
      DBMS_OUTPUT.PUT(', ' || c);     -- Display term
      a := b;                         -- Update a
      b := c;                         -- Update b
      i := i + 1;                     -- Increment counter
   END LOOP;

   DBMS_OUTPUT.NEW_LINE;              -- Move to new line after printing series
END;
/
```
**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

## output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fe154dbb-73af-4e6c-be56-3d5c05f6f111" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

## program:
```
-- PL/SQL Program to Display a Number and Its Reverse

DECLARE
   n NUMBER := 1535;      -- Original number
   reversed NUMBER := 0;  -- Variable to store reversed number
   remainder NUMBER;      -- Variable to store last digit
   temp NUMBER := n;      -- Temporary variable for manipulation
BEGIN
   -- Loop to reverse the number
   WHILE temp > 0 LOOP
      remainder := MOD(temp, 10);             -- Extract last digit
      reversed := (reversed * 10) + remainder;-- Add digit to reversed number
      temp := FLOOR(temp / 10);               -- Remove last digit
   END LOOP;

   -- Display original and reversed numbers
   DBMS_OUTPUT.PUT_LINE('Original number is: ' || n);
   DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || reversed);
END;
/

```
**Expected Output:**  
n = 1535  
Reversed number is 5351

## output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5cdfc4ad-5db2-49f9-9ba0-8b0a16b7bba9" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

## program:
```
-- PL/SQL Program to Find the Largest of Three Numbers

DECLARE
   a NUMBER := 10;  -- First number
   b NUMBER := 9;   -- Second number
   c NUMBER := 15;  -- Third number
   largest NUMBER;  -- Variable to store the largest number
BEGIN
   -- Compare numbers using IF-ELSIF-ELSE
   IF a >= b AND a >= c THEN
      largest := a;
   ELSIF b >= a AND b >= c THEN
      largest := b;
   ELSE
      largest := c;
   END IF;

   -- Display the numbers and the largest
   DBMS_OUTPUT.PUT_LINE('Numbers are: a = ' || a || ', b = ' || b || ', c = ' || c);
   DBMS_OUTPUT.PUT_LINE('Largest of three numbers is: ' || largest);
END;
/

```
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## output:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3d461488-4791-43ed-a883-95d69bbd3914" />

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

