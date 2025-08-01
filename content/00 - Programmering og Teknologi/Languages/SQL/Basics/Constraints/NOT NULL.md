tags: #Programmering #SQL #SQLBasics #Constraint

## Definition 
---
The `NOT NULL` constraint ensures that a column cannot have a `NULL` value. 

This constraint enforces that you must provide a value for the column whenever a new row is inserted or an existing row is updated.
## Syntax
---
```sql
CREATE TABLE table_name (
    column1 datatype NOT NULL,
    column2 datatype,
    ...
);
```
### Example
---
```sql
CREATE TABLE employees (
    employee_id INT NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50),
    department VARCHAR(50)
);
```


## Related Topics
---
- [[Constraints]]
- [[UNIQUE]]
- [[PRIMARY KEY]]
- [[FOREIGN KEY]]
- [[CHECK]]
- [[DEFAULT]]

## Resources
---
- Link
- 