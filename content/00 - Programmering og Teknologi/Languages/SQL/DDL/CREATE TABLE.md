tags: #Programmering #SQL #DDL #Statement 

## Definition 
---
The `CREATE TABLE` statement is used to create a new table in a [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. 

You can specify the columns and their data types, as well as any constraints on the columns.
## Syntax
---
```sql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    ...
);
```
### Example
---
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    department VARCHAR(50)
);
```

## Related Topics
---
- [[DDL Overview]]
- [[ALTER TABLE]]
- [[DROP TABLE]]
- [[CREATE INDEX]]
- [[SQL Syntax|SQL Syntax]]

## Resources
---
- 
- [Creating tables LinkedIn Video](https://www.linkedin.com/learning/programming-foundations-databases-2/creating-tables?u=57075649)