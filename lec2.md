# Primary Key & Foreign Key Constraints (MySQL)

These notes explain **PRIMARY KEY** and **FOREIGN KEY** constraints using your *Instagram-like* database example.

---

## 1️⃣ What is a Database?

A **database** is a structured collection of data stored electronically.

```sql
CREATE DATABASE IF NOT EXISTS instgram;
USE instgram;
```

* `IF NOT EXISTS` prevents errors if the database already exists.
* `USE instgram` tells MySQL to work inside this database.

---

## 2️⃣ What is a Table?

A **table** stores data in rows and columns.

* **Row** → One record
* **Column** → One attribute

---

## 3️⃣ PRIMARY KEY (PK)

### ✅ Definition

A **PRIMARY KEY** uniquely identifies each row in a table.

### 🔑 Rules of Primary Key

* Must be **unique**
* Cannot be **NULL**
* Only **one primary key per table**
* Helps MySQL identify records fast

---

### 📌 Example: `user` Table

```sql
CREATE TABLE user (
  id INT,
  age INT,
  name VARCHAR(40) NOT NULL,
  email VARCHAR(40) UNIQUE NOT NULL,
  followers INT DEFAULT 0,
  following INT,
  CONSTRAINT age_check CHECK (age >= 13),
  PRIMARY KEY (id)
);
```

### 🧠 Explanation

* `id` is the **PRIMARY KEY**
* Each user must have a **unique id**
* Two users **cannot share the same id**

📌 Example (Valid):

| id | name | email                             |
| -- | ---- | --------------------------------- |
| 1  | Ravi | [r@gmail.com](mailto:r@gmail.com) |
| 2  | Anu  | [a@gmail.com](mailto:a@gmail.com) |

❌ Invalid (Duplicate PK):

| id | name |
| -- | ---- |
| 1  | Ravi |
| 1  | Anu  |

---

## 4️⃣ FOREIGN KEY (FK)

### ✅ Definition

A **FOREIGN KEY** creates a link between two tables.
It ensures **data consistency**.

> Foreign Key = Reference to Primary Key of another table

---

### 📌 Example: `posts` Table

```sql
CREATE TABLE posts (
    id INT PRIMARY KEY,
    content VARCHAR(100),
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES user(id)
);
```

### 🧠 Explanation

* `user_id` is a **FOREIGN KEY**
* It refers to `id` in the `user` table
* Each post **must belong to an existing user**

---

## 5️⃣ Relationship Between Tables

### 🔗 One-to-Many Relationship

* **One user** → can create **many posts**
* **One post** → belongs to **one user**

```
user (1) -------- (many) posts
```

---

## 6️⃣ How FK Enforces Rules

### ✅ Allowed

```sql
INSERT INTO posts VALUES (1, 'Hello World', 1);
```

✔ Works **only if user with id = 1 exists**

### ❌ Not Allowed

```sql
INSERT INTO posts VALUES (2, 'Invalid Post', 99);
```

❌ Error because **user id 99 does not exist**

---

## 7️⃣ Why Primary & Foreign Keys Are Important

### 🔒 Data Integrity

* Prevents invalid data

### 🔗 Table Relationships

* Connects tables logically

### ⚡ Performance

* Faster searching and indexing

### 🧠 Real-World Mapping

| Real Life      | Database    |
| -------------- | ----------- |
| Aadhaar Number | Primary Key |
| Post Owner     | Foreign Key |

---

## 8️⃣ Commands You Used

### Show tables

```sql
SHOW TABLES;
```

### Describe table structure

```sql
DESC user;
```

### View data

```sql
SELECT * FROM user;
```

---

## 9️⃣ Summary Table

| Constraint  | Purpose                   |
| ----------- | ------------------------- |
| PRIMARY KEY | Uniquely identifies a row |
| FOREIGN KEY | Links two tables          |
| UNIQUE      | Prevents duplicates       |
| CHECK       | Enforces condition        |
| NOT NULL    | Prevents empty values     |

---

## 🔚 Final Takeaway

* **Primary Key** = Identity of a record
* **Foreign Key** = Relationship between tables
* Both are **mandatory concepts** in DBMS & interviews

---

📌 *These notes are VTU + interview oriented. Save this README.md for revision.*
