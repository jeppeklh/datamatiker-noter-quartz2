tags: #Programmering #SQL #AdvancedTopicsSQL 

## Definition 
---
**Common Table Expressions (CTEs)** provide a way to create a temporary result set that can be referenced within a [[SELECT]], [[INSERT]], [[UPDATE]], or [[DELETE]] statement. 

They improve readability and manageability of complex queries.
## Syntax
---
```sql
WITH cte_name AS
(
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition
)
SELECT column1, column2, ...
FROM cte_name;
```
### Example
---
Using a CTE to find employees with salaries above average:
```sql
WITH AverageSalary AS
(
    SELECT AVG(salary) AS avg_salary
    FROM employees
)
SELECT first_name, last_name, salary
FROM employees, AverageSalary
WHERE employees.salary > AverageSalary.avg_salary;
```

## Related Topics
---
- Link
- 

## Resources
---
- Link
- 