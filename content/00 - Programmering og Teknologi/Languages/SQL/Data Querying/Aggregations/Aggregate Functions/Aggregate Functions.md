tags: #Programmering #SQL #DataQuerying

> [!tldr] Definition
> **Aggregate Functions** laver udregninger på et set af værdier og returnerer en enkelt værdi.


Ofte brugte funktioner:  
- [[COUNT()]]
- [[SUM()]]
- [[AVG()]]
- [[MIN() and MAX()]]

---

## Example
Returnér den gennemsnitlige løn af `employees`.
```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```

---

## Related Topics
- [[Data Querying Overview]]
- 

---

## Resources
- [Aggregate functions](https://www.w3schools.com/sql/sql_aggregate_functions.asp)
- 