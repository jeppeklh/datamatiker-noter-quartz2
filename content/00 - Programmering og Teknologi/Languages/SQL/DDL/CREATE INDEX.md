tags: #Programmering #SQL #DDL #Statement 

> [!tldr] Definition
> The `CREATE INDEX` statement is used to create an index on a [[Table|table]]. 

Indexes are used to speed up the retrieval of data from the table by providing quick access to rows based on the values of one or more columns.

---

## Syntax
```csharp
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

---

### Example
```csharp
CREATE INDEX idx_employee_lastname
ON Employees (LastName);
```

In this example, an index named `idx_employee_lastname` is created on the `LastName` column of the `Employees` table to speed up searches on that column.

---

## Related Topics
- [[DDL Overview]]
- [[ALTER TABLE]]
- [[CREATE TABLE]]
- [[DROP TABLE]]
- [[SQL Syntax|SQL Syntax]]

---

## Resources
- Link
- 