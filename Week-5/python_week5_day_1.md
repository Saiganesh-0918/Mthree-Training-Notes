# PYTHON(WEEK-5, DAY-1)

## NUMPY

Numpy is the library in python where we can work on large amounts of data. It provides fast, optimized functions. It is an open-source library that works on arrays, matrices, and mathematical operations efficiently.

### Flow of execution

1. Imported the numpy packages as np
2. Created two arrays 1D and 2D.
3. Printing the arrays.
4. Created the arrays using random numbers:
   - `np.random.rand(3, 4)`: Creates a 3×4 matrix with random values between 0 and 1.
   - `np.zeros((3, 4))`: Creates a 3×4 matrix filled with zeros.
   - `np.ones((3, 4))`: Creates a 3×4 matrix filled with ones.
   - `np.full((3, 4), 10)`: Creates a 3×4 matrix filled with 10s.
5. `np.arange(10, 20, 0.5)`: Creates an array starting from 10 to 20, with a step of 0.5.
6. Performing matrix additions.
7. Performing matrix subtractions.
8. Performing matrix multiplications.
9. Performing matrix divisions.
10. Performed power matrix.
11. Performed transpose.
12. Dot product operation after transposing the necessary matrices.
13. Mean is the average of all terms. Median is the middle value when numbers are sorted. Performed these two operations on matrices.
14. Standard deviation measures how much the numbers deviate from the mean.
15. Variance is the square of the standard deviation.

## PANDAS

Pandas is also an important and efficient library where it is helpful for operations involving data with series in a single column. It works with dataframes (table with rows and columns).

### Flow of execution

1. Imported the pandas package as pd.
2. Created one-dimensional series without indexes.
3. Created two-dimensional series with indexes.
4. Created a sample dataframe.
5. Created a dataframe from a CSV file and concatenated it.
6. Finding the number of rows in a table.
7. Adding the row into the table.
8. Saving the updated table to a new CSV file (`data_new.csv`).
9. Reading the data from the new CSV file.

## SQLALCHEMY

SQLAlchemy is the bridge between Python and databases. It easily connects to databases like SQLite, MySQL, PostgreSQL, etc.

### Flow of execution

1. Importing necessary packages from SQLAlchemy.
2. Creating a connection to an SQLite database stored at the given path.
3. `echo=True` enables logging, so SQLAlchemy will print the SQL commands it runs.
4. `metadata` acts as a blueprint that keeps track of the tables in the database.
5. Created the `users` table with four columns and one primary key.
6. Created the `posts` table with four columns, one primary key, and one foreign key linked to the `users` table.
7. Created both tables inside the SQLite database.
8. Opened the connection to the database and inserted data into the `users` table.
9. Inserted data into the `posts` table and committed the changes to the database.
10. Fetched all the data from both tables.

### Process

1. **Creating a Database Directory**
   ```sh
   mkdir -p ~/databases
   ```
   This command creates a new folder called `databases` in the home directory.
2. **Moving the Database File**
   ```sh
   mv /home/ganesh/basic-module/data.db ~/databases/
   ```
3. **Checking If the File Exists**
   ```sh
   ls -l ~/databases/data.db
   ```
4. **Navigating to the Project Directory**
   ```sh
   cd basic-module/
   cd numerical/
   ```
5. **Installing Required Packages**
   ```sh
   sudo apt install python3-pip
   pip3 install sqlalchemy
   pip3 install --break-system-packages sqlalchemy
   ```
6. **Running the Python Script**
   ```sh
   python3 temp.py
   ```
7. **Opening the SQLite Database**
   ```sh
   sqlite3 /home/ganesh/databases/data.db
   ```
8. **Checking Available Tables**
   ```sh
   .tables
   ```
9. **Viewing Data in Tables**
   ```sh
   SELECT * FROM users;
   SELECT * FROM posts;
   SELECT * FROM book;
   ```
10. **Exiting the Virtual Environment**
    ```sh
    deactivate
    ```
11. **Checking Python and SQLAlchemy Versions**
    ```sh
    python3 -V
    pip3 list | grep sqlalchemy
    ```
12. **Reinstalling SQLAlchemy**
    ```sh
    pip3 install --break-system-packages sqlalchemy
    ```
13. **Running Python Script Again**
    ```sh
    python3 /home/ganesh/basic-module/numerical/temp.py
    ```
14. **Reopening SQLite and Checking Tables**
    ```sh
    sqlite3 /home/ganesh/databases/data.db
    .tables
    ```

## Python Script

```python
from sqlalchemy import create_engine, text, MetaData, Table, Column, Integer, String, ForeignKey, insert, select

db_path = "/home/ganesh/databases/data.db"
engine = create_engine(f'sqlite:///{db_path}', echo=True)

metadata = MetaData()

users = Table('users', metadata,
    Column('id', Integer, primary_key=True),
    Column('name', String),
    Column('age', Integer),
    Column('city', String),
)

posts = Table('posts', metadata,
    Column('id', Integer, primary_key=True),
    Column('title', String),
    Column('content', String),
    Column('user_id', Integer, ForeignKey('users.id')),
)

metadata.create_all(engine)

with engine.connect() as con:
    insert_stmt = insert(users).values(name='John', age=20, city='New York')
    result = con.execute(insert_stmt)
    print(result.rowcount)

    insert_stmt = insert(posts).values(title='Post 1', content='Content 1', user_id=1)
    result = con.execute(insert_stmt)
    print(result.rowcount)

    con.commit()

    select_stmt = select(users)
    result = con.execute(select_stmt)
    for row in result:
        print(row)

    select_stmt = select(posts)
    result = con.execute(select_stmt)
    for row in result:
        print(row)
```

### Output

Getting the same output in Ubuntu as well as in the terminal from the cursor.

- In the breakout room, we discussed the morning session topics and the final project and went through LMS.

