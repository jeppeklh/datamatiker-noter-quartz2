tags: #Programmering #SQL #DataQuerying 

## Definition 
---
**Subqueries** are queries nested inside another query. 

They can be used in various places such as the [[SELECT]], `FROM`, `WHERE`, and `HAVING` clauses to filter, aggregate, and transform data.
## Syntax
---
```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name = (SELECT column_name FROM another_table WHERE condition);
```
### Example
---
Retrieve employees whose salaries are above the average salary:
```sql
SELECT first_name, last_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

## Related Topics
---
- [[Data Querying Overview]]
- 

## Resources
---
- Link
- 