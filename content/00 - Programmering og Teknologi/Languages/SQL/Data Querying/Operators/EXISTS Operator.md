tags: #Programmering #SQL

## Definition 
---
`EXISTS`-operatoren bruges til at teste for records i en [[Subqueries|subquery]] eksisterer.
Returnerer `TRUE` hvis  [[Subqueries|subqueryen]] returnerer én eller flere records.

## Syntax
---
```SQL
SELECT column_name(s)
FROM table_name 
WHERE EXISTS  
(SELECT column_name FROM table_name WHERE condition);
```
### Example
---
Returnérer `TRUE` og returnerer en liste a `suppliers` med en produktpris mpå mindre end 20:
```SQL
SELECT SupplierName  
FROM Suppliers  
WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price < 20);
```



## Related Topics
---
- [[WHERE Clause|WHERE]]
- [[SELECT]]
- [[AND Operator|AND]]

## Resources
---
- [SQL Exists](https://www.w3schools.com/sql/sql_exists.asp)
- 