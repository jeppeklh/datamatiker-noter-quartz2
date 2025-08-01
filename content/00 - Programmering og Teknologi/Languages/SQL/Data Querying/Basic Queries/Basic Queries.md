tags: #Programmering #SQL

## Definition 
---
**Basic Queries** in SQL involve using the [[SELECT]] statement to retrieve data from one or more [[Table|tables]]. 

The [[SELECT]] statement is fundamental to SQL and allows you to specify the columns you want to retrieve, filter rows using the `WHERE` clause, sort results using `ORDER BY`, and more.
## Syntax
---
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
### Example
---
Retrieve all columns from the "employees" [[Table|table]]:
```sql
SELECT * FROM employees;
```

Retrieve specific columns from the "employees" [[Table|table]] where the department is 'Sales':
```sql
SELECT first_name, last_name, department
FROM employees
WHERE department = 'Sales';
```

## Related Topics
---
- [[Data Querying Overview]]
- 

## Resources
---
- Link
- 