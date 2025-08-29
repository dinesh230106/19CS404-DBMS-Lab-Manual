## (DINESH KUMAR A,212223060057) SLOT-4P4-1
# ER Diagram Workshop – Submission Templatr 

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

![ER Diagram](https://github.com/user-attachments/assets/ece76bb2-0f81-4665-bd6c-d45658e53f3c)


### Entities and Attributes

| **Entity**            | **Attributes (PK, FK)**                                                                                                   | **Notes**                                                            |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Admin**             | User\_Name (PK), Password                                                                                                 | Admin manages the website.                                           |
| **Gym Member**        | Member\_ID (PK), First\_Name, Last\_Name, User\_Name, Password, Email\_ID, Phone\_Number, Age, Address (Street, City)     | A person who uses the system for gym-related activities.             |
| **Instructor**        | Instructor\_ID (PK), First\_Name, Last\_Name, User\_Name, Password, Email\_ID, Phone\_Number, Age, Address (Street, City) | Manages exercises, diet plans, and classes.                          |
| **Exercise**          | Exercise\_ID (PK), Exercise\_Types                                                                                        | Different types of workouts/exercises.                               |
| **Diet Plan**         | DietPlan\_ID (PK), Diet\_Types                                                                                            | Diet plans categorized by types.                                     |
| **Classes**           | Class\_ID (PK), Cost, Date, Timing                                                                                        | Gym classes that members can take.                                   |
| **Gym Buddy Website** | (No explicit attributes shown)                                                                                            | Acts as a platform entity between users (admin, member, instructor). |


### Relationships and Constraints

| **Relationship**                            | **Cardinality** | **Participation**          | **Notes**                                                                     |
| ------------------------------------------- | --------------- | -------------------------- | ----------------------------------------------------------------------------- |
| **Admin – Manage – Gym Buddy Website**      | 1 : 1           | Total (Admin must manage)  | Admin controls the website.                                                   |
| **Gym Member – Used – Gym Buddy Website**   | M : 1           | Partial (members use site) | Members interact with website.                                                |
| **Instructor – Manage – Gym Buddy Website** | M : 1           | Partial                    | Instructors also interact via website.                                        |
| **Gym Member – View – Exercise**            | M : M           | Partial                    | Members can view many exercises, and exercises can be viewed by many members. |
| **Instructor – Manage – Exercise**          | 1 : M           | Total on Exercise          | Instructors create/manage exercises.                                          |
| **Gym Member – View – Diet Plan**           | M : M           | Partial                    | Members can view many diet plans.                                             |
| **Instructor – Manage – Diet Plan**         | 1 : M           | Total on Diet Plan         | Instructors manage diet plans.                                                |
| **Gym Member – Take Classes – Classes**     | M : 1           | Partial                    | A member can take many classes, each class can have many members.             |
| **Instructor – Assign – Classes**           | M : 1           | Total on Instructor        | Instructors are assigned to classes.                                          |


### Assumptions
- Each Gym Member and Instructor has unique login credentials (User Name, Password).

- A Diet Plan is always created/managed by an Instructor (not directly by a member).

- Classes are scheduled by instructors and attended by members; each class must have at least one instructor assigned.

- Exercises can exist independently, but usually managed by instructors.

The Gym Buddy Website is more of a conceptual entity representing the system, not a data table.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:

![ER Diagram2](https://github.com/user-attachments/assets/128778b9-3147-4d3d-9144-eb392b907340)


### Entities and Attributes

| Entity                                | Attributes (PK, FK)                                                          | Notes                                                          |
| ------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------- |
| **Books**                             | **Book\_ID (PK)**, Title, Author, Price, Available                           | Represents library books.                                      |
| **Publisher**                         | **Pub\_ID (PK)**, Name, Address                                              | Publishers of books.                                           |
| **Member**                            | **Member\_ID (PK)**, Name, Address, Member\_Type, Member\_Date, Expiry\_Date | Library members who borrow books.                              |
| **Borrowed\_By** (Associative Entity) | **Book\_ID (FK)**, **Member\_ID (FK)**, Issue, Due\_Date, Return\_Date       | Relationship entity to track which member borrowed which book. |


### Relationships and Constraints

| Relationship                        | Cardinality | Participation                        | Notes                                                                                                   |
| ----------------------------------- | ----------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| **Published\_By (Books–Publisher)** | M : 1       | Total on Books, Partial on Publisher | Each book must be published by exactly one publisher, a publisher can publish many books.               |
| **Borrowed\_By (Books–Member)**     | M : M       | Partial on both sides                | A member can borrow many books, and a book can be borrowed by many members over time (history tracked). |


### Assumptions
- Each book has exactly one publisher.

- A member can borrow multiple books at a time.

- The Borrowed_By entity is used to store transaction details (issue date, due date, return date).

- A book’s Available attribute indicates whether it can be borrowed.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

![Untitled Diagram](https://github.com/user-attachments/assets/226c37ae-112d-4f6c-be93-ac7d8e93231e)


### Entities and Attributes

| Entity            | Attributes (PK, FK)                                                                                     | Notes                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Admin**         | admin\_id (PK), admin\_Fname, admin\_Mname, admin\_Lname, admin\_pass                                   | Manages and checks rooms.                               |
| **Receptionist**  | rec\_id (PK), rec\_Fname, rec\_Mname, (other attributes)                                                | Confirms customer reservations and checks rooms.        |
| **Customer**      | cust\_id (PK), cust\_Fname, cust\_Mname, cust\_Lname, cust\_address, cust\_number                       | Makes reservations and creates transactions.            |
| **Room**          | room\_id (PK), (attributes like availability, capacity)                                                 | Represents physical hotel rooms, linked to room types.  |
| **Room\_type**    | room\_code (PK), room\_name                                                                             | Defines category/type of room (e.g., Deluxe, Standard). |
| **Transaction**   | trans\_id (PK), cust\_id (FK), rec\_id (FK), start\_date, end\_date, total\_payment, payment\_type (FK) | Records booking/payment details for customers.          |
| **Payment\_type** | payment\_type\_id (PK), payment\_name                                                                   | Stores different payment methods (cash, card, online).  |


### Relationships and Constraints

| Relationship                           | Cardinality | Participation                                  | Notes                                           |
| -------------------------------------- | ----------- | ---------------------------------------------- | ----------------------------------------------- |
| **Admin – Checks – Room**              | 1 : N       | Total on Admin, Partial on Room                | Admin checks multiple rooms.                    |
| **Receptionist – Checks – Room**       | 1 : N       | Total on Receptionist, Partial on Room         | Receptionist verifies/checks room availability. |
| **Receptionist – Confirms – Customer** | 1 : N       | Total on Receptionist, Partial on Customer     | Receptionist confirms bookings for customers.   |
| **Customer – Creates – Transaction**   | 1 : N       | Total on Customer, Partial on Transaction      | A customer can create multiple transactions.    |
| **Room – has – Room\_type**            | N : 1       | Total on Room, Partial on Room\_type           | Each room must belong to a room type.           |
| **Transaction – has – Payment\_type**  | N : 1       | Total on Transaction, Partial on Payment\_type | Every transaction requires a payment type.      |

### Assumptions
- Each Admin and Receptionist can check multiple rooms, but each room is checked by only one staff member at a time.

- A Customer must exist before making a Transaction.

- Transaction includes booking dates (start_date, end_date) and payment info.

- Room_type determines room classification; attributes like price and capacity can be included here.

Payment_type is standardized (e.g., Cash, Credit Card, UPI).
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
