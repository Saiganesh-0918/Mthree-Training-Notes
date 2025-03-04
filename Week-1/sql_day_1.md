# SQL Day 1

## SQL - Structured Query Language
SQL is a structured query language used to store and retrieve data in an organized manner using tables (rows and columns). Operations on data are performed using SQL commands.

### Types of SQL Commands:
- **DDL (Data Definition Language)** - Used for defining and modifying database structure.
  - Commands: `CREATE`, `ALTER`, `DELETE`, `TRUNCATE`
- **DML (Data Manipulation Language)** - Used for manipulating data in tables.
  - Commands: `INSERT`, `UPDATE`, `DELETE`

### MySQL Workbench Commands:
```sql
-- Creating a database
CREATE DATABASE database_name;

-- Using the database
USE database_name;

-- Creating a table
CREATE TABLE trainee(
   id INT,
   name VARCHAR(200),
   address VARCHAR(200),
   age INT
);

-- Inserting values into the table
INSERT INTO trainee VALUES (1, 'ABCD', 'PUNE', 20);

-- Renaming the table
RENAME TABLE trainee TO trainees;

-- Inserting more values
INSERT INTO trainees VALUES (2, 'BCDE', 'DELHI', 21);
INSERT INTO trainees VALUES (3, 'CDEF', 'PUNJAB', 22);
INSERT INTO trainees VALUES (4, 'DEFG', 'AP', 23);

-- Selecting all records
SELECT * FROM trainees;
```

### SQL Queries Practiced on HackerRank:
1. Query all columns for all American cities in the CITY table where `population > 100000` (`CountryCode = 'USA'`).
2. Query the `NAME` field for American cities where `population > 120000` (`CountryCode = 'USA'`).
3. Query all columns for every row in the CITY table.
4. Query all columns for a city in CITY where `ID = 1661`.
5. Query all attributes of every Japanese city (`CountryCode = 'JPN'`).

### Additional Learnings:
- **Shallow Copy vs Deep Copy**
- **Creating a temporary table from an existing table**

**Summary:**
- Gained a basic understanding of SQL commands.
- Hands-on practice with SQL queries using HackerRank.
- Good introductory session to SQL fundamentals.

