# SQL Cheat Sheet: Accessing Databases using Python

## SQLite

### `connect()`
```python
import sqlite3
con = sqlite3.connect("INSTRUCTOR.db")
```
**Description:**
Creates and opens a database connection to work with SQLite. If the database does not exist, it is created.

---

### `cursor()`
```python
cursor_obj = con.cursor()
```
**Description:**
Creates a database cursor to execute SQL statements and fetch results.

---

### `execute()`
```python
cursor_obj.execute("INSERT INTO INSTRUCTOR VALUES (1, 'Rav', 'Ahuja', 'Math')")
```
**Description:**
Executes an SQL command, such as inserting or retrieving data.

---

### `fetchall()`
```python
statement = "SELECT * FROM INSTRUCTOR"
cursor_obj.execute(statement)
output_all = cursor_obj.fetchall()
for row in output_all:
    print(row)
```
**Description:**
Retrieves all rows from the query result and presents them as a list of tuples.

---

### `fetchmany()`
```python
statement = "SELECT * FROM INSTRUCTOR"
cursor_obj.execute(statement)
output_many = cursor_obj.fetchmany(2)
for row in output_many:
    print(row)
```
**Description:**
Retrieves a specified number of rows from the result set.

---

### `read_sql_query()`
```python
import pandas as pd
df = pd.read_sql_query("SELECT * FROM INSTRUCTOR", con)
```
**Description:**
Executes an SQL query and returns the result as a Pandas DataFrame.

---

### `shape`
```python
df.shape
```
**Description:**
Returns the shape of the DataFrame as (rows, columns).

---

### `close()`
```python
con.close()
```
**Description:**
Closes the connection to the SQLite database.

---

### `CREATE TABLE`
```sql
CREATE TABLE INTERNATIONAL_STUDENT_TEST_SCORES (
    country VARCHAR(50),
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    test_score INT
);
```
**Description:**
Defines and creates a new table within the database.

---

### `barplot()`
```python
import seaborn as sns
sns.barplot(x='Test_Score', y='Frequency', data=df)
```
**Description:**
Creates a bar plot using the Seaborn library.

---

### `read_csv()`
```python
import pandas as pd
df = pd.read_csv("data.csv")
```
**Description:**
Reads a CSV file and loads it into a Pandas DataFrame.

---

### `to_sql()`
```python
df.to_sql("table_name", con, if_exists='replace', index=False)
```
**Description:**
Writes the contents of a DataFrame to a SQL database.

---

### `read_sql()`
```python
selectQuery = "SELECT * FROM INSTRUCTOR"
df = pd.read_sql(selectQuery, con)
```
**Description:**
Executes an SQL query and returns the result as a DataFrame.

---

## Db2

### `connect()`
```python
import ibm_db
conn = ibm_db.connect("DATABASE=mydb;HOST=example.com;PORT=50000;UID=myuser;PWD=mypassword;", '', '')
```
**Description:**
Establishes a connection to an IBM Db2 database.

---

### `server_info()`
```python
server = ibm_db.server_info(conn)
print("DBMS_NAME: ", server.DBMS_NAME)
print("DBMS_VER:  ", server.DBMS_VER)
print("DB_NAME:   ", server.DB_NAME)
```
**Description:**
Retrieves information about the IBM Db2 server.

---

### `close()`
```python
conn.close()
```
**Description:**
Closes the connection to the Db2 database.

---

### `exec_immediate()`
```python
dropQuery = "DROP TABLE INSTRUCTOR"
dropStmt = ibm_db.exec_immediate(conn, dropQuery)
```
**Description:**
Executes an SQL statement immediately without preparing or binding it.

---

## Author(s)
- Abhishek Gagneja
- D.M Naidu
