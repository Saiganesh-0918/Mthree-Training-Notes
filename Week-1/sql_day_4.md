# SQL Day 4

## CONCAT Function
The `CONCAT` function in SQL is used to combine two or more strings into one.

### Example:
```sql
SELECT CONCAT('Hello', ' ', 'World') AS greeting;
```

### Working Example with Table:
```sql
CREATE TABLE source_employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2),
    department VARCHAR(50)
);

INSERT INTO source_employees VALUES 
(1, 'John Smith', 50000, 'IT'),
(2, 'Sarah Johnson', 60000, 'HR'),
(3, 'Michael Brown', 55000, 'IT');

SELECT CONCAT(
    'INSERT INTO employees (emp_id, name, salary, department) VALUES (',
    emp_id, ', ', QUOTE(name), ', ', salary, ', ', QUOTE(department), ');'
) AS insert_statement FROM source_employees;
```

## Indexing in SQL
An **Index** helps in retrieving records faster, similar to a book index.

### Example:
```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    name VARCHAR(100),
    price DECIMAL(10,2),
    category VARCHAR(50),
    INDEX idx_category (category)
);
```

## ON DELETE CASCADE & ON UPDATE CASCADE
- **ON DELETE CASCADE**: Deletes child table records when the parent record is deleted.
- **ON UPDATE CASCADE**: Updates child records when the parent table primary key is updated.

## Triggers in SQL
Triggers are **automated actions** that occur before or after `INSERT`, `UPDATE`, or `DELETE` operations.

### Example Query:
```sql
SELECT e.name,
       COALESCE(d.department_name, 'No Department') AS department,
       e.salary,
       CASE 
           WHEN d.department_id IS NULL THEN 'Unassigned'
           WHEN e.salary > 55000 THEN 'High Paid'
           ELSE 'Standard Pay'
       END AS status
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id;
```

## Introduction to Git & GitHub
### Steps to Get Started:
1. **Download Git Bash**: [Git Bash Download](https://git-scm.com/downloads/win)
2. **Create a GitHub Account**
3. **Set Up Git User Information**
   ```sh
   git config --global user.name "Your Name"
   git config --global user.email "youremail@example.com"
   ```
4. **Basic Git Commands:**
   ```sh
   mkdir projectname
   cd projectname
   git init
   echo "Hello Git" > file.txt
   git add file.txt
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/projectname.git
   git push -u origin main
   ```

## Summary:
- Learned **CONCAT function** for string manipulation.
- Explored **Indexing** for optimizing searches.
- Worked on **Triggers** for automatic operations.
- Understood **ON DELETE CASCADE & ON UPDATE CASCADE**.
- Hands-on introduction to **Git & GitHub commands**.
