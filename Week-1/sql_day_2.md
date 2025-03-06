SQL(Day-2)

## JOINS  
Joins are the keyword used to combine two or more tables in a database.

### Types of Joins in SQL:
1. **Left Join:** Returns all the columns in the left table and along with that, matching columns in the right table.
   ```sql
   SELECT column_name FROM table1 LEFT JOIN table2 ON table1.column_name = table2.column_name;
   ```
2. **Right Join:** Returns all the columns in the right table and along with that, matching columns in the left table.
   ```sql
   SELECT column_name FROM table1 RIGHT JOIN table2 ON table1.column_name = table2.column_name;
   ```
3. **Full Join:** Returns all the columns in both right and left tables.
   ```sql
   SELECT column_name FROM table1 FULL JOIN table2 ON table1.column_name = table2.column_name;
   ```
4. **Inner Join:** Returns only the columns and records that match in both tables.
   ```sql
   SELECT column_name FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;
   ```

## UNIONS  
Union is the operator used to combine the result of two or more selected statements. It returns only unique values and does not allow duplicates.
```sql
SELECT column_name FROM table1 UNION SELECT column_name FROM table2;
```

### UNION ALL  
Union All works the same as Union but allows duplicates.
```sql
SELECT column_name FROM table1 UNION ALL SELECT column_name FROM table2;
```

## GROUP BY  
The `GROUP BY` keyword in SQL groups the rows that have the same values into summary rows.

## RANK and DENSE_RANK  
- **Rank:** Assigns a rank for each row, skipping the next number if two consecutive rows have the same value.
- **Dense_Rank:** Works the same as `RANK`, but it does not skip numbers.

## BITWISE OPERATIONS  
Used to check whether the permission is given or not. We can perform AND, OR, XOR, Left Shift, and Right Shift.

## EXISTS  
The `EXISTS` operator checks whether there is any existence or not. It returns `TRUE` if the subquery returns one or more records.

## LAG  
`LAG` compares the previous row and current row.

## DATE_FORMAT  
Formats the date as per the required format of the project.

## CASE  
Acts like an `IF-ELSE` condition, returning values based on conditions.

## PARTITION BY  
Partitions rows in a table and groups them. Useful for ranking functions.

## ANY  
Allows comparison between single column values or a set of column values. Returns a boolean value.

### Examples:
```sql
/* Performing Bitwise AND operation */
SELECT username, permission_flags & 4 AS has_read_permission,
CASE WHEN permission_flags & 4 > 0 THEN 'Yes' ELSE 'No' END AS can_read
FROM permissions;

/* Left join example */
SELECT e.name AS Ename, e.department, m.Name AS ManagerName
FROM employees e
LEFT JOIN employees m ON e.managerid = m.empId;

/* Group By, Lag, and Date_Format */
SELECT DATE_FORMAT(orderdate, '%Y-%m') AS yearmonth, COUNT(*) AS totalorders,
SUM(totalamount) AS totalsales, AVG(totalamount) AS avgordervalue,
(SUM(totalAmount)-LAG(SUM(totalAmount)) OVER (ORDER BY DATE_FORMAT(orderdate, '%Y-%m')))/
(LAG(SUM(totalAmount)) OVER (ORDER BY DATE_FORMAT(orderdate, '%Y-%m'))) *100 AS MoMGrowth
FROM orders
GROUP BY DATE_FORMAT(orderdate, '%Y-%m')
ORDER BY yearmonth;
```

In the afternoon session, we solved a few SQL questions on LeetCode, which was very helpful to gain hands-on experience in SQL. Finally, I learned medium-level SQL topics and solved LeetCode problems. Today's session topics were new to me, but I understood them easily.


## Summary:
- Explored different types of joins.
- Practiced functions like `Rank`, `Dense Rank`, `Partition By`, and `Bitwise Operations`.
- Worked on SQL problems from LeetCode.
- Strengthened medium-level SQL concepts and hands-on problem-solving.

