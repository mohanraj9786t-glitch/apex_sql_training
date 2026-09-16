# SQL Command Categories: DDL, DML, DCL, TCL

SQL commands are grouped into four main categories based on what they do.

---

## 1. DDL – Data Definition Language

Defines and modifies the **structure** of database objects (tables, schemas, indexes, etc.). DDL statements are auto-committed — changes are saved immediately and cannot be rolled back in most databases.

| Command | Purpose |
|---|---|
| `CREATE` | Create a new database object (table, view, index, database, etc.) |
| `ALTER` | Modify the structure of an existing object |
| `DROP` | Delete an object permanently |
| `TRUNCATE` | Remove all rows from a table quickly (structure stays intact) |
| `RENAME` | Rename an existing database object |
| `COMMENT` | Add comments to the data dictionary |

**Example:**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2)
);

ALTER TABLE employees ADD COLUMN department VARCHAR(50);

DROP TABLE employees;

TRUNCATE TABLE employees;
```

---

## 2. DML – Data Manipulation Language

Used to **manipulate data** stored within existing database objects.

| Command | Purpose |
|---|---|
| `SELECT` | Retrieve data from one or more tables |
| `INSERT` | Add new rows of data |
| `UPDATE` | Modify existing data |
| `DELETE` | Remove existing rows |
| `MERGE` | Insert/update/delete in one statement (upsert) |

**Example:**
```sql
INSERT INTO employees (id, name, salary) VALUES (1, 'Anita', 55000);

UPDATE employees SET salary = 60000 WHERE id = 1;

DELETE FROM employees WHERE id = 1;

SELECT * FROM employees WHERE salary > 50000;
```

---

## 3. DCL – Data Control Language

Controls **access and permissions** to database objects.

| Command | Purpose |
|---|---|
| `GRANT` | Give a user access privileges |
| `REVOKE` | Remove previously granted privileges |

**Example:**
```sql
GRANT SELECT, INSERT ON employees TO user_name;

REVOKE INSERT ON employees FROM user_name;
```

---

## 4. TCL – Transaction Control Language

Manages **transactions** to maintain data integrity — grouping DML statements so they succeed or fail together.

| Command | Purpose |
|---|---|
| `COMMIT` | Save all changes made in the current transaction |
| `ROLLBACK` | Undo changes made in the current transaction |
| `SAVEPOINT` | Set a point within a transaction to roll back to |
| `SET TRANSACTION` | Configure properties of a transaction |

**Example:**
```sql
BEGIN;

UPDATE employees SET salary = salary + 5000 WHERE department = 'Sales';
SAVEPOINT before_bonus;

UPDATE employees SET salary = salary + 1000 WHERE department = 'Sales';

ROLLBACK TO before_bonus;

COMMIT;
```

---

## Quick Summary

| Category | Full Form | Deals With | Common Commands |
|---|---|---|---|
| **DDL** | Data Definition Language | Structure | CREATE, ALTER, DROP, TRUNCATE |
| **DML** | Data Manipulation Language | Data | SELECT, INSERT, UPDATE, DELETE |
| **DCL** | Data Control Language | Permissions | GRANT, REVOKE |
| **TCL** | Transaction Control Language | Transactions | COMMIT, ROLLBACK, SAVEPOINT |
