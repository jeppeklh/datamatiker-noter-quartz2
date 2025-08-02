tags: #Programmering #SQL #DataQuerying

> [!tldr] Definition
> **Unions** are used to combine the results of two or more [[SELECT]] queries into a single result set. Each [[SELECT]] statement within the `UNION` must have the same number of columns in the result sets with similar [[SQL Data Types|data types]].

---

## Syntax
```sql
SELECT column1, column2, ...
FROM table1
UNION
SELECT column1, column2, ...
FROM table2;
```

---

### Example
Retrieve all unique department names from two different [[Table|tables]]:
```sql
SELECT department_name FROM departments1
UNION
SELECT department_name FROM departments2;
```

---

## Related Topics
- [[Data Querying Overview]]
- 

---

## Resources
- Link
- 