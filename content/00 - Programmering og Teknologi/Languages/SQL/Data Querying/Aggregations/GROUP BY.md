tags: #Programmering #SQL #DataQuerying

> [!tldr] Definition
> **GROUP BY** bruges sammen med [[Aggregate Functions]] for at gruppere resultat-set efter 1 eller flere kolonner.

---

## Syntax
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

---

### Example
List antallet af `customers` i hvert land.
```SQL
SELECT COUNT(CustomerID), Country  
FROM Customers  
GROUP BY Country  
```

---

## Related Topics
- [[Data Querying Overview]]
- [[SELECT]]

---

## Resources
- [SQL Group By](https://www.w3schools.com/sql/sql_groupby.asp)
- 