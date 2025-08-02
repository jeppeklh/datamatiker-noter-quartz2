tags: #Programmering #SQL #SQLBasics #Constraint

> [!tldr] Definition
> The `DEFAULT` constraint sets a default value for a column if no value is specified when a row is inserted. 

This ensures that a column always has a value, even if none is provided explicitly..

---

## Syntax
```sql
CREATE TABLE table_name (
    column1 datatype DEFAULT default_value,
    column2 datatype,
    ...
);
```

---

### Example
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    hire_date DATE DEFAULT GETDATE(),
    department VARCHAR(50)
);
```

---

## Related Topics
- [[Constraints]]
- [[NOT NULL]]
- [[UNIQUE]]
- [[PRIMARY KEY]]
- [[FOREIGN KEY]]
- [[CHECK]]

---

## Resources
- Link
- 