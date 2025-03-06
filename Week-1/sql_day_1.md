SQL(DAY-1)

## SQL - Structured Query Language  
Here the query means questions that are asked by the user to retrieve the data. Language is the word where we are responding back and what type of language it is.

### What is SQL?  
SQL is a structured Query language where we can store our data in an organized manner, i.e., in tables. Storing the data in rows and columns of the table. Performing the operations on the data as per the requirement.

In SQL all the operations are carried out using commands. In today's session, I have learned DDL and DML commands.

### DDL - Data Definition Language  
Data Definition Language is a type where we work on defining the data for our requirement. Apart from defining, we can perform the operations like altering and deleting the data.

The commands used in DDL are Create, Alter, Delete, Truncate.

### DML - Data Manipulation Language  
Data Manipulation Language is a type where we work on manipulating the data.

The commands used in DML are Insert, Update, Delete.

#### Syntax for creation of database in MySQL workbench:
```sql
Create database database_name;
```
#### To use the created database in MySQL workbench:
```sql
Use database_name;
```
#### Example:
```sql
/* To create database along with table */
Create database training;
Use training;
Create table trainee(
   id int,
   name varchar(200),
   address varchar(200),
   age int
);

/* To insert values into the table */
Insert into trainee values(1, 'ABCD', 'PUNE', 20);

/* To rename the name of table */
Rename table trainee to trainees;

/* Inserting values after rename */
Insert into trainees values(2, 'BCDE', 'DELHI', 21);
Insert into trainees values(3, 'CDEF', 'PUNJAB', 22);
Insert into trainees values(4, 'DEFG', 'AP', 23);

/* To print all the values in the table */
Select * from trainees;
```

In the afternoon session, we solved a few SQL questions on HackerRank which was very helpful to gain hands-on experience on SQL that we learned in the morning session.

1. Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.
2. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
3. Query all columns (attributes) for every row in the CITY table.
4. Query all columns for a city in CITY with the ID 1661.
5. Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

Additionally, I have learned shallow copy and deep copy. Along with that, I have learned how to create the temporary table from the existing table. Finally, I have acquired basic knowledge of SQL and it was a good session on day-1.


**Summary:**
- Gained a basic understanding of SQL commands.
- Hands-on practice with SQL queries using HackerRank.
- Good introductory session to SQL fundamentals.

