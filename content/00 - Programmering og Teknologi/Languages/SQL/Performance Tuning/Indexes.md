tags: #Programmering #SQL #PerformanceTuning

> [!tldr] Definition
> Indexes are database objects that improve the speed of data retrieval operations on a [[Table|table]] at the cost of additional storage and slower write operations. 

They can significantly enhance query performance by allowing the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] engine to locate data quickly.

---

## Types of Indexes

### Primary Index
A Primary Index is an index that is automatically created when a [[PRIMARY KEY|primary key]] is defined on a [[Table|table]].
It ensures that the column (or columns) designated as the  [[PRIMARY KEY|primary key]] is unique and not null. There can only be one primary index per [[Table|table]].

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    last_name VARCHAR(50),
    first_name VARCHAR(50)
);
```

---

### Unique Index
A Unique Index ensures that all values in the indexed column or columns are unique. 
Unlike a [[#Primary Index|primary index]], a [[Table|table]] can have multiple unique indexes. 
This type of index helps enforce the uniqueness of the values without necessarily being a  [[PRIMARY KEY|primary key]].

```sql
CREATE UNIQUE INDEX idx_employee_email ON employees (email);
```

---

### Composite Index
A Composite Index is an index on two or more columns of a [[Table|table]]. 
It is used to optimize queries that use multiple columns in the WHERE clause. 
The order of the columns in the composite index is crucial because the database engine uses this order to optimize query performance.

```sql
CREATE INDEX idx_employee_name ON employees (last_name, first_name);
```

---

### Full-text Index
A Full-text Index is a special type of index used for full-text searches. 
This type of index allows for more complex queries against character-based data. 
Full-text searches look for words or phrases within text columns, making them useful for applications like search engines.

```sql
CREATE FULLTEXT INDEX idx_employee_bio ON employees (bio);
```

---

## Benefits of Indexes
- **Speed up data retrieval**: Indexes can significantly improve the performance of SELECT queries.
- **Enforce uniqueness**: Unique and primary indexes ensure that duplicate values are not entered in the indexed columns.
- **Full-text searching**: Full-text indexes allow for efficient searching of text data.

---

## Drawbacks of Indexes
- **Increased storage space**: Indexes require additional storage.
- **Slower write operations**: INSERT, UPDATE, and DELETE operations can be slower on indexed columns because the indexes need to be updated.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 