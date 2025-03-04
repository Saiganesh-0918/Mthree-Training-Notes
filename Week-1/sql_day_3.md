# SQL Day 3

## Primary Key
A **Primary Key** is a unique identifier for a table. It ensures that no duplicate values exist in the column.

```sql
CREATE TABLE table_name (
   Column1 INT PRIMARY KEY,
   Column2 VARCHAR(50)
);
```

## Foreign Key
A **Foreign Key** establishes a relationship between two tables by referencing the primary key of another table.

```sql
CREATE TABLE table1 (
   Column1 INT PRIMARY KEY,
   Column2 VARCHAR(50)
);

CREATE TABLE table2 (
   Column1 INT,
   Column2 VARCHAR(50),
   Column3 INT,
   FOREIGN KEY (Column3) REFERENCES table1(Column1)
);
```

## Example: Primary Key & Foreign Key
```sql
CREATE TABLE courses (
   course_id INT PRIMARY KEY,
   course_name VARCHAR(100),
   credits INT
);

CREATE TABLE students (
   stud_id INT PRIMARY KEY,
   first_name VARCHAR(100),
   last_name VARCHAR(100),
   email VARCHAR(100)
);

CREATE TABLE enrollments (
   enrollment_id INT PRIMARY KEY,
   stud_id INT,
   course_id INT,
   enroll_date DATE,
   FOREIGN KEY (stud_id) REFERENCES students(stud_id),
   FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

## Entity Relationship (ER) Diagram
- A visual representation of table relationships.
- Includes **Entities**, **Weak Entities**, **Strong Entities**, and **Recursive Entities**.
- Relationships: **One-to-Many, Many-to-One, Many-to-Many**.

### Cardinality
- Defines relationships between entities in ER diagrams.
- Types: **One-to-One, One-to-Many, Many-to-One, Many-to-Many**.

## Normalization
A process to **organize data and remove redundancy**.

### Types of Normalization:
1. **1NF (First Normal Form)** - Each column should have unique and atomic values.
2. **2NF (Second Normal Form)** - Removes **partial dependencies**.
3. **3NF (Third Normal Form)** - Removes **transitive dependencies**.

## SQL Delimiter
Used when creating stored procedures.

## SQL Procedure
A **stored procedure** is a reusable function in SQL.

```sql
DELIMITER //
CREATE PROCEDURE procedure_name (
   Column1 DATATYPE,
   Column2 DATATYPE
)
BEGIN
   -- SQL Statements
   SELECT * FROM table_name;
END //
DELIMITER ;
```

## Example: Stored Procedure for Student Insertion
```sql
DELIMITER //
CREATE PROCEDURE sp_insert_student (
    IN p_first_name VARCHAR(50),
    IN p_last_name VARCHAR(50),
    IN p_email VARCHAR(100)
)
BEGIN
    INSERT INTO students (first_name, last_name, email, enrollment_date)
    VALUES (p_first_name, p_last_name, p_email, CURDATE());
    SELECT LAST_INSERT_ID() AS student_id;
END //
DELIMITER ;

CALL sp_insert_student('John', 'Doe', 'john.doe@email.com');
```

## SQL Anomalies & ACID Properties
- **ACID Properties** ensure database transactions are processed reliably:
  - **Atomicity**: Ensures all operations are completed or none at all.
  - **Consistency**: Maintains database integrity before and after transactions.
  - **Isolation**: Transactions do not interfere with each other.
  - **Durability**: Ensures data is permanently stored.

## Practice Queries:

### Query to Display Employees with Salary > 25000
```sql
SELECT e.ename FROM employee e
INNER JOIN salary s ON e.eid = s.eid
WHERE s.sal > 25000;
```

### Query to Display Employees Working in the Same Location
```sql
SELECT e.ename, l.loc
FROM employee e
JOIN location l ON e.eid = l.eid
WHERE l.loc IN (
    SELECT loc FROM location
    GROUP BY loc
    HAVING COUNT(eid) > 1
)
ORDER BY l.loc;
```

## Summary:
- Learned about **Primary Key & Foreign Key**.
- Explored **ER Diagrams & Cardinality**.
- Understood **Normalization (1NF, 2NF, 3NF)**.
- Worked on **Stored Procedures & Delimiters**.
- Practiced SQL queries related to **ACID Properties & Anomalies**.
