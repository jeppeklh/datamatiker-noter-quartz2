tags: #Programmering #SQL #DataQuerying

## Definition 
---
`Having`-klausulen blev tilføjet fordi [[WHERE Clause|WHERE]]-klausulen ikke kan bruges sammen med [[Aggregate Functions]].

## Syntax
---
```SQL
SELECT column_name(s) 
FROM table_name
WHERE condition  
GROUP BY column_name(s)  
HAVING condition  
ORDER BY column_name(s);
```
### Example
---
Liste antallet a `customers` i hvert land. Inkludér kun lande hvor der er 5 eller flere `customers`:
```sql
SELECT COUNT(CustomerID), Country  
FROM Customers  
GROUP BY Country  
HAVING COUNT(CustomerID) > 5;
```

## Related Topics
---
- [[Data Querying Overview]]
- [[GROUP BY]]
- [[WHERE Clause|WHERE]]
- [[ORDER BY Clause|ORDER BY]]
- [[SELECT]]

## Resources
---
- [SQL Having Clause](https://www.w3schools.com/sql/sql_having.asp)
- 