tags: #Programmering #SQL #SQLBasics #Constraint

## Definition 
---
The `CHECK` constraint ensures that all values in a column satisfy a specific condition. 

This can be used to enforce domain integrity by limiting the values that can be stored in a column.
## Syntax
---
```sql
CREATE TABLE table_name (
    column1 datatype CHECK (condition),
    column2 datatype,
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
    age INT CHECK (age >= 18),
    department VARCHAR(50)
);
```


## Related Topics
---
- [[Constraints]]
- [[NOT NULL]]
- [[UNIQUE]]
- [[PRIMARY KEY]]
- [[FOREIGN KEY]]
- [[NOT NULL]]

## Resources
---
- Link
- 