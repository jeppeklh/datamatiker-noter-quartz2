tags: #Programmering #SQL #SQLBasics #Constraint

> [!tldr] Definition
> The `UNIQUE` constraint ensures that all values in a column are unique. 
> No two rows can have the same value in the specified column(s).
> A [[Table]] can have multiple `UNIQUE` constraints.

---

## Syntax
```sql
CREATE TABLE table_name (
    column1 datatype UNIQUE,
    column2 datatype,
    ...
);
```

---

### Example
```sql
CREATE TABLE employees (
    employee_id INT UNIQUE,
    email VARCHAR(100) UNIQUE,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
```

---

## Related Topics
- [[Constraints]]
- [[NOT NULL]]
- [[PRIMARY KEY]]
- [[FOREIGN KEY]]
- [[CHECK]]
- [[DEFAULT]]

---

## Resources
- Link
- 