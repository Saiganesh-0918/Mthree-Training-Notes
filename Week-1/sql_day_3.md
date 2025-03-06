SQL(DAY-3)

## PRIMARY KEY  
A primary key in SQL refers to a column or set of columns in a table that is unique and does not allow duplicates. A table can have at most one primary key. By default, the primary key will be the first column.
```sql
CREATE TABLE table_name(
  Column1 INT PRIMARY KEY,
  Column2 VARCHAR(50)
);
```

## FOREIGN KEY  
A foreign key in SQL refers to a column or set of columns in a table and builds a relationship between two tables by referencing a column from another table. A table can have more than one foreign key.
```sql
CREATE TABLE table1_name(
  Column1 INT PRIMARY KEY,
  Column2 VARCHAR(50)
);

CREATE TABLE table2_name(
  Column1 INT,
  Column2 VARCHAR(50),
  Column3 INT,
  FOREIGN KEY(Column3) REFERENCES table1(Column1)
);
```

## ENTITY RELATIONSHIP  
An entity-relationship diagram (ERD) visually represents relationships between tables. It includes:
- **Entities** (Rectangle)
- **Attributes** (Ellipse)
- **Relationships** (Diamond)
- **Weak Entities** (Double Rectangle)

## CARDINALITY  
Cardinality in SQL represents the relationships in entity-relationship diagrams. It can be:
- One-to-One
- One-to-Many
- Many-to-One
- Many-to-Many

## NORMALIZATION  
Normalization is the process of organizing data in a database to reduce redundancy and maintain consistency.

### Types of Normalization:
1. **1NF (First Normal Form):** Each column must be unique and separate.
2. **2NF (Second Normal Form):** No partial dependencies; all columns must depend on the primary key.
3. **3NF (Third Normal Form):** No transitive dependencies.

Normalization helps improve data quality, consistency, efficiency, and simplifies database design.

## DELIMITER  
A delimiter in SQL is used when creating stored procedures.

## PROCEDURE  
A procedure in SQL works like a function in other programming languages. It is used for executing the same query repeatedly. Parameters can be passed while creating the procedure.
```sql
DELIMITER //
CREATE PROCEDURE procedure_name(
  Column1 DATATYPE,
  Column2 DATATYPE
)
BEGIN
  -- SQL Statements
  SELECT * FROM table_name;
END //
DELIMITER ;
```

### Example - Insert Procedure:
```sql
CREATE PROCEDURE sp_insert_student(
    IN p_first_name VARCHAR(50),
    IN p_last_name VARCHAR(50),
    IN p_email VARCHAR(100)
)
BEGIN
    INSERT INTO students (first_name, last_name, email, enrollment_date)
    VALUES (p_first_name, p_last_name, p_email, CURDATE());
    
    SELECT LAST_INSERT_ID() AS student_id;
END;
```

### Example - Update Procedure:
```sql
CREATE PROCEDURE sp_update_gpa(
    IN p_student_id INT,
    IN p_new_gpa DECIMAL(3,2)
)
BEGIN
    DECLARE current_gpa DECIMAL(3,2);
    
    SELECT gpa INTO current_gpa
    FROM students
    WHERE student_id = p_student_id;
    
    IF p_new_gpa > current_gpa THEN 
        UPDATE students
        SET gpa = ROUND(p_new_gpa), last_updated = NOW()
        WHERE student_id = p_student_id;
        
        SELECT 'GPA IMPROVED' AS Message;
    ELSE 
        SELECT 'NO CHANGE' AS Message;
    END IF;
END;
```

## ACID PROPERTIES  
ACID stands for:
- **Atomicity:** Ensures all operations in a transaction are completed or none are executed.
- **Consistency:** Guarantees that a database moves from one valid state to another.
- **Isolation:** Ensures that multiple transactions occur independently without interference.
- **Durability:** Ensures that committed transactions are permanently stored.

### Example - Query to Retrieve Employees with Salary Greater than 25000:
```sql
SELECT e.ename
FROM employee e
INNER JOIN salary s ON e.eid = s.eid
WHERE s.sal > 25000;
```

### Example - Query to Display Employees Working in the Same Location:
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

In the afternoon session, we revised the morning topics, discussed doubts in breakout rooms, and learned about anomalies. Additionally, we solved SQL problems to strengthen our understanding.


## Summary:
- Learned about **Primary Key & Foreign Key**.
- Explored **ER Diagrams & Cardinality**.
- Understood **Normalization (1NF, 2NF, 3NF)**.
- Worked on **Stored Procedures & Delimiters**.
- Practiced SQL queries related to **ACID Properties & Anomalies**.
