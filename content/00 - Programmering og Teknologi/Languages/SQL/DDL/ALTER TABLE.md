tags: #Programmering #SQL #Statement #DDL

> [!tldr] Definition
> The `ALTER TABLE` statement is used to modify an existing [[Table]]. 

You can add, modify, or drop columns, as well as add or drop constraints.

---

## Syntax
```sql
ALTER TABLE table_name
ADD column_name datatype;

ALTER TABLE table_name
DROP COLUMN column_name;

ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

---

### Example
```sql
ALTER TABLE employees
ADD date_of_birth DATE;

ALTER TABLE employees
DROP COLUMN date_of_birth;

ALTER TABLE employees
MODIFY COLUMN last_name VARCHAR(100);
```

---

## Related Topics
- [[DDL Overview]]
- [[CREATE TABLE]]
- [[DROP TABLE]]
- [[CREATE INDEX]]
- [[SQL Syntax|SQL Syntax]]

---

## Resources
- Link
- 