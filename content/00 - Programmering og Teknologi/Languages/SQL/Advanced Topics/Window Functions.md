tags: #Programmering #SQL #AdvancedTopicsSQL 

> [!tldr] Definition
> **Window Functions** perform calculations across a set of [[Table|table]] rows related to the current row. 
> They are useful for ranking, cumulative sums, moving averages, and more.

---

## Syntax
```sql
SELECT column1, column2,
       window_function() OVER (PARTITION BY column3 ORDER BY column4)
FROM table_name;
```

---

### Example
Using a window function to rank employees by salary within departments:
```sql
SELECT department_id, first_name, last_name, salary,
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank
FROM employees;
```

The `RANK()` function assigns a rank to each row within a partition of the result set. 
The rank of a row is one plus the number of ranks that come before it. 
If there are ties, it leaves gaps between the ranks.

---

## Other Window Functions
- `ROW_NUMBER()`: Assigns a unique number to each row within a partition of the result set, starting at 1.
- `DENSE_RANK()`: Similar to `RANK()`, but without gaps between ranks when there are ties.
- `NTILE(n)`: Divides the result set into `n` approximately equal parts and assigns a unique bucket number to each row.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 