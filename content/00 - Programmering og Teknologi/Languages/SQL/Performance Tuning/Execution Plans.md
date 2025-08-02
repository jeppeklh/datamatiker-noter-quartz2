tags: #Programmering #SQL #PerformanceTuning

> [!tldr] Definition
> **Execution Plans** are visual or textual representations of how a database engine executes a query. They help in understanding the performance characteristics of a query and identifying bottlenecks.

---

## Viewing Execution Plans
In SQL Server, you can view the execution plan by running:
```sql
SET SHOWPLAN_TEXT ON;
GO
SELECT * FROM employees;
GO
SET SHOWPLAN_TEXT OFF;
GO
```

In MySQL, you can use the `EXPLAIN` statement:
```sql
EXPLAIN SELECT * FROM employees;
```

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 