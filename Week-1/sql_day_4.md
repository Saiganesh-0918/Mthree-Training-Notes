SQL(DAY-4)

## CONCAT  
The `CONCAT` function in SQL is used to combine two or more strings into a single string.

### Example:
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
(3, 'Michael Brown', 55000, 'IT'),
(4, 'Sai Ganesh', 70000, 'IT');

SELECT CONCAT(
    'INSERT INTO employees (emp_id, name, salary, department) VALUES (',
    emp_id, ', ', 
    QUOTE(name), ', ',
    salary, ', ',
    QUOTE(department), ');'
) AS insert_statement
FROM source_employees;
```

## INDEX  
An index in SQL improves the speed of data retrieval operations by avoiding full-table scans.

### Example:
```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    name VARCHAR(100),
    price DECIMAL(10,2),
    category VARCHAR(50),
    INDEX idx_category(category)
);
```

## ON DELETE CASCADE  
If a record in the parent table is deleted, the corresponding records in the child table will also be deleted.

## ON UPDATE CASCADE  
If the primary key in the parent table is updated, the foreign key in the child table will be automatically updated.

## TRIGGERS  
A trigger in SQL is an event-driven function that automatically executes before or after certain operations (INSERT, UPDATE, DELETE).

### Example - Left Join with Conditional Statements:
```sql
SELECT  
    e.name, 
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

---

## Introduction to Git and GitHub  
We were introduced to Git Bash and GitHub for version control and collaboration.

### Git Installation:
Download Git Bash from the official site: [Git SCM](https://git-scm.com/downloads/win)

### Git Configuration:
```bash
git config --global user.name "ABC"
git config --global user.email "ABC@gmail.com"
```

### Git Basic Commands:
```bash
# Create a new directory and navigate into it
mkdir projectname
cd projectname

# Initialize a new Git repository
git init

# Create a file and add text
echo "text" > filename.txt

# Stage the file for commit
git add filename.txt

# Check the status
git status

# Commit the changes
git commit -m "Adding the text"

# Rename the branch to 'main'
git branch -M main

# Add a remote repository
git remote add origin https://github.com/ABC/projectname.git

# Push the changes to GitHub
git push -u origin main
```

---

In the afternoon session, we revised the morning topics, resolved doubts in breakout rooms, and solved LeetCode problems to reinforce our SQL skills.

## Summary:
- Learned **CONCAT function** for string manipulation.
- Explored **Indexing** for optimizing searches.
- Worked on **Triggers** for automatic operations.
- Understood **ON DELETE CASCADE & ON UPDATE CASCADE**.
- Hands-on introduction to **Git & GitHub commands**.
