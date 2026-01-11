# SQL BASICS – DAY 1 NOTES

## 1. Create Database

A database is used to store tables and data.

```sql
CREATE DATABASE student;
```

---

## 2. Use Database

Before creating tables or inserting data, we must select the database.

```sql
USE student;
```

---

## 3. Create Table

A table stores data in rows and columns.

```sql
CREATE TABLE user (
  id INT,
  age INT,
  name VARCHAR(40) NOT NULL,
  email VARCHAR(40) UNIQUE NOT NULL,
  followers INT DEFAULT 0,
  following INT,
  CONSTRAINT age_check CHECK (age >= 13)
);
```

### Explanation of Columns

* `id` → user identification number
* `age` → user age (must be 13 or above)
* `name` → user name (cannot be NULL)
* `email` → user email (must be unique)
* `followers` → number of followers (default 0)
* `following` → number of accounts followed

---

## 4. See Tables in Database

Shows all tables present in the selected database.

```sql
SHOW TABLES;
```

---

## 5. See Table Structure

Shows column names, data types, constraints, and default values.

```sql
DESC user;
```

---

## 6. See Table Creation Query

Shows the exact SQL used to create the table.

```sql
SHOW CREATE TABLE user;
```

---

## 7. Insert Data (Example)

Insert one record into the table.

```sql
INSERT INTO user (id, age, name, email)
VALUES (1, 18, 'Akshay', 'akshay@gmail.com');
```

---

## 8. View Data in Table

Displays all rows and columns from the table.

```sql
SELECT * FROM user;
```

---

## 9. Raw Data Table (Example Output)

| id | age | name   | email                                       | followers | following |
| -- | --- | ------ | ------------------------------------------- | --------- | --------- |
| 1  | 18  | Akshay | [akshay@gmail.com](mailto:akshay@gmail.com) | 0         | NULL      |

---

## Summary

* Created a database
* Created a table with constraints
* Viewed table structure
* Inserted data
* Displayed records

✅ End of Day 1 SQL Notes
